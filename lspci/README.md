# lspci

Vamos ao problema de "apresentar interfaces wi-fi".

- Não existem "comandos do Linux";
- Comandos não resolvem problemas;
- Você resolve problemas!

Dito isso...

- O utilitário lspci não tem comandos!
- O utilitário lspci não é o problema nem a solução do problema!
- O utilitário lspci, no máximo, é uma possível solução!
- O problema, segundo vc, é "apresentar interfaces wifi".

O que é ambíguo e, certamente, não é o que você realmente quer saber/obter!

"Você está perguntando sobre um problema ou está com dificuldades de executar uma das suas possíveis soluções?"

— Prof. Kretcheu

Dito isso, também...

O lspci não lista interfaces,  **o utilitário lista informações de todos os dispositivos conectados ao barramento PCI**. Logo, o que vc quer pode estar entre as informações listadas.

Sabendo que você queria se lembrar de um comando que o @kretcheu usa muito (porque ele sabe o que quer e já sabe como escrever de um jeito que o sistema pode interpretar), o maior problema nem é obter a informação, porque ela poderia ser obtida de muitas outras formas, mas o equívoco de tentar decorar "comandos" sem se dar ao trabalho de aprender a chegar até eles.

Então, vejamos a resposta do professor:

`lspci -nnkd::0280`

Aqui:

```
-nn exibe informações de ID da origem do dispositivo como nomes e números (nn).

-k inclui informações de módulos do kernel.

-d faz uma filtragem por dispositivo segundo o formato:

-d [FABRICANTE]:[BARRAMENTO]:[CLASSE][.FUNC]
```

Onde tudo entre colchetes é opcional. Logo, para filtrar pela classe, nós podemos omitir todo o restante, menos os separadores (os dois-pontos):

`-d ::CLASSE`

Mas, é muito difícil você se lembrar (ou saber de antemão) da classe e do formato a ser passado para a opção -d. Sem saber disso, eu executaria apenas:

`lspci -mkv`

Ou...

`lspci -mmkv`

Onde -mm exibe a listagem de forma mais legível e de fácil uso em scripts (com essa opção, o primeiro campo aparece como "Slot", em vez de "Device", o que diferencia do quarto campo, que aparece com o mesmo nome no print).

Depois disso, eu correria para os últimos dispositivos listados, porque a lista vem em ordem de slots, e os slots de dispositivos de rede têm ID mais alto (02:XX.X, 03..., 04...).

Ou seja, mesmo sem me lembrar dos detalhes para filtragem, a opção -mkv (ou -mmkv) é bem memorizável e me dá todas as informações de que eu realmente possa precisar. Resultando na saída formatada como no print.

Prof. Kretcheu adicionou lista de classes: https://salsa.debian.org/kretcheu/tutoriais/-/blob/master/pciids.classes.md


*Fonte: Blau Araújo (Grupo Curso GNU no Telegram).*
