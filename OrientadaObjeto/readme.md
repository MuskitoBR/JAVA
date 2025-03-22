# O que é um objeto?

Um objeto é um pacote de software de estado e comportamento relacionados. <br>
Esta seção explica como o estado e o comportamento são representados dentro de um objeto,<br>
introduz o conceito de encapsulamento de dados e explica os benefícios de projetar seu software dessa maneira.<br>
<br>
Objetos compartilham duas características: todos eles têm estado e comportamento. <br>
Cachorros têm estado (nome, cor, raça, fome) e comportamento (latindo, buscando, abanando o rabo). <br>
Bicicletas também têm estado (marcha atual, cadência atual do pedal, velocidade atual) e comportamento <br>
(trocando marcha, trocando cadência do pedal, aplicando freios). <br>
Identificar o estado e o comportamento de objetos do mundo real é uma ótima maneira de começar a pensar em termos de programação orientada a objetos.

Reserve um minuto agora mesmo para observar os objetos do mundo real que estão em sua área imediata. Para cada objeto que você vê, faça a si mesmo duas perguntas: "Em quais estados possíveis esse objeto pode estar?" e "Qual comportamento possível esse objeto pode executar?". Certifique-se de anotar suas observações. Ao fazer isso, você notará que os objetos do mundo real variam em complexidade; sua luminária de mesa pode ter apenas dois estados possíveis (ligado e desligado) e dois comportamentos possíveis (ligar, desligar), mas seu rádio de mesa pode ter estados adicionais (ligado, desligado, volume atual, estação atual) e comportamento (ligar, desligar, aumentar volume, diminuir volume, procurar, escanear e sintonizar). Você também pode notar que alguns objetos, por sua vez, também conterão outros objetos. Essas observações do mundo real são um ponto de partida para entender o mundo da programação orientada a objetos.

# POO
<br>

A Programação Orientada a Objetos (POO) é um paradigma de programação que organiza o código em <br>
torno de **objetos**, que representam entidades do mundo real. No Java, POO é um dos pilares da linguagem.
<br>

 ## Principais Conceitos da POO em Java <br>
<br>

 1. **Classe** - Modelo ou estrutura para criar objetos.<br>
 2. **Objeto** - Instância de uma classe.<br>
 3. **Encapsulamento** - Proteção dos atributos e métodos de uma classe.<br>
 4. **Herança** - Reutilização de código através de classes derivadas.<br>
 5. **Polimorfismo** - Capacidade de um método ter diferentes comportamentos.<br>
 6. **Abstração** - Ocultação de detalhes desnecessários.<br>
<br>
<br>
 
## Exemplo Prático<br>
Aqui está um exemplo simples de uma classe em Java que segue os princípios da POO:<br>

```
      // Definição da classe

      class Carro {
          // Atributos
          private String modelo;
          private int ano;
      
          // Construtor
          public Carro(String modelo, int ano) {
              this.modelo = modelo;
              this.ano = ano;
          }
      
          // Método para exibir informações
          public void mostrarDetalhes() {
              System.out.println("Modelo: " + modelo + ", Ano: " + ano);
          }
      }
      
      // Classe principal
      public class Main {
          public static void main(String[] args) {
              // Criando um objeto da classe Carro
              Carro meuCarro = new Carro("Toyota Corolla", 2022);
              meuCarro.mostrarDetalhes(); // Saída: Modelo: Toyota Corolla, Ano: 2022
          }
      }

```

<br>
<br>

# Explicação do Código

 1. Criamos a classe Carro com atributos privados (modelo e ano).<br>
 2. Utilizamos um construtor para inicializar esses atributos.<br>
 3. Criamos um método para exibir os detalhes do carro.<br>
 4. No método main, instanciamos um objeto Carro e chamamos o método mostrarDetalhes().<br>
 <br>


# Classes

### O que é uma classe?

Em seus aplicativos, você frequentemente encontrará muitos objetos individuais, todos do mesmo tipo. Pode haver milhares de outras bicicletas existentes, todas da mesma marca e modelo. Cada bicicleta foi construída a partir do mesmo conjunto de projetos e, portanto, contém os mesmos componentes. Em termos orientados a objetos, dizemos que sua bicicleta é uma instância da classe de objetos conhecida como bicicletas. Uma classe é o projeto a partir do qual os objetos individuais são criados.
 Uma classe em Java é um modelo (ou molde) para criar objetos. Ela define 
 atributos (características) e métodos (comportamentos) que os objetos criados a partir dela terão.<br>

  ## Estrutura de uma Classe
  * Uma classe em Java segue essa estrutura básica:
```
// definição da class
public class NomeDaClasse {
    // Atributos (variáveis de instância)
    tipo nomeAtributo;

    // Construtor (opcional)
    public NomeDaClasse(tipo parametro) {
        this.nomeAtributo = parametro;
    }

    // Métodos (comportamentos)
    public void metodo() {
        // Código do método
    }
}

```

## Exemplo Prático

 Aqui está um exemplo de uma classe chamada Carro: 
```
// Definição da classe Carro
public class Carro {
    // Atributos
    String modelo;
    int ano;

    // Construtor
    public Carro(String modelo, int ano) {
        this.modelo = modelo;
        this.ano = ano;
    }

    // Método para exibir detalhes do carro
    public void exibirDetalhes() {
        System.out.println("Modelo: " + modelo + ", Ano: " + ano);
    }
}

```

## Criando Objetos a Partir da Classe
Agora, podemos criar objetos dessa classe em outra classe principal:
```
public class Main {
    public static void main(String[] args) {
        // Criando um objeto da classe Carro
        Carro meuCarro = new Carro("Honda Civic", 2023);

        // Chamando o método da classe
        meuCarro.exibirDetalhes(); // Saída: Modelo: Honda Civic, Ano: 2023
    }
}

```


# Objeto
é uma instância/ criação dessas classes
