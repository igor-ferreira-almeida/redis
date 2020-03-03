# Redis

## Instalação 

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

