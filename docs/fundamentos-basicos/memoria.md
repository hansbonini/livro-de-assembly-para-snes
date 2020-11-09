# A memória do SNES

Escrever na linguagem assembly envolve escrever diversas instruções de armazenar valores e salvar valores em determinados endereços para conseguir o resultado desejado, como. por exemplo mudar o efeito de um item que seu personagem coleta. Quando escrevendo em linguagem assembly, trabalhamos com a memória do SNES grande parte do tempo.

A memória do SNES é basicamente uma região de bytes, e cada byte é localizado em um determinado endereço. Pense nela como este tabuleiro de xadrez:

![](../.gitbook/assets/chessboard.png)

Como você pode ver, para referenciarmos certa casa do tabuleiro, a imagem faz uso de linhas e colunas numeradas. O endereço em que está a Rainha no caso \(o valor\) seria D8, por exemplo. Dessa forma uma única casa do tabuleiro não pode armazenar mais que um valor. Essa mesma lógica se aplica à memória do SNES.

A memória do SNES está mapeada do endereço $000000 até o endereço $FFFFFF, geralmente, a faixa de endereço $000000 até $7FFFFF é o mais comum de ser usado. O formato do endereço é o seguinte: $BBHHDD.

* BB é o banco ou "bank byte" do endereço
* HH é o "high byte" do endereço
* DD  é o "low byte" do endereço

Endereços podem ser escritos de 3 formas diferentes: $BBHHDD, $HHDD e $DD, que seria algo como $7E0003, $0003 e $03.

* Endereços na notação $DD são chamados de “paginação direta"
* Endereço na notação $HHDD são chamados de “endereços absolutos”
* Endereços na notação $BBHHDD são chamados de “endereços long”

Como estabelecido anteriormente, o endereço pode conter apenas um byte. Se você estiver no modo 16 bit,  quer dizer que você estará acessando o `endereço` e o `endereço+1`, porque o modo 16-bit consiste em acessos de 2 bytes.

Aqui está uma generalização da memória básica do SNES \(também conhecido por mapeamento de memória\):

![The &#x201C;LoROM&#x201D; Memory Map](../.gitbook/assets/memory.png)

O mapeamento da memória está no formato "LoROM". Se você for um romhacker do SMW, não deve ter problema com isso, apenas tenha certeza de memorizar isso.

## ROM

ROM é o acrônimo de "Read-Only Memory" \(Memória somente de leitura\) e é isso exatamente o que podemos fazer com esse tipo de memória, apenas ler. Isso quer dizer que você não vai conseguir salvar valores na ROM com ASM durante a execução do jogo. O que você pode fazer é programar o jogo para conter dentro dela os valores dos dados, textos, gráficos, músicas e outras coisas. Este é o arquivo .smc/.sfc/.fig/etc que você "carrega no emulador".

## RAM

RAM é o acrônimo para "Random-Access Memory" \(Memória de Acesso Aleatório\). Esta sim é uma memória dinâmica que permite que você salve valores durante a execução do jogo como desejar. É nela que você irá salvar as variáveis que são importantes e tem significância. A RAM pode ser escrita para salvar várias coisas. Por exemplo, se você escrever nela $04 para o número de vidas de um personagem, então seu personagem terá exatamente 4 vidas.

A memória RAM do SNES tem 128kB de tamanho, e está localizada na faixa de endereços 7E0000 até $7FFFFF. A memóra RAM do SNES é completamente genérica. Não existe nenhum tipo de regra que define por exemplo, que o "endereço $7E0120 vai ser sempre para definir o número de vidas de um personagem". Você pode definir qualquer endereço para qualquer propósito, escrevendo seu código em linguagem assembly. 

O mapeamento de memória exibe os bancos de paginação de $00 à $3f contendo o "espelho" da RAM. Endereços espelhados da RAM contem o mesmo valor do endereço normal referente. Isso quer dizer que $001234 contém o mesmo valor de $0F1234 sempre. Com a RAM espelhada durante a execução da ROM, todos esses bancos pode ser acessado na faixa de $7E0000 à $7E1FFF de forma fácil. Enquanto, que valores de banco na faixa de $40 à $6F tem mais problemas de acesso à RAM por não estarem espelhados.

PAra entender de forma simples, você pode assumir que o banco $00 é igual ao banco $7E.

## SRAM

SRAM é o acrônimo para  "Static Random-Access Memory" \(Memória Estática de Acesso Aleatório\). Ela possui também 128kB de tamanho e é fica localizada em blocos de 32kb nas faixas $700000-$707FFF, $710000-$717FFF, $720000-$727FFF e $730000-$737FFF, entretanto o tamanho final da SRAM depende das especificações da ROM, dependendo exclusivamente de algo chamado "cabeçalho interno da ROM\). A SRAM não pode ser espelhada em outros bancos.

A SRAM funciona exatamente como a RAM, você pode ler e salvar valores nela, porém, esses valores não são limpos quando o reset do SNES é acionado. A SRAM continua ali enquanto a bateria do cartucho no SNES durar. Quando a bateria acaba, ou, se é removida do cartucho, todos esses dados armazenados na SRAM são perdidos para sepre. Nos emuladores a SRAM é salva em arquivos de extensão .srm.

A SRAM usualmente é usada para salvar o seu progresso no jogo, entrentato, pode também ser usada como espaço extra da RAM.

