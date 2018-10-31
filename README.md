# aplicacao
CRUD (Back x Front) ASP.NET C# v4.5+ MVC

1. O teste foi desenvolvido com o back-end e front-end separadas,
segue abaixo algumas informações para rodar:

	A. No arquivo Web.config do projeto Aplicação voçe deve 
     alterar a Key UrlWeAPI do appSettings para o local que
     vai estar rodando a API em sua máquina;
	3. No arquivo Web.config do projeto WebAPI voçe deve 
     alterar as connectionStrings (TesteCRUDDapper, TesteCRUDEntities) de
     acordo com os dados necessários para acessar o banco de dados SQLServer;
	4. Segue abaixo os scripts para criação do banco;

#########################################
##    Script para criar a DataBase     ##
#########################################
create database TesteCRUD
use TesteCRUD

#########################################
##    Script para criar as Tabelas     ##
#########################################
CREATE TABLE Genero (
    GeneroID int IDENTITY(1,1) PRIMARY KEY,
    Nome varchar(100) NOT NULL,
    DtCriacao date,
    Ativo char(1)
);

CREATE TABLE Acesso (
    AcessoID int IDENTITY(1,1) PRIMARY KEY,
    Email varchar(100) NOT NULL,
    Senha varchar(100) NOT NULL,
    Ativo char(1),
    Perfil char(1),
    Nome varchar(100) NOT NULL,
    Sobrenome varchar(100)
);

CREATE TABLE Filme (
    FilmeID int IDENTITY(1,1) PRIMARY KEY,
    Nome varchar(100) NOT NULL,
    DtCriacao date,
    Ativo char(1),
    GeneroID int FOREIGN KEY REFERENCES Genero(GeneroID),
);

CREATE TABLE Locacao (
    LocacaoID int,
    FilmeID int FOREIGN KEY REFERENCES Filme(FilmeID),
    ClienteCPF varchar(14),
    DtLocacao date,
    CONSTRAINT PK_LocacaoFilmePK PRIMARY KEY (LocacaoID, FilmeID)
);

#########################################
## Incluir genero para popular a combo ##
#########################################
INSERT INTO Genero(Nome, DtCriacao, Ativo)
VALUES ('Ação', '2018-10-20', 1);
INSERT INTO Genero(Nome, DtCriacao, Ativo)
VALUES ('Ficção', '2018-10-20', 1);
INSERT INTO Genero(Nome, DtCriacao, Ativo)
VALUES ('Fantasia', '2018-10-20', 1);
INSERT INTO Genero(Nome, DtCriacao, Ativo)
VALUES ('Terror', '2018-10-20', 1);
INSERT INTO Genero(Nome, DtCriacao, Ativo)
VALUES ('Suspense', '2018-10-20', 1);
INSERT INTO Genero(Nome, DtCriacao, Ativo)
VALUES ('Aventura', '2018-10-20', 1);
INSERT INTO Genero(Nome, DtCriacao, Ativo)
VALUES ('Romance', '2018-10-20', 1)



