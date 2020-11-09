# Binário

Outro base numérica importante é o sistema "binário". Em binários os dígitos podem ser apenas 2 valores: 0 ou 1. Um digito binário é chamador de "bit". E na linguagem assembly a denotação dos bits é precedida pelo carácter "%".

Um byte é constituído de oito "bits". Como um dígitos binário pode ser apenas dois valores, e um byte tem oito bits, existem 2⁸ possibilidades de byte.

Por exemplo, um byte composto pelos seguintes bits: `1001 0110` or `1001 0101`. O primeiro bit da esquerda para a direita é chamado de "bit 7" e o bit final é chamado de bit "0".

```text
Bit 7654 3210

    1001 0110
    1001 0101
    .... ....
```

A tabela a seguir é basicamente fácil para memorizar binários.

| Binary | Hexadecimal |
| :--- | :--- |
| `%0000 0001` | `$01` |
| `%0000 0010` | `$02` |
| `%0000 0100` | `$04` |
| `%0000 1000` | `$08` |
| `%0001 0000` | `$10` |
| `%0010 0000` | `$20` |
| `%0100 0000` | `$40` |
| `%1000 0000` | `$80` |

Note que aqui existe um espaço a cada 4 bits para tornar a leitura mais fácil, contudo, os assembladores não aceitam esse tipo de sintaxe. Grupos de 4 bits são chamados de "nibbles" e para o proósito desse capitulo, eles tornaram mais fácil para ler os binários. porque cada "nibble" corresponde à um digito em hexadecimal.

O SNES é capaz de trabalhar tanto no com valores 8-bit quanto valores 16-bit. Enquanto valores 8-bit são chamados de byte, valores 16-bit são chamados de "word". Que por sua vez estarão presentes dessa forma em binário:`10000101 11010101` \(que trata-se do valor `$85D5` na representação hexadecimal\). No caso de valores 16-bit o primeiro digito à esquerda é chamado de "bit 15" enquanto o último digito a direita é chamado de "bit 0":

```text
    1111 11             (leia de cima para baixo)            
Bit 5432 1098 7654 3210
    1000 0101 1101 0101
    0000 0000 1001 0110
    .... .... .... ....
```

## Flags

Binários são altamente úteis quando você precisa especificar valores hexadecimais com propósitos variados, por exemplo uma opção de Liga/Desliga para certos recursos. Esses bits são chamados de "flags" e geralmente são salvos na memória dos jogos.

Para exemplificar, você pode dividir um byte em 8 bits com cada bit tendo uma função única. O bit 7 pode indicar se está ou não chovendo no estágio, Bit 6 pode indicar se o estágio é horizontal ou vertical. Bit 5 pode indicar se está de dia ou de noite, etc. Dessa forma você poderá compactar diversas informações em único byte. Abaixo um exemplo de como isso ocorre em binário:

```text
10100000
││└───── flag "Está dia?"
│└───── flag "O estágio é Horizontal"
└───── flag "Está chovendo?"
```

Para finalizar, abaixo uma revisão de como contar em decimal, hexadecimal e binário:

| Decimal | Hexadecimal | Binário |
| :--- | :--- | :--- |
| `00` | `$00` | `%0000 0000` |
| `01` | `$01` | `%0000 0001` |
| `02` | `$02` | `%0000 0010` |
| `03` | `$03` | `%0000 0011` |
| `04` | `$04` | `%0000 0100` |
| `05` | `$05` | `%0000 0101` |
| `06` | `$06` | `%0000 0110` |
| `07` | `$07` | `%0000 0111` |
| `08` | `$08` | `%0000 1000` |
| `09` | `$09` | `%0000 1001` |
| `10` | `$0A` | `%0000 1010` |
| `11` | `$0B` | `%0000 1011` |
| `12` | `$0C` | `%0000 1100` |
| `13` | `$0D` | `%0000 1101` |
| `14` | `$0E` | `%0000 1110` |
| `15` | `$0F` | `%0000 1111` |
| `16` | `$10` | `%0001 0000` |
| `17` | `$11` | `%0001 0001` |
| ... | ... | ... |
| `254` | `$FE` | `%1111 1110` |
| `255` | `$FF` | `%1111 1111` |

## Notação

Em algumas ocasiões a escrita de bits pode ser parcial, como `11` ou `110 0000`. Isso pode tornar o valor binário díficil de ler por que o convencional é escreve-los em grupos de 8 bits. Em todo caso, para ler, você precisa apenas adicionar zeros à esquerda do dígito até completar grupos de 8 ou 16-bits.

Em 8-bit:

* `11` será `00000011`
* `1100000` será `01100000`

Em 16-bit:

* `11` será `00000000 00000011`
* `1100000` será `00000000 01100000`

Você pode converter entre decimais, hexadecimais e binários usando a calculadora do seu sistema operacional no modo "Programação".  Existem várias calculadoras online também. A sintaxe da linguagem assemby aceita todas as bases numéricas, então você não precisa ficar convertendo entre elas em si.

