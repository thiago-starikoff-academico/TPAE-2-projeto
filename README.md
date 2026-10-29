# TPAE-2-projeto

# 📊 Infraestrutura da Informação na Paraíba

> 🎓 **Curso:** Técnicas de Pesquisa e Análise Econômica II (PSAE00320)  
> 🏫 **Turma:** 012026.2  
> 👨‍🏫 **Professor:** Aléssio Almeida

---

## 🎯 1. Sobre o Projeto e Problema de Pesquisa

O projeto busca construir uma base de dados que ajude a identificar quais regiões da Paraíba apresentam maior carência de acesso à informação.

A proposta está relacionada ao programa **Paraíba Sem Dívidas**, do CORECON-PB, que busca ampliar o conhecimento da população sobre educação financeira. A partir da análise de diferentes indicadores, o projeto pretende contribuir para a identificação das regiões que podem apresentar maior necessidade de ações e recursos voltados à educação financeira.

**Pergunta de pesquisa:**  
Como o acesso à informação afeta o conhecimento familiar em educação financeira na Paraíba?

**Objetivo principal:**  
Mapear e quantificar a relação entre acesso à informação e educação financeira, buscando identificar regiões da Paraíba com maior necessidade de atenção.

---

## 👥 2. Equipe de Desenvolvimento

- **Thiago Ramirez Balotta Starikoff**
- **João Marcos Nery da Silva**
- **Cauã Antero do Nascimento**

---

## 🗃️ 3. Fontes de Dados

### Fontes já utilizadas

**IBGE – Censo Demográfico 2022**

Foram utilizados dados de população residente, área territorial e densidade demográfica dos **223 municípios da Paraíba**.

**IBGE – Agregados por Setores Censitários**

A base foi utilizada para identificar a distribuição da população entre áreas urbanas e rurais. Os dados nacionais foram filtrados para a Paraíba e posteriormente agregados por município.

**Cadastro de municípios brasileiros**

Base auxiliar utilizada para identificação dos municípios por meio dos códigos oficiais do IBGE.

### Fontes previstas para etapas posteriores

- **PNAD Contínua – IBGE:** indicadores relacionados às características socioeconômicas e ao acesso à informação.
- **Dados de Telecomunicações – Anatel:** indicadores de acesso aos serviços de telecomunicações nos municípios da Paraíba.

O detalhamento das fontes, cobertura, formato e forma de aquisição está disponível em:

`docs/inventario_fontes.md`

---

## 📁 4. Estrutura do Repositório

```text
.
├── README.md
├── .gitignore
│
├── data/
│   ├── raw/                 # Dados originais permitidos
│   └── processed/           # Dados tratados e consolidados
│
├── notebooks/               # Aquisição, tratamento e análise dos dados
│
├── docs/
│   ├── inventario_fontes.md
│   ├── dicionario_dados.md
│   └── plano_aquisicao.md
│
└── outputs/                 # Tabelas, gráficos e produtos gerados
```

---

## 📓 5. Aquisição e Tratamento dos Dados

Os procedimentos de aquisição e tratamento são desenvolvidos em Python, utilizando principalmente a biblioteca **pandas**.

O notebook utilizado nesta etapa é:

`notebooks/01_aquisicao_dados_ibge.ipynb`

Entre os procedimentos realizados estão:

1. carregamento das bases;
2. seleção dos dados referentes à Paraíba;
3. identificação dos municípios pelo código IBGE;
4. tratamento e organização das variáveis;
5. agregação dos setores censitários por município;
6. separação da população urbana e rural;
7. criação de variáveis derivadas;
8. validação dos resultados;
9. exportação das bases processadas.

---

## 📊 6. Dados Processados

Entre os arquivos produzidos nesta etapa está:

`data/processed/populacao_urbana_rural_municipios_pb_2022.csv`

A base contém os **223 municípios da Paraíba** e as seguintes variáveis:

- `codigo_ibge`
- `municipio`
- `populacao_rural`
- `populacao_urbana`
- `populacao_total`
- `percentual_rural`

A validação realizada nesta etapa não identificou valores ausentes nessas variáveis.

---

## 🔗 7. Unidade de Análise e Integração

A principal unidade de análise do projeto é o **município**.

A principal chave utilizada para identificar e integrar informações entre diferentes bases é o:

`codigo_ibge`

Essa padronização permitirá a integração futura dos indicadores provenientes das diferentes fontes utilizadas no projeto.

---

## 📑 8. Documentação

A documentação da Entrega 04 está organizada na pasta `docs/`:

- `inventario_fontes.md` — origem, cobertura e características das fontes utilizadas;
- `dicionario_dados.md` — descrição das principais variáveis;
- `plano_aquisicao.md` — procedimentos de obtenção, tratamento e atualização dos dados.

---

## ▶️ 9. Reprodução

Para reproduzir as etapas já desenvolvidas:

1. obter os dados nas fontes indicadas no inventário;
2. executar o notebook de aquisição disponível em `notebooks/`;
3. aplicar os filtros indicados para o estado da Paraíba;
4. executar as etapas de tratamento e validação;
5. gerar os arquivos tratados em `data/processed/`.

Arquivos grandes ou que não possam ser redistribuídos diretamente pelo repositório devem ser obtidos a partir das fontes originais indicadas na documentação.

---

## 🔒 10. Segurança

O projeto utiliza dados públicos.

Senhas, tokens, chaves de acesso, dados pessoais, documentos internos ou bases restritas não devem ser adicionados ao repositório. O arquivo `.gitignore` é utilizado para evitar o versionamento de arquivos que não devem ser publicados.
