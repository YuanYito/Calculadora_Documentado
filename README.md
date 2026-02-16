```mermaid
classDiagram
    class Main {
        +main(args: String[])
    }

    class IEntrada {
        <<interface>>
        +solicitarNumero(mensaje: String) double
        +solicitarOperacion() String
    }

    class EntradaConsola {
        -scanner: Scanner
        +solicitarNumero(mensaje: String) double
        +solicitarOperacion() String
        -esNumerico(valor: String) boolean
        -esOperacionValida(op: String) boolean
    }

    class ISalida {
        <<interface>>
        +mostrarResultado(resultado: double)
        +mostrarError(mensaje: String)
    }

    class SalidaConsola {
        +mostrarResultado(resultado: double)
        +mostrarError(mensaje: String)
    }

    class ICalculadora {
        <<interface>>
        +sumar(a: double, b: double) double
        +restar(a: double, b: double) double
        +multiplicar(a: double, b: double) double
        +dividir(a: double, b: double) double
    }

    class Calculadora {
        +sumar(a: double, b: double) double
        +restar(a: double, b: double) double
        +multiplicar(a: double, b: double) double
        +dividir(a: double, b: double) double
    }

    class GestorCalculadora {
        -entrada: IEntrada
        -salida: ISalida
        -calculadora: ICalculadora
        +ejecutar()
        -procesarOperacion(op: String, n1: double, n2: double)
    }

    Main ..> GestorCalculadora : instanciar
    GestorCalculadora --> IEntrada : usa
    GestorCalculadora --> ISalida : usa
    GestorCalculadora --> ICalculator : usa
    IEntrada <|.. EntradaConsola
    ISalida <|.. SalidaConsola
    ICalculadora <|.. Calculadora
```

    Main ..> GestorCalculadora : instanciar
    GestorCalculadora --> IEntrada : usa
    GestorCalculadora --> ISalida : usa
    GestorCalculadora --> ICalculator : usa
    IEntrada <|.. EntradaConsola
    ISalida <|.. SalidaConsola
    ICalculadora <|.. Calculadora
