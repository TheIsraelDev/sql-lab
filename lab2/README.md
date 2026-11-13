# SQL Lab 2 · MangáVerso

Continuação do SQL Lab. Aqui você **monta bancos de dados inteiros, do zero**, seguindo uma trilha de
44 missões em 7 fases, no tema de uma loja de mangás, HQs e webtoons. Enquanto você cria as tabelas,
o **diagrama (DER e MER) se desenha sozinho** ao lado do editor. Tudo roda no navegador, sem instalar nada.

**Acesse:** https://theisraeldev.github.io/sql-lab/lab2/

> Autoria: Professor Arquiteto de Software Full Stack Israel Pinheiro Lemos

---

## Como usar

1. Abra o link acima. Não precisa de login, instalação nem MySQL.
2. Leia a **missão 1** no painel da direita (e na faixa acima do editor).
3. Escreva o comando no editor e aperte **Ctrl + Enter** para executar a instrução onde o cursor está.
   **Ctrl + Shift + Enter** executa tudo o que está escrito.
4. Veja o resultado na grade e o desenho nascer ao lado. Quando a missão estiver certa, ela ganha um ✓ verde.
5. Siga para a missão seguinte. As 44 missões vão do `CREATE DATABASE` até um projeto seu.

Use a **apostila em PDF** ("Apostila SQL Lab 2 - MangaVerso.pdf", nesta pasta) como guia: ela tem um passo para cada
missão, na mesma ordem, com a explicação, o comando e o resultado esperado.

## A trilha de missões

| Fase | O que você faz | O que aprende |
|---|---|---|
| 1. Abrindo a loja | Cria o banco `mangaverso` e as tabelas `editoras`, `series` e `volumes` | `ENUM`, `DEFAULT`, `UNIQUE`, `CHECK`, chave estrangeira com `ON DELETE` |
| 2. Enchendo as prateleiras | Cadastra editoras, séries e volumes | `INSERT` de várias linhas, `NULL`, datas |
| 3. Consultando o catálogo | Faz perguntas ao banco | `LIKE`, `BETWEEN`, `LEFT JOIN`, `CASE`, `HAVING`, subconsulta |
| 4. Clientes e pedidos | Cria `clientes`, `pedidos` e `itens_pedido` | relação N:N, chave primária composta |
| 5. Mudando com segurança | Altera e apaga dados | `UPDATE`, Modo seguro, `ALTER TABLE`, `ROLLBACK`, `CASCADE`, `SET NULL` |
| 6. Relatórios guardados | Guarda consultas e junta listas | `VIEW`, `UNION` |
| 7. Desafio final | Monta o banco `clube_leitores` sozinho | tudo junto |

## O painel de missões

Cada missão tem quatro botões:

- **Conferir**: testa de novo o seu banco e diz o que ainda falta.
- **Dica**: uma pista, sem entregar a resposta.
- **Ver resposta**: o comando pronto, para comparar com o seu.
- A conferência também é **automática** a cada comando executado.

No topo do painel, **Montar o banco até aqui** apaga o que você tem e refaz o banco com as respostas das missões
anteriores à atual. Serve para quem pulou uma etapa e quer continuar sem travar.

## O diagrama ao lado do editor

- **DER**: as tabelas como ficam no banco, com colunas, tipos, chaves primárias (bolinha dourada) e estrangeiras (losango rosa).
- **MER**: o desenho conceitual, com entidades, relacionamentos (1 para N) e a ligação N para N como losango.
- O botão de download salva o diagrama como imagem **SVG**.
- A aba **Diagrama** (barra de cima) abre uma versão grande, em que você pode arrastar as tabelas.
- Em telas estreitas o painel lateral fica oculto; use a aba **Diagrama**.

## Seu banco e seu progresso

- O banco que você monta e o seu progresso ficam **guardados no seu navegador**; ao voltar, você continua de onde parou.
- **Salvar .sql** baixa o banco como arquivo e **Abrir .sql** carrega de volta (em uma nova aba do editor).
- **Recomeçar** apaga todos os bancos e volta a trilha ao início.
- **Modo seguro** (interruptor da barra): bloqueia `UPDATE` e `DELETE` sem `WHERE` em coluna-chave, como no MySQL Workbench (erro 1175).

## Comandos que o simulador entende

`CREATE DATABASE`, `USE`, `CREATE TABLE` (com `PRIMARY KEY`, `FOREIGN KEY`, `ON DELETE CASCADE/SET NULL/RESTRICT`,
`UNIQUE`, `CHECK`, `DEFAULT`, `ENUM`, `AUTO_INCREMENT`), `ALTER TABLE`, `DROP`, `INSERT`, `UPDATE`, `DELETE`,
`SELECT` com `JOIN`, `LEFT JOIN`, `GROUP BY`, `HAVING`, `ORDER BY`, `LIMIT`, `CASE`, subconsultas, `UNION`,
`CREATE VIEW`, `START TRANSACTION`, `COMMIT`, `ROLLBACK` e várias funções de texto, número e data.

**Limites:** não há triggers, procedures, `UPDATE`/`DELETE` com `JOIN`, `WINDOW` (`OVER`) nem `WITH` (CTE).
É um simulador para aprendizado, não um servidor de banco de dados.

## Se aparecer um erro

Leia a mensagem inteira: ela diz o que o banco não entendeu. Os casos mais comuns:

| Erro | Significa | O que fazer |
|---|---|---|
| 1062 Duplicate entry | valor repetido em coluna única | troque o valor |
| 1452 Cannot add or update a child row | a chave estrangeira aponta para algo que não existe | cadastre primeiro a tabela "pai" |
| 1451 Cannot delete a parent row | ainda existem registros ligados | apague os filhos antes |
| 1175 Safe update mode | `UPDATE` ou `DELETE` sem `WHERE` na chave | acrescente `WHERE id = ...` |
| 1064 Syntax error | erro de escrita | releia vírgulas, parênteses e aspas |

```
lab2/
├── index.html                           o Lab 2 completo (um único arquivo)
├── README.md                            este guia
└── Apostila SQL Lab 2 - MangaVerso.pdf  o passo a passo em PDF
```
