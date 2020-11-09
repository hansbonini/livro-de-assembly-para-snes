# Os registradores do SNES

O SNES tem vários registradores usados para diferentes propósitos. Nenhum deles pode ser esquecido, eles são a razão para o SNES funcionar corretamente. Basicamente, registradores são "variáveis globais" que podem ser usadas para armazenar valores ou usadas para operações lógicas e matemáticas, e para outras coisas também. Esses registradores podem ser acessados a qualquer hora.

## Acumulador

O Acumulador também conhecido por **A,** geralmente é usado para operações matemáticas, deslocamento de bits, operações bitwise e carregar valores indiretos. A pode também armazenar variáveis de uso geral para posteriormente salva-las na memória ou em outros registradores. Esse registrador trabalha tanto com valores 8-bit quanto com valores 16-bit.

O Acumulador algumas vezes é referenciado como  `B` ou `C` em algumas instruções. B trata-se do high byte do acumulador, enquanto C quer dizer que o acumulador é totalmente 16-bit.

{% hint style="warning" %}
Na realidade, o registrador pode ser considerado sempre de 16-bit. Quando A está no modo 8-Bit, você acessa seu low byte do registrador. Quando A está no modo 16-bit você acessa tanto o high byte quanto o low byte do registrador. O high byte não é zerado quando o registrador A entra no modo 8-bit, mesmo quando novos valores são escritos em A, o high byte vai ser considerado como um valor "escondido". Vale ressaltar também, que certas instruções usam ambos os valores high e low byte do registrado A, independente se ele estiver ou não no modo 8-bit ou 16-bit.
{% endhint %}

## Indexados

O Indexadores são dois registradores, conhecidos como X e Y. Apesar se serem registradores separados, ambos possuem o mesmo propósito e funcionam da mesma forma. Esses registrados são feitos para indexar, algo que será explicado futuramente neste livro. Ambos os registradores podem ter valores 8-bit ou 16-bit. X e Y podem também armazenar variáveis de uso geral para posteriormente salva-las na memória ou em outros registradores. 

X e Y são "pares" - eles podem somente trabalhar com modos 8 e 16-bit ao mesmo tempo. Um não pode estar no modo 8-bit enquanto o outro está no modo 16-bit.

{% hint style="warning" %}
Quando X e Y deixam o modo 16-bit, seus high bytes são zerados para o valor $00, enquanto que no registrador A o high byte fica intacto.
{% endhint %}

## Paginação Direta

A paginação direta é um registrador 16-bit, usado para o modo de endereçamento de paginação direta \(explicado posteriormente neste livro\). Quando você acessar um endereço de memória pela notação de endereçamento direto, o valor na paginação direta será adicionado a este endereço. Você geralmente ignora esse registrador se está começando na linguagem assembly.

## Ponteiro de Pilha

O ponteiro de pilha é um registrador de 16-bit que armazena o ponteiro da pilha da memória RAM \(explicado posteriormente nesse livro\), relativo ao endereço de memória $0000000. É um registrador que muda dinamicamente conforme você faz o push ou pull \(coloca ou retira seus valores\) na pilha \(explicado posteriormente neste livro\).

## Estado do Processador

O registrador de estado do processador armazena as flags atuais do processador em formato 8-bit. Existem 8 flags de processador e cada uma ocupa 1 bit. Alterando esse registrador irá alterar o funcionamento de todo o SNES. As flags do processador serão explicadas posteriormente neste livro.

## Banco de Dados

O registrador de banco de dados armazena o o valor do banco atual em um único byte. Quando você acessa um endereço usando a notação de "endereçamento absoluto", o SNES irá usar esse registrador para determinar qual banco pertence esse endereço.

## Banco do Programa

O registrador de banco do programa continuamente segue o banco atual de cada instrução executada. Portanto, se você tiver um código executando no endereço $018009, esse registrador irá armazenar o valor $01 como banco.

## Contador do Programa

Esse registrador continuamente segue o high byte e o low byte de cada instrução executada. Portanto se você tiver um código executando no endereço $018009, o valor armazenado nesse registrador será $8009.

