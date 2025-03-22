# O que é uma interface?

Como você já aprendeu, os objetos definem sua interação com o mundo externo por meio dos métodos que eles expõem. <br>
Os métodos formam a interface do objeto com o mundo externo; os botões na frente do seu aparelho de televisão, por exemplo, <br>
são a interface entre você e a fiação elétrica do outro lado do seu invólucro de plástico. <br>
Você pressiona o botão "power" para ligar e desligar a televisão.

Em sua forma mais comum, uma interface é um grupo de métodos relacionados com corpos vazios. <br>
O comportamento de uma bicicleta, se especificado como uma interface, pode aparecer como segue:<br>

<br>

```

interface Bicycle {

    //  wheel revolutions per minute
    void changeCadence(int newValue);

    void changeGear(int newValue);

    void speedUp(int increment);

    void applyBrakes(int decrement);
}

```

<br>

Para implementar essa interface, o nome da sua classe mudaria (para uma marca específica de bicicleta, por exemplo, como ACMEBicycle), <br>
e você usaria a implementspalavra-chave na declaração da classe:<br>


```

class ACMEBicycle implements Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;

   // The compiler will now require that methods
   // changeCadence, changeGear, speedUp, and applyBrakes
   // all be implemented. Compilation will fail if those
   // methods are missing from this class.

    void changeCadence(int newValue) {
         cadence = newValue;
    }

    void changeGear(int newValue) {
         gear = newValue;
    }

    void speedUp(int increment) {
         speed = speed + increment;   
    }

    void applyBrakes(int decrement) {
         speed = speed - decrement;
    }

    void printStates() {
         System.out.println("cadence:" +
             cadence + " speed:" + 
             speed + " gear:" + gear);
    }
}

```

<br>

Implementar uma interface permite que uma classe se torne mais formal sobre o comportamento que ela promete fornecer. <br>
Interfaces formam um contrato entre a classe e o mundo externo, e esse contrato é imposto no momento da construção pelo compilador. <br>
Se sua classe alega implementar uma interface, todos os métodos definidos por essa interface devem aparecer em <br>
seu código-fonte antes que a classe seja compilada com sucesso.

<br>
  
  **Nota**: Para realmente compilar a ACMEBicycleclasse, você precisará adicionar a publicpalavra-chave ao início dos métodos de interface implementados. <br>
<br>
