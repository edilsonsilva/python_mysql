# Conexão do Python com o MySQL

!["Imagem Python com MySQL"](https://miro.medium.com/v2/resize:fit:1137/1*OnDVcS17HTWZ2L2vPaaQ1A.png)

## Drive de comunicação com o mysql
Para estabelecer a comunicação entre o Python e o banco de dados mysql, iremos usar o seguinte drive:
<a href="https://pypi.org/project/mysql-connector-python/#description"> https://pypi.org/project/mysql-connector-python/#description </a>

### Comando para instalar o drive
```python
    python -m pip install mysql-connector-python
```
### Configuração do banco de dados MySQL
O nosso banco de dados está em um container de docker. Para acessá-lo será necessário criar o container, então faremos os seguintes comandos em um servidor Fedora com o docker instalado:

#### Criação do volume
```shell
mkdir dadosclientes
```

#### Criação do container
<p style="text-align:center">
<img src="https://cdn.iconscout.com/icon/free/png-256/free-docker-226091.png" height="100" width="100">
</p>

```shell
docker run --name srv-mysql -v ~/dadosclientes:/var/lib/mysql -p 3784:3306 -e MYSQL_ROOT_PASSWORD=senac@123 -d mysql
```
### Criação do banco de dados e da tabela clientes

```sql
CREATE DATABASE banco;
USE banco;
CREATE TABLE clientes(
clientes_id int auto_increment primary key,
nome_cliente varchar(50) not null,
email varchar(100) not null unique,
telefone varchar(20)
)
```