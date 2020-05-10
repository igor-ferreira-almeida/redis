# Redis

## Instalação 

### Windows 

O Redis não suporta oficialmente o sistema operacional Windows, mas é possível instalar uma versão experimental, mantida pelo grupo Microsoft Open Tech. Por se tratar de uma versão experimental, é importante deixar claro que até o momento em que este curso foi escrito a sua instalação é recomendada apenas em ambiente de desenvolvimento.

Outra observação a ser feita, é que atualmente apenas a versão para instalações do Windows de 64-bit é suportada oficialmente pelo projeto Microsoft Open Tech.

A versão mantida pelo Microsoft Open Tech pode ser obtida através do link https://github.com/MSOpenTech/redis mas, para simplificar, vamos realizar o download de um arquivo de instalação no repositório do projeto através do link:

https://github.com/MSOpenTech/redis/releases/download/win-3.0.500/Redis-x64-3.0.500.msi

Após o download do arquivo, vamos executá-lo.

A seguir temos a tela de boas vindas do instalador do Redis. Clique no botão "Next".

O instalador do Redis no windows já configura um serviço para o servidor do Redis, por isso não é necessário iniciar o servidor. Podemos conectar abrindo o prompt de comando do Windows e executando o comando redis-cli.

Observação: caso você receba um erro dizendo que o comando redis-cli não foi encontrado após realizar os passos aqui descritos, reinicie o computador e tente utilizar o redis-cli novamente. Isso deve ser suficiente.

Caso haja problema na instalação: Verify that you have sufficient privileges o start system services

Acessar serviços do windows, ache o serviço do redis, dê um duplo clique, na tela que aparecer vá na aba logon e altere para conta do sistema local aplique e clique em retry! Espero ter ajudado! Estava com o mesmo problema.

### Mac OS

#### Home Brew

```
$ brew install redis
```

After installation, you will see some notification about some caveats on configuring. Just leave it and continue to following some tasks on this article.
Launch Redis on computer starts.

```
$ ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
```

##### Start Redis server via “launchctl”

```
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

##### Start Redis server using configuration file

```
$ redis-server /usr/local/etc/redis.conf
```

##### Stop Redis on autostart on computer start
```
$ launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

##### Location of Redis configuration file
```
/usr/local/etc/redis.conf
```

##### Uninstall Redis and its files.
```
$ brew uninstall redis
$ rm ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

##### Get Redis package information
```
$ brew info redis
```

##### Test if Redis server is running
```
$ redis-cli ping
```

[Referência - Pete Houston](https://medium.com/@petehouston/install-and-config-redis-on-mac-os-x-via-homebrew-eb8df9a4f298)

Para facilitar a inicialização é possível adicionar uma variável de ambiente para acessar o comando redis-cli de forma direta pelo terminal

Localizado em /Users/USUARIO
adicionar um arquivo caso ainda não exista como o nome __.bash_profile__

````
export JAVA_HOME=$(/usr/libexec/java_home)
export M2_HOME=$(/usr/local/Cellar/maven/3.6.2/libexec)
export REDIS_HOME=$(/usr/local/etc/redis.conf)
export PATH="$HOME/Library/Python/3.7/bin:$JAVA_HOME/bin:$M2_HOME/bin:$REDIS_HOME:$PATH"
````

Após essas configurações é possível subir o servidor do Redis, com o comando:

```
$ redis-server
```

Após subir o servidor basta acessar a linha de comando do Redis para acessar suas funcionalidades
```
$ redis-cli
```

## Funções Básicas

### Adicionar e atualizar

```
SET "CHAVE" VALOR
SET "total_de_cursos" 105
```

#### Múltiplos valores

```
MSET "CHAVE" VALOR "CHAVE" VALOR
MSET "total_de_cursos" 105 "quantidade_de_respostas" 144000
```

### Buscar

```
GET "CHAVE"
GET "total_de_cursos"
```

### Buscar

```
DEL "CHAVE"
GET "total_de_cursos"
```

### Exibir todas as chaves criadas 

````
KEYS *
