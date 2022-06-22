# Firmware-realtek

listar e colocar em um arquivo:

```
lspci -vmmnn > lspci.txt
```

Jogar neste site: https://h-node.org/search/form/en

Ele identifica todo seu hardware e diz pra você o que funciona só com softwares livres e o que não funciona. Bem prático.

## Sobre o Debian

O Debian oficial não vem com nada proprietário, ele te dá a liberdade de instalar firmwares proprietários que você venha precisar, caso você queira.

Diferente do Ubuntu e Mint, por exemplo, que já vem com eles por padrão.

Tem também as imagens não oficiais do Debian que incluem os mesmos firmwares proprietários supracitados. Você provavelmente não teria problemas se tivesse usado uma dessas imagens. E não precisaria de Ubuntu e derivados pra isso. Ou seja, o problema não está no Debian, e sim nos componentes do seu hardware que não respeitam sua liberdade e não funcionam com software livre.

Infelizmente isso é muito comum, então temos que votar com nossa carteira, escolhendo componentes de hardware que respeitem nossa liberdade e funcionem com software livre em detrimento das alternativas.

## Site oficial do Debian

Aqui está no site oficial do Debian:

https://cdimage.debian.org/cdimage/unofficial/non-free/firmware/bullseye/current

Para a versão Bullseye, mas pode encontrar de acordo com sua versão em particular.

## Garantindo integridade do arquivo

Se quiser garantir a integridade do arquivo confira o checksum.

```
sha256sum ~/Downloads/firmware.zip
```

No comando acima, confira o caminho onde se localiza o arquivo.

Depois, confira se o hash bate com os oficiais:

https://cdimage.debian.org/cdimage/unofficial/non-free/firmware/bullseye/current/SHA256SUMS

## Somente com o arquivo da realtek

Baixar o firmware:

https://packages.debian.org/bullseye/all/firmware-realtek/download

O caso acima é para o Bullseye, adapte para sua particularidade.

Para poder instalar:

```
sudo apt install ./firmware-realtek_20210315-3_all.deb
```

Com o terminal no diretório do arquivo.

O ./ na frente é fundamental para instalar pacotes .deb locais.

## Caso a luz da placa não tenha acendido

Dá um ip link e veja o que aparece.

```
ip link
```

Depois:

```
ip link set enp3s0 up
```

## Caso só tiver ipv6

Dá um:

```
dhcpcd
```

ou

```
dhclient
```

```
systemctl enable --now dhclient
```
