# SQL Lab Workbench

Simulador de banco de dados para aprender SQL direto no navegador, sem instalar nada.
Os alunos escrevem consultas, veem os resultados em uma grade, exploram as tabelas e o
diagrama de relacionamento e resolvem desafios com conferência automática.

**Acesse:** https://theisraeldev.github.io/sql-lab/

> Autoria: Professor Arquiteto de Software Full Stack Israel Pinheiro Lemos

**Já terminou o Lab 1? Continue no [SQL Lab 2 · MangáVerso](https://theisraeldev.github.io/sql-lab/lab2/)**: monte bancos inteiros, passo a passo, com diagramas MER e DER automáticos.

---

## Para o aluno

Basta clicar no link acima. Não precisa de login, instalação nem MySQL.

1. O banco **loja_games** já vem pronto, com as tabelas `plataformas` e `jogos`.
2. Escreva uma consulta no editor e aperte **Ctrl + Enter** para executar.
3. O resultado aparece na grade logo abaixo. Se houver erro, a mensagem explica o que corrigir.
4. Abra **Desafios** (botão no topo) para treinar com perguntas prontas.
5. Abra **Diagrama** para ver como as tabelas se ligam.

### Comandos para começar

```sql
SHOW TABLES;
DESCRIBE jogos;
SELECT * FROM jogos;
SELECT nome, preco FROM jogos WHERE genero = 'Aventura' ORDER BY preco DESC;
```

### Atalhos

| Atalho | O que faz |
|---|---|
| Ctrl + Enter | Executa a instrução onde o cursor está |
| Ctrl + Shift + Enter | Executa todas as instruções |
| Ctrl + / | Comenta ou descomenta linhas |
| Tab ou Enter | Aceita a sugestão do autocompletar |
| Clique duplo na tabela | Abre `SELECT * FROM tabela` |

### Posso criar o meu próprio banco?

Pode, e do jeito que quiser. O editor é livre e aceita qualquer estrutura de tabelas:

```sql
CREATE DATABASE escola;
USE escola;
CREATE TABLE alunos (
  id INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(50) NOT NULL,
  nascimento DATE,
  turno ENUM('manhã','tarde') DEFAULT 'manhã',
  nota DECIMAL(4,2) CHECK (nota BETWEEN 0 AND 10),
  criado_em DATETIME DEFAULT CURRENT_TIMESTAMP
);
CREATE TABLE matriculas (
  aluno_id INT,
  disciplina VARCHAR(30),
  PRIMARY KEY (aluno_id, disciplina),
  FOREIGN KEY (aluno_id) REFERENCES alunos(id) ON DELETE CASCADE
);
INSERT INTO alunos (nome, nascimento) VALUES ('Ana', '2010-05-01');
SELECT * FROM alunos;
```

Os dados existem só enquanto a página está aberta. Para guardar o seu banco, use o botão
**Salvar .sql** (baixa um arquivo com a estrutura e os dados) e, depois, **Abrir .sql** para
carregar o arquivo em uma nova aba e executar com Ctrl + Shift + Enter.
O botão **Restaurar** devolve o `loja_games` ao original e remove os bancos criados por você.

Cada aluno tem o próprio banco no navegador: o que você altera não aparece para os colegas.

---

## O que o simulador entende

- **Consultas:** `SELECT`, `WHERE`, `AND`, `OR`, `NOT`, `IN`, `BETWEEN`, `LIKE`, `REGEXP`,
  `EXISTS`, `ORDER BY`, `LIMIT`, `DISTINCT`, `GROUP BY`, `HAVING`, `JOIN` (inner, left, right,
  cross), subconsultas, `UNION` e `UNION ALL`, e funções como `COUNT`, `SUM`, `AVG`, `MIN`,
  `MAX`, `GROUP_CONCAT`, `ROUND`, `CONCAT`, `UPPER`, `LOWER`, `SUBSTRING`, `COALESCE`, `IF`,
  `NOW`, `CURDATE`, `YEAR`, `DATEDIFF`, `DATE_FORMAT` e outras.
- **Dados:** `INSERT` (inclusive `INSERT IGNORE` e `ON DUPLICATE KEY UPDATE`), `REPLACE`,
  `UPDATE` e `DELETE` (com `ORDER BY` e `LIMIT`).
- **Estrutura:** `CREATE`/`DROP DATABASE`, `CREATE`/`DROP TABLE` (também `LIKE` e `AS SELECT`),
  `ALTER TABLE` (várias alterações de uma vez: `ADD`, `DROP`, `MODIFY`, `CHANGE`, `RENAME`),
  `RENAME TABLE`, `TRUNCATE`, `CREATE INDEX`.
- **Tipos:** `INT` (e `TINYINT`, `SMALLINT`, `BIGINT`, `UNSIGNED`), `DECIMAL`, `FLOAT`, `DOUBLE`,
  `VARCHAR`, `CHAR`, `TEXT`, `ENUM`, `BOOLEAN`, `DATE`, `DATETIME`, `TIMESTAMP`, `TIME`, `YEAR`.
- **Regras:** `PRIMARY KEY` (simples ou composta), `FOREIGN KEY` com `ON DELETE`/`ON UPDATE`
  (`CASCADE`, `SET NULL`, `RESTRICT`), `AUTO_INCREMENT`, `NOT NULL`, `UNIQUE`, `DEFAULT`
  (inclusive `CURRENT_TIMESTAMP`), `CHECK`. Quando uma regra é violada, o erro é igual ao de um
  MySQL real (1062, 1451, 1452, 1364, 3819...), explicado em português.
- **Views:** `CREATE VIEW`, `CREATE OR REPLACE VIEW`, `DROP VIEW`, `SHOW CREATE VIEW`.
- **Transações:** `START TRANSACTION`, `COMMIT` e `ROLLBACK` (o `ROLLBACK` desfaz de verdade).
- **Modo seguro:** o interruptor na barra de ferramentas (ou `SET SQL_SAFE_UPDATES = 1;`) barra
  `UPDATE` e `DELETE` sem `WHERE` em coluna-chave, com o erro 1175.
- **Informação:** `SHOW DATABASES`, `SHOW TABLES`, `SHOW COLUMNS`, `SHOW INDEX`,
  `SHOW CREATE TABLE`, `DESCRIBE`, `USE`.
- **Variáveis:** `SET @x = 5; SELECT @x + 1;`.

**Limites:** não há triggers, procedures, `UPDATE`/`DELETE` com `JOIN`, `WINDOW` (`OVER`) nem
`WITH` (CTE). É um simulador para aprendizado, não um servidor de banco de dados.

---

## Sobre o projeto

```
sql-lab/
├── index.html   o Lab 1: a aplicação completa (HTML, CSS e JavaScript em um único arquivo)
├── README.md    este guia
└── lab2/        o Lab 2 (MangáVerso): página, guia e apostila em PDF
```

Não há nada para instalar. A página roda inteira no navegador e funciona em computador,
tablet e celular.
