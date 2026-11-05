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

## Para o professor: publicar no GitHub Pages

Faça uma vez. Depois disso, o link funciona para qualquer aluno.

1. No GitHub, acesse https://github.com/new
2. Em **Repository name**, escreva `sql-lab`. Marque **Public** e clique em **Create repository**.
3. Na página do repositório, clique em **uploading an existing file**.
4. Arraste para a página os arquivos `index.html` e `README.md` desta pasta.
   O arquivo principal **precisa se chamar `index.html`**, em minúsculas.
5. Clique em **Commit changes**.
6. Abra **Settings → Pages**.
7. Em **Build and deployment → Source**, escolha **Deploy from a branch**.
   Em **Branch**, escolha **main** e a pasta **/ (root)**. Clique em **Save**.
8. Aguarde de 1 a 2 minutos e atualize a página de configurações.
   Aparece a mensagem **Your site is live at ...** com o endereço final.

O endereço será:

```
https://theisraeldev.github.io/sql-lab/
```

Se aparecer erro 404, confira: repositório **Public**, arquivo chamado `index.html`,
Pages ativado na branch **main** e o endereço escrito exatamente como o do passo 8.

### Como atualizar depois

1. Abra o repositório e clique em `index.html`.
2. Clique no lápis (**Edit**) ou, na página principal, em **Add file → Upload files**
   e envie o novo arquivo com o mesmo nome.
3. Clique em **Commit changes**. Em poucos minutos o link já mostra a versão nova.

### Dica para a sala

Coloque o link ou um QR code no slide da aula. Cada aluno tem o próprio banco no
navegador, então o que um altera não aparece para os outros.

---

## Estrutura do projeto

```
sql-lab/
├── index.html   a aplicação completa (HTML, CSS e JavaScript em um único arquivo)
└── README.md    este guia
```

Não há dependências para instalar. A única coisa carregada da internet é a fonte do
texto; sem ela, o navegador usa uma fonte padrão.
