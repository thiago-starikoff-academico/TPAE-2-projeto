# Dicionário Preliminar de Dados

Este documento apresenta as principais variáveis utilizadas no projeto TPAE-2, com suas descrições, tipos, unidades de medida e fontes.

## Base municipal de população, área e densidade demográfica

| Variável | Descrição | Tipo | Unidade | Fonte / Cobertura |
|---|---|---|---|---|
| `codigo_ibge` | Código oficial utilizado para identificar cada município | Inteiro | Código identificador | IBGE / 223 municípios da Paraíba |
| `municipio` | Nome do município | Texto | Não se aplica | IBGE / 223 municípios da Paraíba |
| `populacao` | População residente no município | Inteiro | Habitantes | Censo Demográfico 2022 – IBGE / Paraíba |
| `area_km2` | Área territorial do município | Numérico | km² | IBGE / 223 municípios da Paraíba |
| `densidade_demografica` | Relação entre a população residente e a área territorial do município | Numérico | habitantes por km² | Censo Demográfico 2022 – IBGE / Paraíba |

## Base municipal de população urbana e rural

| Variável | Descrição | Tipo | Unidade | Fonte / Cobertura |
|---|---|---|---|---|
| `codigo_ibge` | Código oficial utilizado para identificar cada município | Inteiro | Código identificador | IBGE / 223 municípios da Paraíba |
| `municipio` | Nome do município | Texto | Não se aplica | IBGE / 223 municípios da Paraíba |
| `populacao_rural` | População residente em setores censitários classificados como rurais | Inteiro | Habitantes | Agregados por Setores Censitários – Censo 2022 / Paraíba |
| `populacao_urbana` | População residente em setores censitários classificados como urbanos | Inteiro | Habitantes | Agregados por Setores Censitários – Censo 2022 / Paraíba |
| `populacao_total` | Soma das populações rural e urbana do município | Inteiro | Habitantes | Calculada a partir dos dados do Censo 2022 / Paraíba |
| `percentual_rural` | Percentual da população total do município residente em áreas rurais | Numérico | % | Calculada a partir dos dados do Censo 2022 / Paraíba |

## Variáveis originais utilizadas no tratamento dos setores censitários

| Variável | Descrição no projeto | Tipo | Unidade | Utilização |
|---|---|---|---|---|
| `CD_UF` | Código da Unidade da Federação | Inteiro | Código identificador | Utilizado para selecionar os registros da Paraíba |
| `CD_MUN` | Código do município | Inteiro | Código identificador | Utilizado para identificar e agrupar os municípios |
| `NM_MUN` | Nome do município | Texto | Não se aplica | Utilizado para identificação dos municípios |
| `SITUACAO` | Classificação da situação do setor censitário | Texto | Urbana/Rural | Utilizada para separar a população urbana da rural |
| `v0001` | População residente considerada na agregação utilizada pelo projeto | Inteiro | Habitantes | Utilizada para calcular a população urbana e rural por município |

## Unidade de análise

A principal unidade de análise é o **município**.

O conjunto de dados final possui informações referentes aos **223 municípios do estado da Paraíba**.

## Chave de junção

A principal chave prevista para integração das bases é:

`codigo_ibge`

Nos dados originais dos setores censitários, essa informação aparece como `CD_MUN`.

O código permite relacionar informações provenientes de diferentes bases sem depender apenas do nome textual do município.

## Variáveis derivadas

Algumas variáveis foram calculadas durante o tratamento dos dados.

### População total

A população total é calculada pela soma:

`populacao_total = populacao_rural + populacao_urbana`

### Percentual rural

O percentual da população rural é calculado por:

`percentual_rural = (populacao_rural / populacao_total) * 100`

O resultado foi arredondado para duas casas decimais.
