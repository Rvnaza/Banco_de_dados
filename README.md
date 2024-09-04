# Banco_de_dados

CREATE DATABASE estacionamento;
USE estacionamento;
-- Apagar coluna específica --


ALTER TABLE ticket
DROP COLUMN observacao_ticket;

ALTER TABLE estacionamento
RENAME TO Parking;

ALTER TABLE setor
MODIFY descricao_setor VARCHAR(100);



DROP DATABASE escola; -- apagar o banco de dados
DROP TABLE sala; -- apaga a tabela

CREATE TABLE estacionamento(
id_estacionamento INT NOT NULL AUTO_INCREMENT,
nome_estacionamento VARCHAR (45) NOT NULL,
cnpj_estacionamento BIGINT NOT NULL,
PRIMARY KEY (id_estacionamento)
);

CREATE TABLE setor(
id_setor INT NOT NULL AUTO_INCREMENT,
nome_setor VARCHAR (45) NOT NULL,
descricao_setor VARCHAR (45),
PRIMARY KEY (id_setor)
);

CREATE TABLE vaga(
id_vaga INT NOT NULL AUTO_INCREMENT,
numero_vagas INT NOT NULL,
PRIMARY KEY (id_vaga)
);

CREATE TABLE ticket(
id_ticket INT NOT NULL AUTO_INCREMENT,
codigo_barra_ticket INT NOT NULL,
observacao_ticket TEXT NOT NULL,
PRIMARY KEY (id_ticket)
);

ALTER TABLE estacionamento
ADD COLUMN ticket_id INT,
ADD FOREIGN KEY (ticket_id)
REFERENCES ticket (id_ticket);

ALTER TABLE setor
ADD COLUMN estacionamento_id INT,
ADD FOREIGN KEY (estacionamento_id)
REFERENCES estacionamento (id_estacionamento);

ALTER TABLE vaga
ADD COLUMN setor_id INT,
ADD FOREIGN KEY (setor_id)
REFERENCES setor (id_setor);
