# Formatação e gerenciamento de discos

## Criar um pen-drive do Debian

Digite o comando lsblk para listar os dispositivos conectados no seu PC e suas labels.

Quando você conectar um novo dispositivo no seu pc, o Linux vai atribuir uma label para ele, por exemplo o “/dev/sda” que é o HD onde o seu sistema está instalado, então o próximo dispositivo que você conectar receberá a label “/dev/sdb”, o próximo “/dev/sdc” e por aí adiante.

Quando o dispositivo está dividido em várias partições, cada partição recebera um número. Assim, por exemplo “/dev/sda1”, “/dev/sda2”, “/dev/sda3”, etc. Agora vamos supor que você tenha apenas um pendrive de 8 GB espetado, ele aparecerá como “/dev/sdb”. Desta forma, vamos criar a live USB nele, para isso vamos logar como usuário root e navegar até o diretório onde o arquivo .iso está guardado.

```
dd if=nome-da-iso-baixada.iso of=/dev/sdb
```

## Criar isos de outras distros

```
dd if=/dev/cdrom of=NomeDoArquivo.iso
```

Para gravar uma iso em um cd ou dvd, basta fazer o processo contrario, colocando uma mídia gravável no driver e digitando o comando abaixo.

```
dd if=NomeDoArquivo.iso of=/dev/cdrom
```

## Formatando pen-drives via terminal

Como usuário root.

Desmontamos o dispositivo que iremos formatar, você deve desmontar partição por partição:

```
umount /dev/sdb1
umount /dev/sdb2
```

**Atenção, antes verifique com o comando lsblk se você está desmontando a partição correta!!!**

### Criando partições

Comando cfdisk:

```
cfdisk /dev/sdb
```

Vai aparecer uma tabela com opções. Escolha como quiser. Apague tudo, crie uma ou mais partições dividindo-as, você pode dividindo-las em “GB” gigas, “MB” megas, “KB” kbytes, etc.

## Formatando partições com o comando mkfs

```
mkfs -t ext4 /dev/sdb1
```

ou usar:

```
mkfs.ext4 /dev/sdb1
```

Você também pode formatar o pendrive com outros sistemas de arquivos como o ntfs (Windows), por exemplo:

```
mkfs -t ntfs /dev/sdb1
```

ou 

```
mkfs.ntfs /dev/sdb1
```

## Permissões

Você pode formata-los em ext3, ext4, NTFS, etc, mas caso você escolha o formato “ext” você terá que mudar as permissões para poder acessar as partições que você acaba de criar, para isso basta montar o dispositivo em /mnt e alterar as permissões com o chmod.

```
mount /dev/sdb1 /mnt
```

```
chmod ugo+rw /mnt
```

```
umount /dev/sdb1
```

Muito bem, você acaba de formatar seu pendrive manualmente, agora você pode formatar seus dispositivos de armazenamento sem a necessidade de qualquer outro software adicional. Faça bom proveito de seus conhecimentos e compartilhe-os com as pessoas.
