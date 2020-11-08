# Contribuindo

Este capítulo são as convenções seguidas pelos escritores deste tutorial. Quando escrevemos este, alguns padrões foram definidos para maximizar a consistência do mesmo.

## Estilo

Esses são convenções quanto ao estilo do documento.

### Tabelas

* Sentenças e frases com células das tabelas não devem terminar com ponto. 
* Tabelas introduzindo Opcodes devem ter as Instruções marcadas com negrito e pelo menos três colunas como visto no exemplo abaixo:

| Instrução | Nome Completo | Explicação |
| :--- | :--- | :--- |
| **LDA** | Load into accumulator | Armazena um valor no registrador A |

## Terminologia

| Regra | Exemplo |
| :--- | :--- |
| Quando referenciado o processador `Ricoh 5A22` use o`SNES` no lugar | `O SNES` é capaz de trabalhar no modo 8-bit e 16-bit |
| Quando referenciar uma area específica da memória do SNES, sempre precede-la com `endereço.` Preferencialmente junto com a área da memória \(ex: `RAM`\) | \(O\) `endereço da RAM` $7E0000 contém \[...\] |
| Quando referenciar o registradores A, X and Y, usar apenas`A`, `X` ou `Y` | `A` está agora no modo 8-bit. `X` é usado para indexar endereços. |
| Quando referenciar valores sempre precede-lo com`valor.` | A contem o `valor` $00 |

## Exemplos de Códigos

* Code shall use indentation when there are labels, sublabels or plus/minus labels on the same line as an instruction. The amount of indentation equals the length of the longest aforementioned type of label in the code block, including colon \("`:`"\), plus two additional spaces.
  * Code shall use whitespace for indentation, not tabs.
* Opcodes are written entirely in uppercase \(e.g.: `LDA`\).
* Labels are written in PascalCase \(e.g.: `Label1:`\).
* Sublabels are written entirely in lower, underscore-case and the name should semantically suit the parent label, without redundancy \(e.g.: `.return`\).
* Defines are written in PascalCase \(e.g.: `!SomeDefine`\).
* Direct data \(`db`, `dw`, `dl`, `dd`\) and opcode length specifiers \(`.b`, `.w`, `.l`\) are written entirely in lowercase.
* Comment indicators \(i.e. `;`\) shall start on column 20, and left-padded by whitespace, not tabs.
  * If there's no space for a comment on column 20, it will start on the same line.
* Comment indicators shall be followed by a whitespace, before the comment itself.
* There will be an extra new line after the opcodes `RTS`, `RTL`, `RTI`, `JMP`, `JML`, `BRA`, `BRL`.
* These are guidelines which are to be followed as strictly as possible, but there may be exceptional cases.

Example:

```text
SomeLabel:         ; This label is on its own line
LDA.b #$42
STA $00            ; This is a comment
RTS

.table:
db $01,$02,$03,$04 ; Another comment

.second_table:
db $01,$02,$03,$04,$01,$02,$03,$04 ; An exceptional comment

TestLabel:  LDA #$02 ; This label is on the same line as an instruction
            STA $01
            BNE +
            NOP
+           RTS      ; The code is indented according to "TestLabel"
```

