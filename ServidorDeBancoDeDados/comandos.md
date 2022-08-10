## Servidor de Banco de Dados com Linux

### Instalando o MySQL
    - apt search mysql-server 
    - apt install mysql-server-8.0 -y
    - mysql -u root -p (acessar o mysql com o root)
    - show databases; (mostrar listas do mysql)
    - create database Pessoas; (Criar banco de dados)
    - use Pessoas (usar o banco de dados pessoas)
    - create table Nomes(PessoasID int, Nome varchar(50), Sobrenome varchar(50));
    - exit (sair do mysql)