# Little-endian

Dentro da memória do SNES, valores 16-bit e 24-bit são escritos sempre em "little-endian". Vamos usar como exemplo o valor $1234 que está gravado na RAM; $1234 não estará visível na memória, como $12 $34  e sim como, $34 $12. É dessa forma que o SNES trabalha. Quando um numero é lido no modo 16-bit, ele interpretara como $1234 não como $3412 como aparece na memória. O SNES faz essa inversão dos valores de forma automática.

Valores de 24-bit não são exceção. Valores como $123456, serão gravados na memória como $56 $34 $12.

Você pode escrever tudo normalmente em ASM sem se preocupar com o sistema "little-endian", porque tudo é manipulado automaticamente pelo SNES e pelo Assemblador. Você precisará apenas se preocupar quando for manipular valores 16-bit no modo 8-bit.

Por exemplo: se você gravar o valor $1234 no endereço $7E0000, na memória vai estar gravado $34 $12. Então, se você quiser acessar o low byte desse valor \(que é $34\) você precisará ler $7E00000 e não $7E0001.

O conceito de sistema "little-endian" é importante especialmente quando se está manipulando "ponteiros", assunto que será abordado futuramente nesse livro.

