# Danilo Evangelista

### Eu entrego o sistema inteiro — e com o número que prova que ele funciona.

Back-end em **Python/FastAPI**, interface em **React/TypeScript**, banco modelado, suíte de
testes, Docker e CI. Não paro no protótipo: cada projeto aqui sobe com um comando, tem
teste automatizado e traz a medição do que ele faz — inclusive quando a medição contraria
o que eu esperava.

**235 testes automatizados** · **CI verde em 5 repositórios** · **tudo com `docker compose up`**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-conversar-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/danilogep)
[![Email](https://img.shields.io/badge/Email-danilo.gep@gmail.com-c14438?style=flat-square&logo=gmail&logoColor=white)](mailto:danilo.gep@gmail.com)

---

## Em destaque

### XiloScan — identificação de madeira por foto

<a href="https://github.com/danilogep/XiloScan">
  <img src="https://raw.githubusercontent.com/danilogep/XiloScan/main/docs/img/01_landing.png" width="210" align="right" alt="Tela inicial do XiloScan no celular">
</a>

Fotografe o corte de uma peça de madeira e o sistema diz de que espécie ela é.
Reconhecimento visual por *embedding* **ArcFace** sobre EfficientNet-B4, busca vetorial
**FAISS** no catálogo de **271 espécies** do Laboratório de Produtos Florestais, e um filtro
por caracteres anatômicos que reordena o ranking com o que o perito vê na lupa.

- Dataset construído do zero: scraper próprio, **893 imagens**, proveniência por campo
- API FastAPI + PyTorch · PWA em React/TS com captura guiada · Docker · **144 testes**
- Devolve `top1_ambiguo` quando a diferença para o segundo colocado é pequena — a interface
  então **exige** comparação visual antes de concluir

`PyTorch` `FAISS` `FastAPI` `React` `TypeScript` `Docker`

**[→ Ver o projeto](https://github.com/danilogep/XiloScan)**

<br clear="right">

---

### Otimização de banco medida, não afirmada

<a href="https://github.com/danilogep/Ecommerce-SQL-Database-Specialist">
  <img src="https://raw.githubusercontent.com/danilogep/Ecommerce-SQL-Database-Specialist/main/img/diagrama_final.png" width="49%" align="right" alt="Diagrama EER do e-commerce">
</a>

Modelagem completa de e-commerce em MySQL com **100 mil pedidos** de massa, e um benchmark
que compara `EXPLAIN` e tempo antes e depois de cada índice.

**Dois dos quatro índices não melhoraram nada — e o relatório diz isso.** Um era redundante:
o InnoDB já indexava a chave estrangeira. O outro funcionava, mas o `SELECT *` obrigava a
voltar à tabela, e o ganho sumia. A mesma coluna com `COUNT(*)` ficou **8× mais rápida**,
porque aí a resposta cabe no índice.

- Rodado em dois ambientes diferentes: os tempos mudam, os planos de execução não
- Subir a sequência do zero com volume real revelou **dois scripts quebrados** que passavam
  com 3 linhas de teste — os dois corrigidos

`MySQL 8` `InnoDB` `índices B-Tree` `Docker Compose` `Python`

**[→ Ver o benchmark](https://github.com/danilogep/Ecommerce-SQL-Database-Specialist/blob/main/docs/benchmark.md)**

<br clear="right">

---

### ViaturaAPI — gestão de frota, do banco à tela

<a href="https://github.com/danilogep/Viatura-API">
  <img src="https://raw.githubusercontent.com/danilogep/viatura-frontend/main/img/02_frota.png" width="49%" align="right" alt="Tabela da frota no painel">
</a>

Sistema completo de frota: **PostgreSQL + FastAPI + React 19**, os três subindo com
`docker compose up`. **35 testes, 95% de cobertura**, rodando em SQLite na memória — quem
clona não precisa subir banco para testar.

A regra central tem arquivo de teste próprio: **veículo baixado não volta a ser alocado**.
Se voltasse, reapareceria no efetivo de uma unidade e pesaria de novo na previsão
orçamentária — que é justamente o número que a baixa deveria reduzir.

- A previsão de custo é agregada em SQL, não somada no cliente: a versão anterior somava a
  primeira página da listagem e subnotificava a partir de 100 veículos
- [Interface em React/TypeScript](https://github.com/danilogep/viatura-frontend), servida
  por nginx, com busca instantânea sobre a frota

`FastAPI` `SQLAlchemy 2.0 async` `PostgreSQL` `React 19` `Docker`

**[→ Ver a API](https://github.com/danilogep/Viatura-API)** · **[→ Ver a interface](https://github.com/danilogep/viatura-frontend)**

<br clear="right">

---

## Mais projetos

| Projeto | O que resolve | A prova |
| :--- | :--- | :--- |
| **[Store API com TDD](https://github.com/danilogep/TDD-Project-API-Store)** | CRUD em FastAPI + MongoDB escrito teste primeiro, ciclo Red-Green-Refactor | **33 testes, 100% de cobertura.** `pytest` sobe um MongoDB descartável em container — um comando, sem configurar nada |
| **[ETL com IA generativa](https://github.com/danilogep/etl-sinistros-ia-generativa)** | Pipeline assíncrono que cruza dados abertos de sinistros e gera alertas por LLM | **US$ 0,022 por mil registros**, medido. Retry que distingue falha transitória de permanente, e modo offline de custo zero |
| **[Dashboard de sinistros](https://danilogep.github.io/dashboard-sinistros-transito-powerbi/)** | Power BI sobre 59 mil ocorrências de trânsito | A madrugada tem **2,4× mais letalidade** que o pleno dia com 1/8 do volume. [Navegável no ar](https://danilogep.github.io/dashboard-sinistros-transito-powerbi/) |
| **[Oficina mecânica (SQL)](https://github.com/danilogep/Oficina-SQL-Database-Specialist)** | Modelagem que congela o preço praticado no momento da venda | Reajustar a tabela de preços não reescreve o histórico financeiro de nenhuma OS já fechada |
| **[API bancária](https://github.com/danilogep/API-bancaria)** | API RESTful assíncrona com autenticação JWT | Integridade de transação e hash de senha |

---

## Como eu trabalho

**Publico o resultado, mesmo quando ele contraria a tese.** O benchmark de índices acima
mostra dois casos sem ganho nenhum. Era mais fácil apagar as duas linhas e mostrar só os
8×. O relatório inteiro vale mais com elas.

**Teste que precisa de banco instalado não é rodado por ninguém.** Em todos os projetos,
`pytest` funciona em um clone novo: ou contra SQLite em memória, ou subindo o banco em
container descartável. É o que mantém a suíte viva depois que o entusiasmo passa.

**Número sem método é opinião.** Onde não há medição, está escrito `[MEDIR]` em vez de uma
estimativa simpática — como na tabela de desempenho do XiloScan, que espera um treino.

---

## Stack

**Back-end** Python · FastAPI · SQLAlchemy 2.0 assíncrono · Pydantic v2 · Alembic
**Dados** PostgreSQL · MySQL · MongoDB · Power BI · pandas
**ML / Visão** PyTorch · timm · FAISS · OpenCV
**Front-end** TypeScript · React 19 · Vite · Chakra UI
**Infra** Docker · Docker Compose · GitHub Actions · nginx · Railway
**Qualidade** pytest · pytest-asyncio · testcontainers · ruff · pre-commit

---

## Formação e contexto

**Ciência da Computação** — Gran Faculdade (em curso) · **Engenharia Mecânica** — UFPB

Venho da engenharia e de anos de operação de campo em serviço público, onde processo mal
desenhado custa tempo de gente e, às vezes, mais que isso. É de lá que vem a obsessão por
sistema que aguenta condição real: foto tirada com luz ruim, planilha com campo vazio,
banco que cresceu dez vezes desde o dia do teste.

Certificações: SQL Database Specialist · Python Back-end Developer · Ciência de Dados com
Python *(DIO)*

---

<div align="center">

### Trabalho por projeto

Escopo fechado, prazo combinado, remoto. O que eu pego:

**API e back-end** em Python/FastAPI &nbsp;·&nbsp; **Modelagem e otimização de banco** em
MySQL e PostgreSQL &nbsp;·&nbsp; **Automação e pipelines de dados** &nbsp;·&nbsp;
**Dashboards** em Power BI

Me descreva o problema em duas linhas. Respondo com escopo, prazo e orçamento —
e, se não for trabalho para mim, eu digo.

[![LinkedIn](https://img.shields.io/badge/Conversar_no_LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/danilogep)
[![Email](https://img.shields.io/badge/danilo.gep@gmail.com-c14438?style=for-the-badge&logo=gmail&logoColor=white)](mailto:danilo.gep@gmail.com)

</div>
