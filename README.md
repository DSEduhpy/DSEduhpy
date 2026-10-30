<h1 align="center">Eduardo de Castro Vieira</h1>

<p align="center">
  <strong>Engenheiro de Dados &amp; Machine Learning</strong><br />
  Engenharia de Software · Cibersegurança <em>(em formação)</em>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/eduardo-de-castro-vieira-5b061027b/"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-Eduardo%20de%20Castro%20Vieira-1F6FEB?style=flat-square" /></a>
  <a href="mailto:eduardodecastroep@gmail.com"><img alt="Contato por e-mail" src="https://img.shields.io/badge/Contato-E--mail-1F6FEB?style=flat-square" /></a>
  <img alt="Localização: Juiz de Fora, MG" src="https://img.shields.io/badge/Juiz%20de%20Fora%2C%20MG-6E7681?style=flat-square" />
</p>

---

## Sobre

Desenvolvo sistemas de dados e Machine Learning com rigor de engenharia de software: pipelines modulares, testes automatizados, APIs e rastreabilidade de experimentos.

Curso Tecnologia em Ciência de Dados e, em paralelo, aprofundo minha base em redes e segurança da informação. Meu objetivo é atuar profissionalmente com soluções orientadas a dados e software enquanto avanço minha especialização em Cibersegurança.

| Área | Situação | O que sustenta |
|---|---|---|
| **Dados e Machine Learning** | Prática em projetos | Credit Risk MLOps, biblioteca PNS, transcrição com Whisper |
| **Engenharia de software** | Prática em projetos | Study Agent, Credit Risk (144 testes) |
| **Segurança e redes** | Em formação | Cursos e segurança por design no Study Agent |

---

## Projetos em destaque

### Credit Risk MLOps

*Pipeline de Machine Learning ponta a ponta para risco de crédito, construído para simular um ambiente de produção.*

- Ingestão, validação, processamento e engenharia de atributos
- Benchmark entre Logistic Regression, XGBoost, LightGBM e CatBoost
- Otimização de threshold com métricas técnicas e financeiras
- Experimentos com MLflow, registry Champion/Challenger e pipeline versionado com DVC
- API REST com FastAPI e execução com Docker Compose
- Métricas compatíveis com Prometheus e 4 workflows de GitHub Actions (testes, lint, build Docker e treinamento)
- **144 testes automatizados** com Pytest, além de Ruff, Black e isort

<details>
<summary><strong>Detalhes técnicos e escopo</strong></summary>

<br />

- **Endpoints:** `/predict`, `/health`, `/ready` e `/version`.
- **Organização:** código em `src/` separado por responsabilidade (API, ingestão, validação, processamento, modelagem, avaliação, explicabilidade, monitoramento) e documentação em `docs/`.
- **Escopo:** o projeto simula um ambiente de produção. Deploy em nuvem, Terraform, Kubernetes, Evidently e dashboards completos de Grafana constam no roadmap como evolução futura e não estão implementados.

</details>

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-1F6FEB?style=flat-square" />
  <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-1F6FEB?style=flat-square" />
  <img alt="MLflow" src="https://img.shields.io/badge/MLflow-1F6FEB?style=flat-square" />
  <img alt="DVC" src="https://img.shields.io/badge/DVC-1F6FEB?style=flat-square" />
  <img alt="Docker" src="https://img.shields.io/badge/Docker-1F6FEB?style=flat-square" />
  <img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-1F6FEB?style=flat-square" />
</p>

**Repositório:** [DSEduhpy/credit-risk-mlops](https://github.com/DSEduhpy/credit-risk-mlops)

---

### Study Agent

*Plataforma de aprendizagem adaptativa com currículo em Markdown, focada em Cibersegurança e Ciência de Dados. Em desenvolvimento desde agosto de 2026.*

- Arquitetura em motores com responsabilidades separadas: currículo, grafo de conhecimento, pedagogia, adaptação, retenção, exercícios, meta diária e tutor
- Máquina de estados finita com 13 estados e transições validadas, que distingue memorização de domínio
- Grafo de conhecimento com pré-requisitos que rejeita ciclos
- Repetição espaçada e adaptação de dificuldade determinísticas e explicáveis, sem depender de provedor de IA
- Provedor de IA isolado atrás da interface `AIProvider`, com adaptador OpenAI opcional
- Extensão para VS Code em TypeScript, comunicando-se com o núcleo Python por JSON Lines via stdio
- **Segurança por design:** rejeição de path traversal e de caminhos absolutos ao carregar aulas, e credenciais mantidas apenas em `.env`, fora do Git

<details>
<summary><strong>Detalhes técnicos e escopo</strong></summary>

<br />

- **Funcionamento offline:** consultas ao currículo e ao grafo, retenção, adaptação e testes não chamam provedor externo. As explicações do tutor exigem um provedor de IA configurado.
- **Persistência:** SQLite com esquema idempotente, centralizado em um repositório de aprendizagem.
- **Escopo adiado:** integração com mensageiros, RAG, autenticação e execução controlada de laboratórios estão fora da versão atual.

</details>

<!-- Se o repositório do Study Agent for público, adicione abaixo:
**Repositório:** [DSEduhpy/NOME-DO-REPOSITORIO](https://github.com/DSEduhpy/NOME-DO-REPOSITORIO)
-->

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-1F6FEB?style=flat-square" />
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-1F6FEB?style=flat-square" />
  <img alt="SQLite" src="https://img.shields.io/badge/SQLite-1F6FEB?style=flat-square" />
  <img alt="Extensão para VS Code" src="https://img.shields.io/badge/Extens%C3%A3o%20VS%20Code-1F6FEB?style=flat-square" />
</p>

---

### Biblioteca de análise da PNS (UFJF)

*Biblioteca Python para análise da Pesquisa Nacional de Saúde (2013 e 2019), com foco em saúde da mulher. Desenvolvida como trabalho freelance para uma pesquisa acadêmica da UFJF.*

- Camada de abstração semântica: variáveis analíticas como `sexo` e `renda_per_capita` no lugar dos códigos físicos da pesquisa
- Primeira execução busca no BigQuery apenas as colunas necessárias, e as seguintes leem de um repositório SQLite local persistente, o que reduz custo de consulta
- Gravação com UPSERT e esquema evolutivo (novas colunas conforme a necessidade)
- Variáveis derivadas registráveis pelo usuário, com catálogo de metadados sincronizado
- Arquitetura em camadas (`ingestion`, `transform`, `dao`, `service`) e uma função pública de alto nível para notebooks Jupyter

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-1F6FEB?style=flat-square" />
  <img alt="Pandas" src="https://img.shields.io/badge/Pandas-1F6FEB?style=flat-square" />
  <img alt="BigQuery" src="https://img.shields.io/badge/BigQuery-1F6FEB?style=flat-square" />
  <img alt="SQLite" src="https://img.shields.io/badge/SQLite-1F6FEB?style=flat-square" />
</p>

**Repositório:** [DSEduhpy/pns_analysis_2013_2019](https://github.com/DSEduhpy/pns_analysis_2013_2019)

---

### Transcrição de entrevistas com Whisper

*Automação em Python para transcrever entrevistas de pesquisa acadêmica (gestores escolares e professores) com o modelo Whisper, da OpenAI.*

- Transcrição em lote com geração de transcrições brutas, seguida de revisão manual
- Estrutura de diretórios por etapa do fluxo (áudios, roteiros, transcrições brutas e revisadas, versão final)
- Logs de processamento para acompanhar o progresso da execução

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-1F6FEB?style=flat-square" />
  <img alt="OpenAI Whisper" src="https://img.shields.io/badge/OpenAI%20Whisper-1F6FEB?style=flat-square" />
</p>

**Repositório:** [DSEduhpy/audio-transcriber](https://github.com/DSEduhpy/audio-transcriber)

---

## Stack

<table>
  <tr>
    <td><strong>Linguagens</strong></td>
    <td>
      <img alt="Python" src="https://img.shields.io/badge/Python-1F6FEB?style=flat-square" />
      <img alt="SQL" src="https://img.shields.io/badge/SQL-1F6FEB?style=flat-square" />
      <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-1F6FEB?style=flat-square" />
    </td>
  </tr>
  <tr>
    <td><strong>Dados</strong></td>
    <td>
      <img alt="Pandas" src="https://img.shields.io/badge/Pandas-1F6FEB?style=flat-square" />
      <img alt="NumPy" src="https://img.shields.io/badge/NumPy-1F6FEB?style=flat-square" />
      <img alt="BigQuery" src="https://img.shields.io/badge/BigQuery-1F6FEB?style=flat-square" />
      <img alt="SQLite" src="https://img.shields.io/badge/SQLite-1F6FEB?style=flat-square" />
      <img alt="Jupyter" src="https://img.shields.io/badge/Jupyter-1F6FEB?style=flat-square" />
    </td>
  </tr>
  <tr>
    <td><strong>Machine Learning</strong></td>
    <td>
      <img alt="Scikit-Learn" src="https://img.shields.io/badge/Scikit--Learn-1F6FEB?style=flat-square" />
      <img alt="XGBoost" src="https://img.shields.io/badge/XGBoost-1F6FEB?style=flat-square" />
      <img alt="LightGBM" src="https://img.shields.io/badge/LightGBM-1F6FEB?style=flat-square" />
      <img alt="CatBoost" src="https://img.shields.io/badge/CatBoost-1F6FEB?style=flat-square" />
      <img alt="OpenAI Whisper" src="https://img.shields.io/badge/OpenAI%20Whisper-1F6FEB?style=flat-square" />
    </td>
  </tr>
  <tr>
    <td><strong>MLOps e APIs</strong></td>
    <td>
      <img alt="MLflow" src="https://img.shields.io/badge/MLflow-1F6FEB?style=flat-square" />
      <img alt="DVC" src="https://img.shields.io/badge/DVC-1F6FEB?style=flat-square" />
      <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-1F6FEB?style=flat-square" />
      <img alt="Pydantic" src="https://img.shields.io/badge/Pydantic-1F6FEB?style=flat-square" />
      <img alt="Docker" src="https://img.shields.io/badge/Docker-1F6FEB?style=flat-square" />
      <img alt="Prometheus" src="https://img.shields.io/badge/Prometheus-1F6FEB?style=flat-square" />
      <img alt="GitHub Actions" src="https://img.shields.io/badge/GitHub%20Actions-1F6FEB?style=flat-square" />
    </td>
  </tr>
  <tr>
    <td><strong>Qualidade e ferramentas</strong></td>
    <td>
      <img alt="Pytest" src="https://img.shields.io/badge/Pytest-1F6FEB?style=flat-square" />
      <img alt="Ruff" src="https://img.shields.io/badge/Ruff-1F6FEB?style=flat-square" />
      <img alt="Black" src="https://img.shields.io/badge/Black-1F6FEB?style=flat-square" />
      <img alt="isort" src="https://img.shields.io/badge/isort-1F6FEB?style=flat-square" />
      <img alt="Git" src="https://img.shields.io/badge/Git-1F6FEB?style=flat-square" />
      <img alt="GitHub" src="https://img.shields.io/badge/GitHub-1F6FEB?style=flat-square" />
      <img alt="VS Code" src="https://img.shields.io/badge/VS%20Code-1F6FEB?style=flat-square" />
    </td>
  </tr>
  <tr>
    <td><strong>Web (projeto de cliente)</strong></td>
    <td>
      <img alt="Node.js" src="https://img.shields.io/badge/Node.js-1F6FEB?style=flat-square" />
      <img alt="React" src="https://img.shields.io/badge/React-1F6FEB?style=flat-square" />
      <img alt="tRPC" src="https://img.shields.io/badge/tRPC-1F6FEB?style=flat-square" />
      <img alt="Drizzle ORM" src="https://img.shields.io/badge/Drizzle%20ORM-1F6FEB?style=flat-square" />
      <img alt="MySQL" src="https://img.shields.io/badge/MySQL-1F6FEB?style=flat-square" />
    </td>
  </tr>
  <tr>
    <td><strong>Práticas</strong></td>
    <td>ETL · Modelagem relacional · APIs REST · Testes automatizados · CI com GitHub Actions · Arquitetura modular · Programação orientada a objetos · Automação de processos</td>
  </tr>
</table>

---

## Segurança da informação e redes

> **Em formação.** Esta seção separa o que é estudo do que já foi demonstrado em projeto. Segurança ofensiva é explorada apenas em ambiente de estudo.

| Categoria | Conteúdo |
|---|---|
| <img alt="Em formação" src="https://img.shields.io/badge/Em%20forma%C3%A7%C3%A3o-6E7681?style=flat-square" /> | **Redes de Computadores** (Curso em Vídeo, em andamento) e **Pentest em RFID, NFC e Hardware Hacking** (Penegui, em andamento) |
| <img alt="Curso concluído" src="https://img.shields.io/badge/Curso%20conclu%C3%ADdo-6E7681?style=flat-square" /> | **Segurança da Informação, Módulo 00: Fundamentos** (Curso em Vídeo) |
| <img alt="Estudado" src="https://img.shields.io/badge/Estudado-6E7681?style=flat-square" /> | Conteúdo dos cursos: endereçamento IP, DHCP, sub-redes, roteadores, Wi-Fi e cabeamento UTP; Cisco Packet Tracer; Proxmark3, Flipper Zero, EMP Jammer, tags RFID/NFC e Mifare Classic |
| <img alt="Prática realizada" src="https://img.shields.io/badge/Pr%C3%A1tica%20realizada-6E7681?style=flat-square" /> | Simulação de topologias e protocolos no Cisco Packet Tracer, durante o curso de Redes |
| <img alt="Demonstrado em projeto" src="https://img.shields.io/badge/Demonstrado%20em%20projeto-1F6FEB?style=flat-square" /> | **Study Agent:** primeiros passos de segurança por design, com rejeição de path traversal e isolamento de credenciais |

---

## Formação e cursos

| Formação | Instituição | Período | Situação |
|---|---|---|---|
| Tecnologia em Ciência de Dados | UNINTER | out/2025 – abr/2028 | Cursando |
| Databricks Fundamentals (Academy Accreditation) | Databricks | — | Concluído |
| Segurança da Informação, Módulo 00: Fundamentos | Curso em Vídeo | — | Curso concluído |
| Redes de Computadores | Curso em Vídeo | set–out/2026 | Em andamento |
| Pentest em RFID, NFC e Hardware Hacking | Penegui | desde set/2026 | Em andamento |

---

## Trajetória recente

| Período | Projeto | Resumo |
|---|---|---|
| ago/2026 – atual | **Study Agent** | Plataforma de aprendizagem adaptativa (Python e TypeScript) |
| jun–ago/2026 | **Sistema de gestão operacional** | Plataforma web de produção, estoque e rotinas administrativas para uma empresa do setor alimentício, com React, TypeScript, Node.js e MySQL. Projeto de cliente, interrompido antes da implantação por decisão da cliente. Código fora deste portfólio |
| mar–jul/2026 | **Credit Risk MLOps** | Pipeline de ML de ponta a ponta |
| jan–fev/2026 | **Transcrição de entrevistas** | Automação com Whisper para pesquisa em educação bilíngue (freelance) |
| nov/2025 – jan/2026 | **Dados da PNS na UFJF** | ETL BigQuery para SQLite e camada semântica (freelance) |

---

## Contato

<p>
  <a href="https://www.linkedin.com/in/eduardo-de-castro-vieira-5b061027b/"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-1F6FEB?style=flat-square" /></a>
  <a href="mailto:eduardodecastroep@gmail.com"><img alt="E-mail" src="https://img.shields.io/badge/E--mail-1F6FEB?style=flat-square" /></a>
</p>
