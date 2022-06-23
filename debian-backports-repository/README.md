# Adicionar o repositório backports

Adicionar o repositório backports no seu /etc/apt/sources.list

```
deb http://deb.debian.org/debian bullseye-backports main
```

Depois dar um apt update e apt upgrade

Dê o seguinte comando para instalar a versao do backports.

```
apt install -t bullseye-backports gajim gajim-omemo
```

o ideal antes dessa instalação é remover os pacotes instalados do gajim da versao do stable com comando:

```
apt remove gajim*
```

para evitar que alguns pacotes da versao antiga continuem junto com o do backports, pq nao tem atualizado no backports todos os pacotes gajim-....., apenas o gajim-omemo, gajim-openpgp gajim-pgp e gajim-triggers e o gajim  
