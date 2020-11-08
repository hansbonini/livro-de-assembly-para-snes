# Introdução

Esta é uma versão online do meu tutorial de assembly para 65c816 que está hospedado no [SMW Central](https://www.smwcentral.net/). Eu originalmente escrevi este tutorial para ensinar para os membros da comunidade [SMW Central](https://www.smwcentral.net/) a linguagem assembly 65c816 em inglês pleno. Atualmente, ele é lido por muitos pessoas da cena da ROMHacking em geral. Por isso, tomei a decisão de move-lo para o Github, para que pessoas possam fazer me 

Todavia, mesmo sendo membro da SMW Central, esse tutorial não está associado com o jogo Super Mario World, ou seja, ele não foi feito especificamente para esse jogo. Podendo ser aplicado para o SNES em geral.

## A Linguagem

A linguagem assembly do 65C816 é usada pelo chip RICOH 5A22 do Super Nintendo Entertainment Syystem \(SNES\). Separando o acrônimo 65c816 em parte: `816` significa que o processador suporta tanto o modo 8-bit quanto o modo 16-bit. A letra `c` vem da sigla CMOS, enquanto `65` significa que é um processador da família 65xx. Um processador supostamente revolucionário para seu tempo. Esse  tutorial irá explicar mnemônicos/instruções e como usa-las adequadamente. Esse tutorial não foca em tópicos específicos da arquitetura SNES, como registradores de hardware.

Com a linguagem assembly 65c816 você pode programar uma gama  de coisas específicas para jogos de SNES \(como novos recursos para o Super Mario World\). ASM é a segunda geração de linguagem de programação, considerada de baixo-nível quando comparada à C\# por exemplo. É o que conhecemos como código de máquina legível, que posteriormente será traduzido em código de máquina hexadecimal \(bytes\). Todos os opcodes consistem  em 3 letras, com ou sem parâmetros.

## Agradecimentos Especiais

Meus agradecimento especiais as pessoas que revisaram o tutorial original postado no SMW Central: [**spigmike**](https://www.smwcentral.net/?p=profile&id=132)**,** [**Roy**](https://www.smwcentral.net/?p=profile&id=845)**,** [**smkdan**](https://www.smwcentral.net/?p=profile&id=411)**,** [**S.N.N**](https://www.smwcentral.net/?p=profile&id=23)**,** [**andy\_k\_250**](https://www.smwcentral.net/?p=profile&id=67)**,** [**Domiok**](https://www.smwcentral.net/?p=profile&id=7211)**,** [**reghrhre**](https://www.smwcentral.net/?p=profile&id=4176)**,** [**ChaoticFox**](https://www.smwcentral.net/?p=profile&id=3462)**,** [**Tails\_155**](https://www.smwcentral.net/?p=profile&id=6151)**,** [**GreenHammerBro**](https://www.smwcentral.net/?p=profile&id=18802)**,** [**Vitor Vilela**](https://www.smwcentral.net/?p=profile&id=8251)

Meu agradecimentos especiais aos [contribuidores](https://github.com/Ersanio/snes-assembly-book/graphs/contributors) deste repositório!

