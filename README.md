# OpenSSH Server

O SSH (Secure SHell) é um protocolo amplamente utilizado para acesso remoto seguro a sistemas Unix-like, permitindo a execução de comandos e a transferência de arquivos de forma segura.

## Visão Geral 

O OpenSSH Server é uma implementação do protocolo SSH que permite aos usuários acessar e gerenciar remotamente computadores de forma segura. Neste guia, abordaremos como instalar e configurar o OpenSSH Server em um ambiente Ubuntu, bem como como utilizar chaves SSH para autenticação segura entre hosts.

## Requisitos

Antes de prosseguir, certifique-se de ter:

* Um sistema Ubuntu instalado.
* Acesso ao terminal com permissões de superusuário.

## Instruções

1. [Instalação](#instalação)
2. [Chaves SSH](#chaves-ssh)
3. [Conclusão](#conclusão)

## Instalação

A instalação do cliente e do servidor OpenSSH é simples. Execute os seguintes comandos em um terminal:

```
sudo apt install openssh-client
sudo apt install openssh-server
```

## Chaves SSH

As chaves SSH permitem autenticação entre dois hosts sem a necessidade de senha. Para gerar as chaves, execute o seguinte comando:

```
ssh-keygen -t rsa
```

Isso irá gerar as chaves usando o algoritmo RSA. Você pode modificar o número de bits usando a opção -b. Por exemplo, para gerar chaves com 4096 bits, você pode executar:

```
ssh-keygen -t rsa -b 4096
```

Isso irá gerar as chaves usando o algoritmo RSA. Durante o processo, será solicitada uma senha. Basta pressionar Enter quando solicitado a criar a chave. Por padrão, a chave pública é salva no arquivo `~/.ssh/id_rsa.pub`, enquanto `~/.ssh/id_rsa` é a chave privada.

Copie o arquivo `id_rsa.pub` para o host remoto e anexe-o ao arquivo `~/.ssh/authorized_keys`:

```
ssh-copy-id username@hostremoto
```

Por fim, verifique as permissões no arquivo authorized_keys e ajuste-as, se necessário:

```
chmod 600 .ssh/authorized_keys
```

## Conclusão

Parabéns! Você configurou com sucesso o OpenSSH Server em seu sistema Ubuntu, permitindo acesso remoto seguro. Se necessário, consulte a documentação oficial para obter mais informações sobre como utilizar o OpenSSH Server.

## Contribuição

Se você tiver sugestões de melhorias ou correções para este guia, sinta-se à vontade para enviar uma pull request.

## Referências

* [Documentação oficial do Ubuntu sobre o serviço OpenSSH](https://ubuntu.com/server/docs/service-openssh)

## Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).