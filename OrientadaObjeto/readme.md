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
