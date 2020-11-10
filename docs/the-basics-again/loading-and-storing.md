# Armazenando e Gravando

A primeira coisa que definitivamente precisamos aprender para começar a programar para o SNES, é como armazenar e gravar dados usando os diversos registradores do SNES. As instruções básicas para armazenar e gravar são `LDA` e `STA` respectivamente.

Como mencionado anteriormente, os 3 registradores principais são:

* A \(o acumulador\)
* X \(indexador\)
* Y \(indexador\)

Todos esses registradores podem trabalhar no modo 8-bit ou no modo 16-bit, por enquanto vamos considerar eles, como estando no modo 8-bit por padrão.

## LDA and STA

| Instrução | Nome Completo | Descrição |
| :--- | :--- | :--- |
| **LDA** | Load into accumulator | Armazena um valor no registrador A |
| **STA** | Store from accumulator | Grava o valor armazenado em A no endereço especificado |

Nós usaremos os endereços da RAM pra compreender melhor o funcionamento. É bem simples armazenar e gravar valores.

```text
LDA #$03           ; A = $03
STA $7E0001
```

Vamos observar o nosso código linha à linha:

```text
LDA #$03
```

Aqui armazenamos o valor $03 em A. O "\#" indica que o que estamos armazenando é um valor imediato e não um endereço. Após a execução dessa instrução, o conteudo do registrador A será $03. LDA pode armazenar valores numa faixa de $00-$FF no modo 8-bit e valores numa faixa de $0000-$FFFF no modo 16-bit.

```text
STA $7E0001
```

Aqui gravamos o valor armazenado em A no endereço da RAM $7E0001. Como o valor em A é $03, Oo valor no endereço da RAM $7E0001 também será $03. O conteúdo de A não é resetado. Isso quer dizer que você pode executar sequencias múltiplas desse comando para gravar os valores em mais de um endereço, dessa forma:

```text
LDA #$03
STA $7E0001
STA $7E0053
```

Um erro muito comum de iniciantes é confundir a notação e escrever STA com "\#$", por exemplo, `STA #$7E0001`. A instrução "STA \#$" não existe. Não faz sentido algum e não tem logica armezar um valor dentro de outro valor.

{% hint style="info" %}
Lembre-se, usar $ ao invés de \#$ após a instrução. Isso quer dizer que o parametro é um endereço e não um valor imediato.
{% endhint %}

Colocar ponto-e-virgula fará com que tudo que for escrito após ele seja ignorado pelo assemblador. Em outras palavras isso nos permite colocar comentários. Exemplo:

```text
LDA #$03           ; Aqui está um comentário sobre a linha de código
```

### Armazenando e Gravando valores

Of course, what would be the use to store things to a RAM address when you don’t know how to access the address again? You can load a RAM address’ contents into the A register by using LDA with a different addressing mode. Here is an example.

```text
LDA $7E0013
STA $7E0042
```

Again, we will look at this example line by line.

```text
LDA $7E0013
```

This will load the contents of the RAM address $7E0013 into A. Let’s assume that the contents were $33. So now, A has the value $33. The content of $7E0013 remains unchanged, because LDA copies the number rather than extracting it from the address. Note that this time we have used $ instead of \#$. This is because we wanted to access a RAM address. In the end, A has $33 and RAM $7E0013 has the value $33 also.

```text
STA $7E0042
```

This instruction will store the contents of the A register into the RAM address $7E0042. Of course, A will remain unchanged. RAM address $7E0042 is now $33. In short: the full example will copy the contents of $7E0013 over to $7E0042.

## LDY, STY, LDX, STX

Now that we have learned the basics of loading and store values into addresses, let’s introduce the same loading opcodes, but for the index registers:

| Opcode | Full name | Explanation |
| :--- | :--- | :--- |
| **LDY** | Load into Y | Load a value into Y |
| **STY** | Store from Y | Store Y's value into an address |
| **LDX** | Load into X | Load a value into X |
| **STX** | Store from X | Store X's value into an address |

The above opcodes behave exactly like LDA and STA. The only difference is that these make use of the X and the Y registers instead of the accumulator. For example:

```text
LDY #$03
STY $0001
```

Would store the number $03 into RAM address $7E0001, by utilizing the Y register. To use the X register, use LDX and STX. As for why the address is $0001 instead of $7E0001, please refer to this chapter: [Shorter addresses](shorter-addresses.md)

## STZ

There is another opcode which stores the number $00 into addresses directly.

| Opcode | Full name | Explanation |
| :--- | :--- | :--- |
| **STZ** | Store zero to memory | Sets the value of an address to 0 |

This opcode stores the number $00 into an address. It doesn’t even need the A, X or Y registers to load $00 first.

If you want to make a code that directly stores $00 in a RAM address, you could make it use 1 line:

```text
STZ $01            ; $7E0001 = $00. The A register is unaffected.
```

STZ will store zero to a specified RAM address. After this opcode, RAM address $7E0001 will now contain the number $00. Using STZ when A is in 16-bit mode **will** store $0000 to both RAM addresses $7E0001 and $7E0002.

