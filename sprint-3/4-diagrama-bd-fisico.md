## Diagrama Físico

CREATE DATABASE syspayment;

USE syspayment;

CREATE TABLE Funcionario_Usuario (
dta_admissao DATE,
hora_inicio TIME,
hora_final TIME,
id INTEGER PRIMARY KEY,
sexo CHAR,
nome VARCHAR,
cpf VARCHAR,
tel VARCHAR,
email VARCHAR,
qnt_dependentes INTEGER,
dta_nasc DATE,
usuario VARCHAR,
senha VARCHAR,
ult_acesso DATE,
fk_Perfil_id INTEGER,
cep VARCHAR,
cidade VARCHAR,
estado VARCHAR,
pais VARCHAR,
rua VARCHAR,
bairro VARCHAR,
numero INTEGER,
complemento VARCHAR
);

CREATE TABLE Perfil (
id INTEGER PRIMARY KEY,
descr VARCHAR
);

CREATE TABLE Operacao_funcionario (
id INTEGER PRIMARY KEY,
dta_de DATE,
dta_ate DATE,
fk_Funcionario_Usuario_id INTEGER,
fk_Operacoes_id INTEGER
);

CREATE TABLE Operacoes (
id INTEGER PRIMARY KEY,
valor DECIMAL,
operacao CHAR,
percentual DECIMAL,
fk_Operacoes_desc_id INTEGER,
tipo_salario CHAR,
bloqueia_login CHAR
);

CREATE TABLE Cargo (
id INTEGER PRIMARY KEY,
descr VARCHAR,
cbo VARCHAR,
Periculosidade CHAR
);

CREATE TABLE Estabelecimento (
id INTEGER PRIMARY KEY,
cnpj VARCHAR,
nome VARCHAR,
filial VARCHAR
);

CREATE TABLE Holerite (
id INTEGER PRIMARY KEY,
dta_base DATE,
salario_base DECIMAL,
total_vencimento DECIMAL,
total_desconto DECIMAL,
sal_contr_inss DECIMAL,
base_calc_fgts DECIMAL,
base_calc_irf DECIMAL,
faixa_irf DECIMAL,
fk_Funcionario_Usuario_id INTEGER,
fk_Folha_de_Pagamento_id INTEGER
);

CREATE TABLE Cargo_func (
id INTEGER PRIMARY KEY,
dta_de DATE,
dta_ate DATE,
fk_Funcionario_Usuario_id INTEGER,
fk_Cargo_id INTEGER
);

CREATE TABLE Estab_func (
id INTEGER PRIMARY KEY,
data_ent DATE,
data_sai DATE,
fk_Estabelecimento_id INTEGER,
fk_Funcionario_Usuario_id INTEGER
);

CREATE TABLE Modulo (
id INTEGER PRIMARY KEY,
descr VARCHAR
);

CREATE TABLE Perfil_modulo (
id INTEGER PRIMARY KEY,
fk_Perfil_id INTEGER,
fk_Modulo_id INTEGER
);

CREATE TABLE Operacoes_desc (
id INTEGER PRIMARY KEY,
descr VARCHAR
);

CREATE TABLE Folha_de_Pagamento (
id INTEGER PRIMARY KEY,
dta_base DATE,
valor_total DECIMAL
);

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
