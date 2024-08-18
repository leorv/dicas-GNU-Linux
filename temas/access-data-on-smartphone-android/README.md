# Acessando Smartphone Android e manipulando arquivos com o Debian

language: pt-BR

## Introdução

Aqui vamos ver como transferir e manipular arquivos do nosso smartphone com o Debian.

Estes procedimentos deverão funcionar na maioria das distribuições linux, uma ou outra, talvez precisem de adaptações, mas acreditamos que com estes passos a coisa fique simples.

## Configurando MTP no GNU/Linux

Nas versões anteriores à 4.0 do Android, era possível simplesmente conectarmos o cabo USB no nosso PC e poderíamos passar os arquivos para o computador.

Porém, depois da versão 4.0 do Android, isso não é mais possível, agora temos o MTP, Media Transfer Protocol. Agora os arquivos são passados usando o MTP, e ao plugar o smartphone no GNU/Linux, não é mais possível acessar diretamente os arquivos do smartphone.

Por incrível que pareça, embora o Android use o kernel Linux como base, não possui compatibilidade nativa para o acesso MTP via porta USB.

### Método universal

Instalar o aplicativo MTP e dependências.

#### Instalar o gMTP

Acessar a central de aplicativos de sua distribuição e instalar o gMTP.

Este é o aplicativo responsável por fazer o acesso em ambiente gráfico aos arquivos do smartphone.

Provavelmente ao clicar em conectar dentro do aplicativo, será mostrada uma mensagem de erro.

Isso acontece porque temos que realizar algumas configurações manualmente. Mostradas mais a frente.

#### Instalar os pacotes.

instalar os pacotes mtp-tools e mtpfs.

O mtpfs atualmente se chama go-mtpfs. Abaixo está uma descrição do pacote, peguei no debian.pkgs.org:

> Go-mtpfs é um sistema de arquivos FUSE simples para montar dispositivos Android como um dispositivo MTP. Ele irá expor todas as áreas de armazenamento de um dispositivo na montagem e apenas lê metadados de arquivo conforme necessário, tornando-o montado rapidamente. Ele usa extensões Android para ler/gravar dados parciais, manipular arquivos grandes não requer espaço extra em /tmp.

Para instalar:

```
sudo apt-get install gmtp mtp-tools go-mtpfs
```

### Configurando o fabricante e o smartphone

Para vermos os dados do smartphone, com ele conectado, rode o comando:

```
sudo mtp-detect
```

Estamos interessados em dois códigos, do fabricante e do aparelho.

Procure por valores como vendor-id, será um código parecido com este 22b8, lembrando que o seu provavelmente será diferente.

Também será mostrado o código do produto, será familiar ao anterior.

Anote eles.

Entre no diretório /etc/udev/rules.d e crie o arquivo 51-android.rules

Precisará de privilégios root, para fazer o passo acima.

Escreve dentro do arquivo:

```
SUBSYSTEM=="usb", ATTR{idVendor}=="SEU CÓDIGO", ATTR{idProduct}=="SEU CÓDIGO", MODE="0666"
```

Agora vamos reiniciar o serviço para aplicar as novas configurações:

```
sudo service udev restart
```

Vamos adicionar seu usuário agora no serviço do mtpfs:

```
sudo adduser "NOME DO SEU USUÁRIO" fuse
```

Edite o último arquivo de nossa configuração:

/etc/fuse.conf

Descomente a linha do user_allow_other, retirando a #. Salve.

## Possíveis problemas

Para evitar quaisquer problemas, antes de conectar o smartphone no PC, esteja com ele desbloqueado, caso apareça a mensagem de permitir acesso aos arquivos, permita.

No Debian, pode aparecer uma mensagem para que você escolhe o que fazer, clique em montar, ou acessar arquivos pelo explorador de arquivos, algo do tipo.