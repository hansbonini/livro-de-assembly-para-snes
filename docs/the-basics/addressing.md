# Modos de Endereçamento

Existem diferentes modos de endereçamento no 65c816. Modos de endereçamento são usados para fazer com que as instruções acessem endereços e valores de diferentes formas, por exemplo, de forma "indexada" ou "direta indireta" \(explicado posteriormente neste livro\). Usando esses modos, você poderá acessar valores e endereços da memória de várias formas. Por exemplo, você pode imediatamente armazenar um valor em algum registrador, como o A. Tenha em mente que nem todos os modos são suportados por algumas instruções, existem algumas com um leque particular de modos de endereçamento. Os modos de endereçamento mais relevantes você encontra abaixo.

## Imediato 8/16 bit

Este modo de endereçamento define um valor absoluto, pode ser escrito usando a notação `#$XX` quando no modo 8-bit ou `#$XXXX` quando no modo 16-bit. O \# serve para indicar que é um "valor imediato", enquanto que $ é o indicador de valor hexadecimal. Usando somente \# fará com que o valor seja decimal. Por exemplo, \#10 é o mesmo que \#$0A. Pense no valor imediato como um número que você precisa anotar imediatamente em algum lugar.

## Paginação Direta

Este modo de endereçamento define um endereço de página direto, pode ser escrito usando a notação  `$XX`.

A paginação direta será os dois últimos dígitos hexadecimais de um endereçamento long. Por exemplo, o endereço $7E0011 como paginação direta será $11. Quando armazenado a partir de paginação direta, o valor do banco será sempre $00, sem exceções. Se você escrever a instrução "LDA $11" por exemplo, irá carregar o conteúdo de $000011 no acumulador, que também pode estar espelhado em $7E0011 \(lembre-se da ilustração sobre a memória do SNES\). Ou seja, você armazena também o conteúdo de $7E0011 em A.

## Absoluto

Este modo de endereçamento define um endereço absoluto, pode ser escrito usando a notação `$XXXX`.

O endereço absoluto será os últiimos 4 digitos hexadecimais de um endereço long. Usando o exemplo anterior, o endereço $7E0011 quando em endereçamento absoluto será $0011. O byte referente ao banco do endereço absoluto será determinado pelo registrador de banco de dados.

## Long

Este modo de endereçamento define um endereço long, pose ser escrito usando a notação`$XXXXXX`.

Endereços long tem algumas complicações quando se trabalha com bancos e espelhamento. Entretanto você não precisa se preocupar com o que o registrador de banco de dados está armazenando no momento. Com endereços long você pode acessar quaisquer endereços na memória do SNES.

## Outros modos de endereçamento

O SNES suporta outros modos de endereçamento. Os endereçamentos apresentados anteriormente são os fundamentais. Porém, existem vários outros modos como: versões indexadas da paginação direta, absoluto e long, e outros. Eles serão explicados futuramente neste livro porque não convém didaticamente aprende-los por enquanto. Eles farão mais sentido no futuro.

