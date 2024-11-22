CREATE DATABASE Academia;
USE Academia;

CREATE TABLE Alunos (
    id_aluno INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    data_nascimento DATE NOT NULL,
    genero VARCHAR(20),
    telefone VARCHAR(15),
    email VARCHAR(100) UNIQUE,
    data_cadastro DATE NOT NULL
);

CREATE TABLE Professores (
    id_professor INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    especialidade VARCHAR(50),
    telefone VARCHAR(15),
    email VARCHAR(100) UNIQUE
);

CREATE TABLE Planos (
    id_plano INT AUTO_INCREMENT PRIMARY KEY,
    tipo_plano VARCHAR(50) NOT NULL,
    descricao TEXT,
    preco DECIMAL(10, 2) NOT NULL,
    duracao_meses INT NOT NULL
);

CREATE TABLE Treinos (
    id_treino INT AUTO_INCREMENT PRIMARY KEY,
    id_aluno INT NOT NULL,
    descricao TEXT NOT NULL,
    data_inicio DATE NOT NULL,
    data_fim DATE,
    FOREIGN KEY (id_aluno) REFERENCES Alunos(id_aluno)
);

CREATE TABLE Aulas (
    id_aula INT AUTO_INCREMENT PRIMARY KEY,
    tipo VARCHAR(50) NOT NULL,
    sala VARCHAR(50),
    id_professor INT NOT NULL,
    horario TIME NOT NULL,
    capacidade INT NOT NULL,
    FOREIGN KEY (id_professor) REFERENCES Professores(id_professor)
);

CREATE TABLE Pagamentos (
    id_pagamento INT AUTO_INCREMENT PRIMARY KEY,
    id_aluno INT NOT NULL,
    id_plano INT NOT NULL,
    data_pagamento DATE NOT NULL,
    valor_pago DECIMAL(10, 2) NOT NULL,
    forma_pagamento VARCHAR(50),
    FOREIGN KEY (id_aluno) REFERENCES Alunos(id_aluno),
    FOREIGN KEY (id_plano) REFERENCES Planos(id_plano)
);
