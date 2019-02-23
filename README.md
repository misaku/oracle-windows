# Docker
link: [https://www.docker.com/](https://www.docker.com/)

Versão completa: 

[Docker Copleto Windows >=10 + Hyper-V](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)

Toolbox:

[Docker Toolbox Windows <=10 + VM](https://docs.docker.com/toolbox/overview/)

somente para toolbox:

```js
//modificar C:\Program Files\Docker Toolbox\start.sh. 

“${DOCKER_MACHINE}” create -d  virtualbox $PROXY_ENV "${VM}"

//Por

VB_OPTS="–virtualbox-disk-size 100000 --virtualbox-cpu-count 2 --virtualbox-memory 2048"
"${DOCKER_MACHINE}" create -d virtualbox $VB_OPTS $PROXY_ENV “${VM}”
```
Versão completa e toolbox:
```js
//Comandos iniciais
docker run hello-world
//Com esse comando o docker instala o primeiro container e faz um auto teste
//OBS sempre que um container nao funcionar tente resetar o docker e dar um stop e start no container
//o reset do docker é feito pelo daemon mas o stop e start pode ser feito com esses comandos
docker stop nomecontainer
docker start nomecontainer
```
# Oracle
link documentação:
- [oracle-docker](https://hub.docker.com/_/oracle-database-enterprise-edition)
- [sql developer](https://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html)

comandos:
```js
docker login
docker pull store/oracle/database-enterprise:12.2.0.1
//where <Oracle-DB> is the name of the container and 12.2.0.1 is the Docker image tag.
docker run -d -it -p 1521:1521 -p 5500:5500 --name <Oracle-DB> store/oracle/database-enterprise:12.2.0.1
//para acessar o banco pode usar o pgadmnin ou outra interface, e pela linha de comando docker segue os comandos abaixo
docker exec -it nome-container bash
//com esse comando vc consegue entrar na maquina e depois só usar p sqlplus
sqlplus sys/Oradoc_db1@ORCLCDB as sysdba
alter session set "_ORACLE_SCRIPT"=true;
CREATE USER loja IDENTIFIED BY loja_senha;
GRANT connect,resource TO loja;
exit;
exit;
```
