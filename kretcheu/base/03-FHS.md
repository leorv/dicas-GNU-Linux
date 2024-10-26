O Filesystem Hierarchy Standard teve sua origem em 1996, com a [[comunidade BSD]] da universidade da Califórnia. Hoje é mantido pela Linux Foundation ([[LSB Workgroup]]).

Um padrão de uniformização, para facilitar o uso. Adotado por todas as distribuições Linux.

A distribuição [[Gobo Linux]] não usa esse padrão, usa um padrão completamente diferente.

Link para ver o padrão FHS 3.0 (versão atual): [refspecs fhs](https://refspecs.linuxfoundation.org/fhs.shtml)

Link do FHS do Debian: [debian fhs](https://www.debian.org/releases/stable/amd64/apcs02.en.html)

Para quem está acostumado com o WWOL (Windows Way Of Life), cada programa faz de um jeito! Não há organização.

Unix like -> "Cada coisa no lugar definido".

## Principais diretórios

| *diretório* | *função*       |
| ----------- | -------------- |
| /           | barra ou raiz  |
| /proc       | processos      |
| /dev        | dispositivos   |
| /boot       | kernel, initrd |
| /bin        | binários (E)   |
| /sbin       | binários adm   |
| /lib        | bibliotecas    |
| /etc        | configuração   |
| /media      | removíveis     |
| /mnt        | temporários    |
| /root       | usuário root   |
| /home       | usuários       |
| /tmp        | temporário     |
| /var        | variável       |

## Binários

| *diretório*    | *função*                                                            |
| -------------- | ------------------------------------------------------------------- |
| /usr/bin       | binários (instalação de programas, binários que não são essenciais) |
| /usr/sbin      | binários adm (binários do sistema)                                  |
| /usr/lib       | bibliotecas (que os programas usam)                                 |
| /usr/share     | independente (arquivos que são independentes da arquitetura)        |
| /usr/share/doc | documentação (ex. documentação do firefox)                          |
| /usr/share/man | manuais                                                             |

