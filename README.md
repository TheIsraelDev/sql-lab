# SQL Lab Workbench

Simulador de banco de dados para aprender SQL direto no navegador, sem instalar nada.
Os alunos escrevem consultas, veem os resultados em uma grade, exploram as tabelas e o
diagrama de relacionamento e resolvem desafios com conferência automática.

**Acesse:** https://theisraeldev.github.io/sql-lab/

> Autoria: Professor Arquiteto de Software Full Stack Israel Pinheiro Lemos

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

Pode. O editor é livre:

```sql
CREATE DATABASE biblioteca;
USE biblioteca;
CREATE TABLE livros (
  id INT NOT NULL AUTO_INCREMENT,
  titulo VARCHAR(60) NOT NULL,
  ano INT,
  PRIMARY KEY (id)
);
INSERT INTO livros (titulo, ano) VALUES ('Dom Casmurro', 1899);
SELECT * FROM livros;
```

Os dados existem só enquanto a página está aberta. Ao recarregar, volta o banco original.
O botão **Restaurar** também devolve o `loja_games` ao estado inicial.

Cada aluno tem o próprio banco no navegador: o que você altera não aparece para os colegas.

---

## O que o simulador entende

- Consultas: `SELECT`, `WHERE`, `AND`, `OR`, `IN`, `BETWEEN`, `LIKE`, `ORDER BY`, `LIMIT`,
  `DISTINCT`, `GROUP BY`, `HAVING`, `JOIN` (inner, left, right), subconsultas e funções
  como `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`, `ROUND`, `CONCAT`.
- Dados: `INSERT`, `UPDATE`, `DELETE`.
- Estrutura: `CREATE`/`DROP DATABASE`, `CREATE`/`DROP TABLE`, `ALTER TABLE`,
  `PRIMARY KEY`, `AUTO_INCREMENT`, `FOREIGN KEY`.
- Informação: `SHOW DATABASES`, `SHOW TABLES`, `SHOW CREATE TABLE`, `DESCRIBE`, `USE`.
- Regras do banco: chave duplicada, chave estrangeira, campo obrigatório e tamanho
  máximo de texto geram erros iguais aos de um MySQL real, explicados em português.

**Limites:** não há `UNION`, triggers, procedures nem views. É um simulador para
aprendizado, não um servidor de banco de dados.

---

## Sobre o projeto

```
sql-lab/
├── index.html   a aplicação completa (HTML, CSS e JavaScript em um único arquivo)
└── README.md    este guia
```

Não há nada para instalar. A página roda inteira no navegador e funciona em computador,
tablet e celular.
