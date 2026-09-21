```mermaid
classDiagram

    class Carta {
        -int indice
        Carta(Baraja baraja)
        +mostrar()
        +Pinta get()
        +NombreCarta get()
        +int getValor()
    }

    class Jugador {
        -Carta[] cartas
        -boolean[] enGrupo;
        +void repartir()
        +void mostrar()
        +String getGruposNombre()
        +String getGruposEscalera()
        +int getPuntaje()
    }

    class Baraja {
        -int totalBarajas
        -int[] disponibilidad;
        -Random r
        Baraja(int totalBarajas)
        +int sacarCarta()
    }

    class Juego {
        -Jugador jugador1
        -Jugador jugador2
        +void repartir()
        +void verificar()
    }

    class Pinta {
        <<enumeration>>
        TREBOL
        PICA
        CORAZON
        DIAMANTE
    }

    class NombreCarta {
        <<enumeration>>
        AS
        DOS
        TRES
        CUATRO
        CINCO
        SEIS
        SIETE
        OCHO
        NUEVE
        DIEZ
        JACK
        QUEEN
        KING
    }

    class Grupo {
        <<enumeration>>
        VACIO,
        NON,
        PAR,
        TERNA,
        CUARTA,
        QUINTA,
        SEXTA,
        SEPTIMA,
        OCTAVA,
        NOVENA,
        DECIMA
    }

    Jugador "1" *-- "10" Carta : reparte
    Carta --> Baraja 
    Carta --> Pinta
    Carta --> NombreCarta
    Jugador --> Baraja 
    Jugador --> Pinta
    Jugador --> NombreCarta
    Jugador --> Grupo
    Juego "1" *-- "2" Jugador : participa
    Juego "1" *-- "1" Baraja : contiene