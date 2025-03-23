# Object Calisthenics

foi introduzido por **Jeff Bay** e publicado no seu livro chamado **Thought Works Anthology**. <br>
<br>
A principal motivação para o Object Calisthenics é aplicar alguns princípios do SOLID. <br>
Basicamente são um conjunto de boas práticas e regras de programação para aumentar a qualidade do seu código.

Essas regras são focadas em manutenibilidade, legibilidade, testabilidade e compreensão de seu código.

Se você já escreve um código com boa manutenção, legível, testável e compreensível, essas regras o ajudarão <br>
a escrever um código ainda mais sustentável, mais legível, mais testável e mais compreensível <br>
<br>
**São 9 regras básicas**
<br>
1. **Only One Level Of Indentation Per Method** - (Apenas um nível de recuo por método)
2. **Don’t Use The ELSE Keyword** - (Não use a palavra-chave ELSE)
3. **Wrap All Primitives And Strings** - (Envolva todos os primitivos e strings)
4. **First Class Collections** - (Coleções de primeira classe)
5. **One Dot Per Line** - (Um ponto por linha)
6. **Don’t Abbreviate** - (Não abrevie)
7. **Keep All Entities Small** - (Mantenha todas as entidades pequenas)
8. **No Classes With More Than Two Instance Variables** - (Nenhuma classe com mais de duas variáveis ​​de instância)
9. **No Getters/Setters/Properties** - (Nenhum getter/setter/propriedades)
<br>

### 1. Only One Level Of Indentation Per Method

Primeira regra, tente manter seu método mais simples e compreensível possível.

```
public String LerDados(string[][] data)
{
    StringBuilder buf = new StringBuilder();
    // Primeiro nivel 
    for (int i = 0; i < 10; i++)
    {
         // Segundo nivel
         for (int j = 0; j < 10; j++)
         {
              // Primeiro nivel
              buf.Append(data[i][j]);
         }
         buf.Append("\n");
     }
     return buf.ToString();
}

```

Para aplica a primeira regra no código acima, podemos utilizar o **Extract** <br> 
Method Pattern, introduzido por Martin Fowler em seu livro Refactoring.

Veja agora como ficou nosso código aplicando o Extract Method Pattern:

```
public String LerDados(string[][] data)
{
     StringBuilder buf = new StringBuilder();
           
     LerLinhas(data, buf);
     return buf.ToString();
}
private void LerLinhas(string[][] data, StringBuilder buf)
{
     for (int i = 0; i < 10; i++)
     {
        LerColunas(data, buf, i);
     }
}
private static void LerColunas(string[][] data, StringBuilder buf, int i)
{
     for (int j = 0; j < 10; j++)
     {
        buf.Append(data[i][j]);
     }
     buf.Append("\n");
}

```

### 2. Don’t use “Else” keyword

A ideia deste conceito é evitar o máximo possível o uso do “else” e assumindo que temos um fluxo padrão de execução.<br>

Veja esse código:

```

public IActionResult Login(String username, String password)
{
   var view = String.Empty;
 
   if (!userRepository.isValid(username, password))
   {
        ModelState.AddModelError("error", "Bad credentials");
        view = "Login";
   }
   else
   {
        view = "Home";
   }
   return View(view);
}

```

Agora veja o código utilizando o **Early Return**:

```

public IActionResult Login(String username, String password)
{
     if (!userRepository.isValid(username, password))
     {
         ModelState.AddModelError("error", "Bad credentials");
         return View("Login");
     }
     return View("Home");
}

```

### 3. Wrap All Primitives And Strings

Essa regra é bem simples bastando você encapsular todos os tipos primitivos como objetos.

Se um tipo primitivo tem um comportamento por exemplo CPF então esta variável deveria estar encapsulada em um Objeto CPF.

E isso é especialmente verdade quando falamos em **DDD (Domain Drive Design)** em especial na parte de **Value Objects**.

Vamos ao exemplo:

```

public class Pessoa
{
    public string CPF { get; set; }
}

```

Veja que a variável CPF não esta encapsulada porém temos regras em cima dela. Por exemplo regra de formação de CPF, validação de CPF e etc.

Agora aplicando a regra:

```

public class Pessoa
{
    public CPF CPF { get; set; }
}
public class CPF
{
    public string Numero { get; set; }
    public string NumeroFormatado => FormataNumero();
    public CPF (string numero)
    {
        if (!EstaValido(numero))
            throw new CPFInvalidoException(numero);
        this.Numero = numero;
    }
    private void EstaValido(numero)
    {
        //Codigo..
    }
    private String FormataNumero()
    {
        //Codigo
    }
}

```

### 4. First Class Collections

Qualquer classe que contenha uma coleção não deve conter outras variáveis ​​de membro. <br>
Se você tiver um conjunto de elementos e quiser manipulá-los, crie uma classe dedicada para essa coleção. <br>
Assim comportamentos relacionados à coleção serão implementados por sua própria classe exemplo, métodos de filtro, uma regra a cada elemento e etc.

```
public class ProductCollection : IList<Product>
{
    //Codigo
}

```

### 5. One Dot Per Line

Essa regra cita que você não deve encadear métodos e sim usar objetos que fazem parte do mesmo contexto.

Essa regra não se a aplica objetos que aplicam o Method Chaining Pattern criado por Martin Fowler.

```
public class Endereco 
{
    public Cidade Cidade { get; set; }
}
public class Cidade
{
    public Estado Estado { get; set; }
} 
public class Estado
{
    public string Nome { get; set; }
}
static void Main(string[] args)
{
    var endereco = new Endereco();
    Console.WriteLine(endereco.Cidade.Estado.Nome);
}

```

### 6. Don’t Abbreviate

Porque queremos abreviar o nome de uma variável ou um método ? Lembre-se que o ter um nome com um bom significado <br>
ajuda muito no entendimento do código.

A recomendação desta regra é não usar nomes abreviados e com significado.

Essa prática foi mencionada no livro Clean Code: A Handbook of Agile Software Craftsmanship de Robert C. Martin — “Meaningful Names”

### 7. Keep All Entities Small

Essa regra fala para não termos classes com mais de 50 linhas.

Sabemos que isso é bem complicado mas depende de nós, eu trocaria de 50 linhas por 200 linhas.

O conceito principal desta regra é não termos classes com muitas linhas de código, justamente porque são mais difíceis de entender e de manter.


### 8. No Classes With More Than Two Instance Variables
Essa regra diz que não devemos ter duas instancia de variável por classe.

A ideia principal desta regra é garantir a alta coesão entre as classes e o principio da responsabilidade única.

De modo geral, devemos nos questionar se a classe está fazendo o que ela foi projetada para fazer e se tem mais responsabilidades do que ela deveria ter.

### 9. No Getters/Setters
Essa regra gera sempre discussão porque não podemos usar Getter/Setter, soa estranho ainda mais quando estamos programando em C# e criando classes POCO.

O uso de Getter/Setter são frequentes em classes deste tipo. Mas veja o exemplo abaixo:

```
public class Jogo
{
    public int Score { get; set; }
}
//Uso 
jogo.Score = jogo.Score + PONTOS_INIMIGOS_DESTRUIDO;

```

Não acha que o código acima está violando o principio **Open/Closed do SOLID** ?

O código acima usa a propriedade Score para tomar uma decisão de como incrementar os pontos de um determinado jogador e esquecendo que a responsabilidade de adicionar pontos do jogador é da classe Jogo.

Veja agora o mesmo código aplicando a regra.

```

public class Jogo
{
    public int Score { get; private set; }
    public void AdicionarScore(int pontos)
    {
        this.Score += pontos;
    }
}
//Uso 
jogo.AdicionarPontos(PONTOS_INIMIGOS_DESTRUIDO);

```

No código acima a responsabilidade de adicionar pontos a um determinado jogador é da classe **Jogo**.

É a classe **Jogo** que sabe o comportamento de como aumentar a pontuação do jogador.

**Conclusão**
Eu sei que algumas regras podem ser extremas e de difícil execução porém <br>
aplicando alguns do seus conceitos pode aumentar drasticamente a <br>
qualidade do seu código. De todas as 9 regras as principais no meu modo de <br>
vista são a 1, 2, 3 e a 6.

Tentei explicar neste artigo alguns conceitos básicos do **Object Calisthenics**, <br>
espero que de alguma forma eu consiga inspirar vocês a escreverem um código melhor.



