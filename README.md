# Inteli-M2-Programacao-Aula2

## Código da aula:

CREATE TABLE alunos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  origem TEXT NOT NULL
);

CREATE TABLE cursos (
  id SERIAL PRIMARY KEY,
  curso TEXT NOT NULL,
  duracao_anos INT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  aluno_id INT REFERENCES alunos(id) ON DELETE CASCADE,
  curso_id INT REFERENCES cursos(id) ON DELETE CASCADE,
  data_matricula DATE DEFAULT CURRENT_DATE
);

INSERT INTO alunos (nome, origem)
VALUES ('Livia Oliveira', 'Espírito Santo'),
       ('Maria Arielly', 'Pernambuco'),
       ('Rafael Cabral', 'São José'),
       ('Vivian Peres', 'Rio Grande do Sul'),
       ('Messias Olivindo', 'Amazonas'),
       ('Paulo Vitor', 'São José'),
       ('Alessandra Sena', 'São Paulo'),
       ('Henrique Diniz', 'São Paulo'),
       ('Caue Taddeo', 'São Paulo'),
       ('Hugo Montan', 'São José');


INSERT INTO cursos (curso, duracao_anos)
VALUES ('Sistemas de Informação', 4),
       ('Engenharia de Software', 4),
       ('Ciência da Computação', 4),
       ('Engenharia da Computação', 4),
       ('Sistemas de Informação', 4),
       ('Engenharia de Software', 4),
       ('Sistemas de Informação', 4),
       ('Adm Tech', 4),
       ('Engenharia da Computação', 4),
       ('Adm Tech', 4);

INSERT INTO matriculas (aluno_id, curso_id)
VALUES (1, 1),
       (2, 2),
       (3, 3),
       (4, 4),
       (5, 5),
       (6, 6),
       (7, 7),
       (8, 8),
       (9, 9),
       (10, 10);


SELECT a.nome AS aluno, c.curso AS curso, m.data_matricula
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;
