# Instalação limpa e enxuta

Imagem: Debian net inst

## Partições

Manualmente:

Por exemplo, para um HD de 128Gb:

512mb &rarr; Início do disco; Usar como sistema especial EFI;
30Gb &rarr; ext4; / "barra"; Início do disco; Opções de montagem: `noatime; nodiratime;` se for SSD, com certeza `discard` pra preservar a vida dele. Ródulo: "Raiz"; Blocos reservados 0%.
91Gb &rarr; /home; ext4; Opções de montagem: as mesmas do /; Rótulo: "Home"; Blocos reservados: 0%.
4Gb &rarr; Área de troca, swap;

## Programas

Editar o sources.list em /etc/apt/sources.list, inserir o contrib e non-free caso precise. 

```
apt update

apt install vim

apt install bash-completion

apt install htop
```

Carregar o bash completion: rodar `source /etc/bash_completion`

## Bind9

```
apt install bind9 bind9-utils
```

## Deixar o shell mais amigável

Ir no bashrc, descomentar as linhas para deixar com cores, mais amigável.

Pode descomentar também os alias para evitar fazer cagada quando deleta, move, copia.

Ao final, adicionar:

```
source /etc/bash_completion
```

O acima vai carregar o bash_completion toda vez.

