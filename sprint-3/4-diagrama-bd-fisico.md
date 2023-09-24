## Diagrama Físico

CREATE DATABASE syspayment;

USE syspayment

CREATE TABLE Funcionario_Usuario (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
sexo CHAR,
nome VARCHAR (50) NOT NULL,
cpf VARCHAR (15) NOT NULL,
tel VARCHAR (10) NOT NULL,
email VARCHAR (30) NOT NULL,
cep VARCHAR(9) NOT NULL,
cidade VARCHAR(50) NOT NULL,
estado VARCHAR(50) NOT NULL,
pais VARCHAR(50) NOT NULL,
rua VARCHAR(50) NOT NULL,
bairro VARCHAR(50) NOT NULL,
numero INTEGER NOT NULL,
complemento VARCHAR(20),
dta_nasc DATE NOT NULL,
qnt_dependentes INTEGER NOT NULL,
dta_admissao DATE NOT NULL ,
hora_inicio TIME NOT NULL,
hora_final TIME NOT NULL,
usuario VARCHAR (20) NOT NULL,
senha VARCHAR (30) NOT NULL,
ult_acesso DATE,
fk_Perfil_id INTEGER
);
--DROP TABLE Funcionario_Usuario;

CREATE TABLE Perfil (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
descr VARCHAR (30) NOT NULL
);
--DROP TABLE

CREATE TABLE Operacao_funcionario (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
dta_de DATE NOT NULL,
dta_ate DATE,
fk_Funcionario_Usuario_id INTEGER,
fk_Operacoes_id INTEGER
);
--DROP TABLE Operacao_funcionario

CREATE TABLE Operacoes (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
valor DECIMAL(9,2) NOT NULL,
operacao CHAR NOT NULL,
percentual DECIMAL (9,2) ,
salario_utilizado CHAR,
fk_Operacoes_desc_id INTEGER,
tipo_salario CHAR,
bloqueia_login CHAR
);
--DROP TABLE Operacoes

CREATE TABLE Cargo (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
descr VARCHAR (30) NOT NULL,
cbo VARCHAR (15) NOT NULL,
Periculosidade CHAR NOT NULL
);
--DROP TABLE Cargo

CREATE TABLE Estabelecimento (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
cnpj VARCHAR (20) NOT NULL,
nome VARCHAR (50) NOT NULL,
filial VARCHAR (5) NOT NULL
);
--DROP TABLE Estabelecimento

CREATE TABLE Holerite (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
dta_base DATE NOT NULL,
salario_base DECIMAL (9,2) NOT NULL,
total_vencimento DECIMAL (9,2) NOT NULL,
total_desconto DECIMAL (9,2) NOT NULL,
sal_contr_inss DECIMAL (9,2) NOT NULL,
base_calc_fgts DECIMAL (9,2) NOT NULL,
base_calc_irf DECIMAL (9,2) NOT NULL,
faixa_irf DECIMAL (9,2) NOT NULL,
fk_Funcionario_Usuario_id INTEGER,
fk_Folha_de_Pagamento_id INTEGER
);
--DROP TABLE Holerite

CREATE TABLE Cargo_func (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
dta_de DATE NOT NULL,
dta_ate DATE,
fk_Funcionario_Usuario_id INTEGER,
fk_Cargo_id INTEGER
);
--DROP TABLE Cargo_func

CREATE TABLE Estab_func (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
data_ent DATE NOT NULL,
data_sai DATE,
fk_Estabelecimento_id INTEGER,
fk_Funcionario_Usuario_id INTEGER
);
--DROP TABLE Estab_func

CREATE TABLE Modulo (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
descr VARCHAR (30) NOT NULL
);
--DROP TABLE Modulo

CREATE TABLE Perfil_modulo (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
fk_Perfil_id INTEGER,
fk_Modulo_id INTEGER
);
--DROP TABLE Perfil_modulo

CREATE TABLE Operacoes_desc (
id INTEGER IDENTITY(1,1) PRIMARY KEY NOT NULL,
descr VARCHAR (30) NOT NULL
);
--DROP TABLE Operacoes_desc

CREATE TABLE Folha_de_Pagamento (
id INTEGER IDENTITY(1,1) PRIMARY KEY,
dta_base DATE NOT NULL,
valor_total DECIMAL (9,2) NOT NULL
);
--DROP TABLE Folha_de_Pagamento

ALTER TABLE Funcionario_Usuario ADD CONSTRAINT FK_Funcionario_Usuario_2
FOREIGN KEY (fk_Perfil_id)
REFERENCES Perfil (id)
ON DELETE CASCADE;

ALTER TABLE Operacao_funcionario ADD CONSTRAINT FK_Operacao_funcionario_2
FOREIGN KEY (fk_Funcionario_Usuario_id)
REFERENCES Funcionario_Usuario (id)
ON DELETE CASCADE;

ALTER TABLE Operacao_funcionario ADD CONSTRAINT FK_Operacao_funcionario_3
FOREIGN KEY (fk_Operacoes_id)
REFERENCES Operacoes (id)
ON DELETE CASCADE;

ALTER TABLE Operacoes ADD CONSTRAINT FK_Operacoes_2
FOREIGN KEY (fk_Operacoes_desc_id)
REFERENCES Operacoes_desc (id)
ON DELETE CASCADE;

ALTER TABLE Holerite ADD CONSTRAINT FK_Holerite_2
FOREIGN KEY (fk_Funcionario_Usuario_id)
REFERENCES Funcionario_Usuario (id)
ON DELETE CASCADE;

ALTER TABLE Holerite ADD CONSTRAINT FK_Holerite_3
FOREIGN KEY (fk_Folha_de_Pagamento_id)
REFERENCES Folha_de_Pagamento (id)
ON DELETE CASCADE;

ALTER TABLE Cargo_func ADD CONSTRAINT FK_Cargo_func_2
FOREIGN KEY (fk_Funcionario_Usuario_id)
REFERENCES Funcionario_Usuario (id)
ON DELETE CASCADE;

ALTER TABLE Cargo_func ADD CONSTRAINT FK_Cargo_func_3
FOREIGN KEY (fk_Cargo_id)
REFERENCES Cargo (id)
ON DELETE CASCADE;

ALTER TABLE Estab_func ADD CONSTRAINT FK_Estab_func_2
FOREIGN KEY (fk_Estabelecimento_id)
REFERENCES Estabelecimento (id)
ON DELETE CASCADE;

ALTER TABLE Estab_func ADD CONSTRAINT FK_Estab_func_3
FOREIGN KEY (fk_Funcionario_Usuario_id)
REFERENCES Funcionario_Usuario (id)
ON DELETE CASCADE;

ALTER TABLE Perfil_modulo ADD CONSTRAINT FK_Perfil_modulo_2
FOREIGN KEY (fk_Perfil_id)
REFERENCES Perfil (id)
ON DELETE CASCADE;

ALTER TABLE Perfil_modulo ADD CONSTRAINT FK_Perfil_modulo_3
FOREIGN KEY (fk_Modulo_id)
REFERENCES Modulo (id)
ON DELETE CASCADE;

ALTER TABLE Funcionario_Usuario ALTER COLUMN senha VARCHAR(100);
