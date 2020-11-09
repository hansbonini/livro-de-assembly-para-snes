# Hexadecimal

Para programar em ASM do 65c816, é necessário alguns conhecimentos básico sobre bases hexadecimais. Hexadecimal, mais conhecido por "hex", é uma base numérica assim como decimal, que as pessoas usam diariamente para contar. No hexadecimais, existe 6 dígitos adicionais, que são numerados de A até F como visto na tabela a seguir.

| Decimal | Hexadecimal |
| :--- | :--- |
| 0 | 0 |
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |
| 4 | 4 |
| 5 | 5 |
| 6 | 6 |
| 7 | 7 |
| 8 | 8 |
| 9 | 9 |
| 10 | A |
| 11 | B |
| 12 | C |
| 13 | D |
| 14 | E |
| 15 | F |
| 16 | 10 |
| 17 | 11 |
| ... | ... |
| 255 | FF |

Existem várias formar de denotar valores hexadecimais para que os leitores não os confundam com valores decimais. Elas são:

* Valores hexadecimais precedidos por "0x" \(ex: 0x42\)
* Valores hexadecimais precedidos por "$" \(ex: $42\)
* Valores hexadecimais com o sufixo "H" \(exemplo 42H\)

Por convenção este tutorial usa valores hexadecimais precedidos por "$".

Na linguagem assembly, um valor hexadecimal de dois digitos é chamado de "byte". O que significa que qualquer valor em um intervalo de $00 até $FF será considerado como um byte.

## Valores signed e unsigned

No mundo real, números podem ser positivos ou negativos. Na linguagem assembly, dependendo do código, valores podem ser tratados como "signed" ou "unsigned". "Signed" será atribuído a quaisquer valores que podem ser negativos: o valor $80 ou maior será considerado negativo caso a denotação for decimal, começando do valor -128, e contando regressivamente enquanto o valor hexadecimal conta progressivamente, como pode ser visto na tabela à seguir.

| Decimal | Hexadecimal |
| :--- | :--- |
| 126 | $7E |
| 127 | $7F |
| -128 | $80 |
| -127 | $81 |
| ... | ... |
| -1 | $FF |

A presença de valores negativo vai depende da programação do jogo. Por exemplo, um personagem pode ter velocidade positiva ou negativa \(como resultado avança ou recua\), mas o personagem não pode ter vidas negativas ou pontos \(porque não faria sentido algum\). Vale ressaltar que o valor -0 não existe.

## **Valores hexadecimais de 4 dígitos**

Os valores hexadecimais podem contar além de dois dígitos, como você pode ver abaixo.

| Decimal | Hexadecimal |
| :--- | :--- |
| 254 | $FE |
| 255 | $FF |
| 256 | $0100 |
| 257 | $0101 |
| ... | ... |
| 65535 | $FFFF |

O formato nesse caso é $HHLL

* HH é o "high byte" do valor
* LL é o "low byte" do valor

