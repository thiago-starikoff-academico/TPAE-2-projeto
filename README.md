# TPAE-2-projeto
# 📊 Infraestrutura da Informação na Paraíba 

> 🎓 **Curso:** Técnicas de Pesquisa e Análise Econômica II (PSAE00320)  
> 🏫 **Turma:** 012026.2  
> 👨‍🏫 **Professor:** Aléssio Almeida  

---

## 🎯 1. Sobre o Projeto e Problema de Pesquisa

O objetivo deste projeto é criar uma base de dados que crie um funil que indique quais as regiões da Paraíba com maior carência de informação. Já que o programa 'Paraíba Sem Dívidas' da CORECON-PB busca aprimorar o conhecimento da população sobre educação financeira, entretanto, foi percebida uma necessidade de indicações para onde direcionar mais os recursos que tornem esse processo mais viável. 

* ❓ **Pergunta de Pesquisa:** Como o acesso à informação afeta o conhecimento familiar em educação financeira na Paraíba?
* 🎯 **Objetivo Principal:** Mapear e quantificar a relação entre acesso à informação e educação financeira.

---

## 👥 2. Equipe de Desenvolvimento

👤 **Thiago Ramirez Balotta Starikoff** 
👤 **João Marcos Nery da Silva**
👤 **Cauã Antero do Nascimento** 
---

## 🗃️ 3. Fontes de Dados Utilizadas

Resumo das bases utilizadas no projeto (para o detalhamento completo, consulte o inventário de fontes na pasta `docs/`):

* 🏛️ **PNAD Contínua:** [Instituição, IBGE] — 📌 *Cobertura:* Brasil: 2022-2025
* 🏛️ **Acessos de Telecomunicações (Anatel Dados):** Anatel — 📌 *Cobertura:* Municípios / Paraíba (2022-2025)

---

## 📁 4. Estrutura do Repositório

Organização das pastas e arquivos do projeto conforme as diretrizes da Entrega 04:

```text
.
├── 📄 README.md             # Apresentação do projeto, equipe e instruções gerais
├── 🛡️ .gitignore            # Arquivos e diretórios ignorados pelo versionamento (segurança)
├── 📂 data/
│   ├── 📥 raw/              # Dados brutos e originais (não modificados)
│   └── 🧹 processed/        # Dados limpos, tratados e consolidados
├── 📓 notebooks/            # Scripts e notebooks (aquisição, tratamento e análise)
├── 📑 docs/                 # Documentação (inventário de fontes, dicionário e planos)
└── 📊 outputs/              # Resultados gerados (tabelas finais, gráficos e relatórios)
