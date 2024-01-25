# OpenSSH Server

## Introdução

SSH ("Secure SHell") é um protocolo para acessar com segurança um computador a partir de outro, executar programas e transferir arquivos.

## Instalação

A instalação das aplicações cliente e servidor OpenSSH é simples. Para instalar os aplicativos OpenSSH Client em seu sistema Ubuntu, use este comando em um terminal:

```
sudo apt install openssh-client
```
Para instalar a aplicação OpenSSH Server e os arquivos de suporte relacionado, use este comando em um terminal:

```
sudo apt install openssh-server
```
## Chaves SSH

Permite autenticação entre dois hosts sem a necessidade de senha. A autenticação de chave SSH usa *chave privada* e uma *chave pública*.

Para gerar as chaves, em um terminal digite:

```
ssh-keygen -t rsa
```
Isso irá gerar as chaves usando o *algoritimo RSA*. Você pode modificar o número de bits usando a opção `-b`. Por exemplo, para gerar chaves com 4096 bits, você pode fazer:

```
ssh-keygen -t rsa -b 4096
```
Durante o processo será solicitada uma senha. Basta pressionar *Enter* quando solicitado a criar a chave.  

Por padrão, a chave *pública* é salva no arquivo `~/.ssh/id_rsa.pub`, enquanto `~/.ssh/id_rsa` é a chave *privada*. Agora copie o arquivo `id_rsa.pub` para o host remoto e anexe-o `~/.ssh/authorized_keys` digitando:

```
ssh-copy-id username@hostremoto
```
Finalmente, verifique as permissões no arquivo `authorized_keys`, apenas o usuário autenticado deve ter permissões de leitura e gravação. Se as permissões não estiverem corretas, altere-as:

```
chmod 600 .ssh/authorized_keys
```
Agora você deve conseguir fazer SSH para o host sem ser solicitada uma senha.