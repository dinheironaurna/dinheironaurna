# Dinheiro na Urna 

> Bem público digital para **mapear e rastrear, em código aberto, como o dinheiro privado influencia a política brasileira.**  
> Este repositório conterá todo o fluxo de coleta, tratamento e análise de dados eleitorais, legais e publicitários. Para que qualquer pessoa possa auditar, reutilizar e expandir o trabalho. **100% software livre, 100% dados abertos.**  

---
## Perguntas que guiam este projeto

1. Quem doa quanto, para quem e quando? (candidatos municipais a presidenciais).
2. Quais empresas e famílias concentram as doações? (cruzar CPF/CNPJ com renda, patrimônio e grupos econômicos).
3. Que leis, emendas ou votações foram favorecidas por grandes doadores? (integrar votações da Câmara/Senado).
4. Quanto dinheiro extra‐oficial circula via publicidade política online? (capturar anúncios na Meta e Google).
5. Como tornar tudo auditável, replicável e reutilizável por ONGs, jornalistas e cidadãos?

---

## Ideias de Análises e Produtos

1. Ranking dos N maiores doadores, com setor econômico e evolução temporal.
2. Matriz Doação * Voto (calcular correlação entre valores recebidos e votos pró-setor [Ex: Agrotóxicos]).
3. Redes de influência (grafos [candidato<->doador<->empresa] com visualizações interativas).
4. Monitor de propaganda online (alerta semanal de anúncios políticos caros ou hipersegmentados).
5. Boletim "Dinheiro na Urna" (newsletter automática antes de cada votação relevante).

---

## Objetivos

1. **Coletar** e versionar todas as doações de campanhas do TSE desde 2002.  
2. **Cruzar** CPFs/CNPJs dos doadores com a base oficial da Receita Federal para identificar grupos econômicos e setores de atividade.  
3. **Relacionar** doações a votações na Câmara/Senado para medir correlações entre dinheiro e decisões legislativas.  
4. **Monitorar** gastos em anúncios políticos nas redes (Meta Ad Library, Google Ads).  
5. **Publicar** tudo como _data commons_, assegurando liberdade de compartilhamento.  
6. **Fomentar** jornalismo de dados, pesquisa acadêmica e mobilização cidadã com painéis, APIs e tutoriais.  

---

## Fontes de dados

| Fonte | Descrição | Frequência |
|-------|-----------|-----------|
| **TSE – DivulgaCandContas** | Arrecadação e gastos declarados por candidato, 2002-presente | anual/eleitoral |
| **Base CNPJ (Receita)** | Identificação de empresas e sócios | mensal |
| **APIs Câmara & Senado** | Votações, proposições, emendas | diária |
| **Fundo Partidário/Fundo Eleitoral** | Receitas públicas dos partidos | anual |
| **Meta & Google Ad Libraries** | Gastos com anúncios políticos online | diária |
| **Jurisprudência ADI 4650 (STF)** | Marco legal que baniu doação empresarial (2015) | estático |

---

## Planejamento de Arquitetura

* **Ingestão**: **Airflow** ou **Prefect** (Python). 
* **Transformação**: **dbt** (SQL).
* **Armazenamento**: arquivos **Parquet** em MinIO/S3 + **DuckDB** local ou **BigQuery** gratuito.  
* **API**: **FastAPI** + **GraphQL** para consultas públicas.  
* **Visualização**: **Metabase**, painéis exploráveis e *Jupyter Notebooks*.  
* **Reprodutibilidade**: pipelines versionados com **git** + **DVC**
---

## Licenciamento e princípios

| Camada | Licença | Rationale |
|--------|---------|-----------|
| **Código** | **MIT License** (free as in freedom) 
| **Dados** | **Open Database License 1.0 (ODbL)** 
| **Documentação** | **Creative Commons BY-SA 4.0**
> Nenhum componente proprietário será aceito: **somente software livre** (OSI ou FSF-approved).
