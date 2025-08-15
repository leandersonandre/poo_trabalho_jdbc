# poo_trabalho_jdbc

## Equipe

| Equipe   | Email    |
|----------|----------|
| Aluno A  | Email A  |
| Aluno B  | Email B  |
| Aluno C  | Email C  |

## Configurações

| Item           | Valor     |
|----------------|-----------|
| Banco de Dados | MySQL     |
| Schema         | meu_banco |

## Diagrama de classe da UML

![Diagrama de classe](/diagrama_de_classe.png)

## Diagrama MER


![MER](/mer.png)

## Instruções SQL

Criação do schema e tabelas.
```SQL
-- Criação do schema
CREATE SCHEMA IF NOT EXISTS meu_banco_de_dados;
USE meu_banco_de_dados;

-- Tabela USUARIO
CREATE TABLE IF NOT EXISTS USUARIO (
    id_usuario INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL
);

-- Tabela LIVRO
CREATE TABLE IF NOT EXISTS LIVRO (
    id_livro INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL
);

-- Tabela EMPRESTIMO
CREATE TABLE IF NOT EXISTS EMPRESTIMO (
    id_emprestimo INT AUTO_INCREMENT PRIMARY KEY,
    id_usuario INT NOT NULL,
    id_livro INT NOT NULL,
    data_emprestimo DATETIME NOT NULL,
    data_previsao_devolucao DATETIME NOT NULL,
    data_efetiva_devolucao DATETIME,
    FOREIGN KEY (id_usuario) REFERENCES USUARIO(id_usuario),
    FOREIGN KEY (id_livro) REFERENCES LIVRO(id_livro)
);

```

Inserção de registros.
```SQL
-- Inserção de usuários
INSERT INTO USUARIO (nome, email) VALUES 
('Ana Souza', 'ana.souza@email.com'),
('Bruno Lima', 'bruno.lima@email.com'),
('Carla Mendes', 'carla.mendes@email.com');

-- Inserção de livros
INSERT INTO LIVRO (titulo) VALUES 
('Dom Casmurro'),
('1984'),
('O Senhor dos Anéis');

-- Inserção de empréstimos
INSERT INTO EMPRESTIMO (
    id_usuario, id_livro, data_emprestimo, data_previsao_devolucao, data_efetiva_devolucao
) VALUES 
(1, 1, '2025-08-01 10:00:00', '2025-08-15 23:59:59', '2025-08-14 16:30:00'),
(2, 2, '2025-08-05 14:20:00', '2025-08-19 23:59:59', NULL),
(3, 3, '2025-08-10 09:00:00', '2025-08-24 23:59:59', NULL);
```
