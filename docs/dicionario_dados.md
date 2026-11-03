# Dicionário de Dados — TPAE II

Este documento apresenta as variáveis da base municipal tratada na Entrega 5, suas descrições, tipos, unidades de medida e fontes.

## Base final — Municípios da Paraíba

Arquivo: `base_municipal_pb_tratada.csv`

Unidade de análise: município.

Cobertura: 223 municípios da Paraíba.

Ano de referência dos dados: 2022.

| Variável | Descrição | Tipo | Unidade | Fonte |
|---|---|---|---|---|
| `codigo_ibge` | Código de identificação do município | Inteiro | Código identificador | IBGE — Censo 2022 |
| `municipio` | Nome do município | Texto | Não se aplica | IBGE — Censo 2022 |
| `populacao_rural` | População residente em setores classificados como rurais | Inteiro | Habitantes | IBGE — Agregados por Setores Censitários |
| `populacao_urbana` | População residente em setores classificados como urbanos | Inteiro | Habitantes | IBGE — Agregados por Setores Censitários |
| `populacao_total` | Soma das populações rural e urbana | Inteiro | Habitantes | Calculada a partir dos setores censitários |
| `percentual_rural` | Participação da população rural na população total | Numérico | % | Calculada a partir dos setores censitários |
| `taxa_alfabetizacao` | Percentual de pessoas alfabetizadas com 15 anos ou mais | Numérico | % | IBGE — Tabela 9543 |
| `renda_per_capita` | Rendimento nominal mensal domiciliar per capita médio | Numérico | R$ por pessoa/mês | IBGE — Tabela 10295 |

## Variáveis originais utilizadas no tratamento

| Variável | Descrição | Utilização |
|---|---|---|
| `CD_UF` | Código da Unidade da Federação | Filtrar os registros da Paraíba |
| `CD_MUN` | Código do município | Agrupar os setores por município |
| `NM_MUN` | Nome do município | Identificar os municípios |
| `SITUACAO` | Classificação urbana ou rural do setor | Separar as populações urbana e rural |
| `v0001` | População residente | Calcular os totais populacionais |

## Tratamento e integração

Foram considerados os setores censitários da Paraíba classificados como urbanos ou rurais.

Os registros sem classificação em `SITUACAO` foram excluídos da agregação. Os cinco registros excluídos apresentavam população igual a zero.

A população foi agregada por município e situação do setor censitário.

As informações de alfabetização e renda foram integradas à base municipal utilizando o nome padronizado do município como chave de junção, com validação da correspondência entre os registros.

O código IBGE foi preservado como identificador na base final.

## Variáveis derivadas

**População total**

`populacao_total = populacao_rural + populacao_urbana`

**Percentual rural**

`percentual_rural = (populacao_rural / populacao_total) * 100`

O percentual foi arredondado para duas casas decimais.

## Validação e limitações

A base final possui 223 registros e 8 variáveis, sem valores ausentes ou municípios duplicados.

A soma populacional dos setores censitários é de 3.974.687 habitantes, enquanto a população da
