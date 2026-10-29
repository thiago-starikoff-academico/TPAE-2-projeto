# Inventário de Fontes de Dados

Este documento apresenta as fontes de dados utilizadas no projeto TPAE-2. Os dados utilizados são provenientes de fontes públicas, com prioridade para dados oficiais do Instituto Brasileiro de Geografia e Estatística (IBGE).

## Inventário

| Base | Instituição / Fonte | Link | Cobertura | Formato | Acesso | Licença / Uso |
|---|---|---|---|---|---|---|
| População residente, área territorial e densidade demográfica – Censo 2022 | IBGE – Instituto Brasileiro de Geografia e Estatística | https://www.ibge.gov.br/estatisticas/sociais/populacao/22827-censo-demografico-2022.html | 223 municípios da Paraíba | XLSX | Outubro/2026 | Dados públicos |
| Agregados por Setores Censitários – Resultados do Universo – Censo 2022 | IBGE – Instituto Brasileiro de Geografia e Estatística | https://www.ibge.gov.br/estatisticas/sociais/populacao/22827-censo-demografico-2022.html | Brasil, com filtragem de 9.639 setores censitários da Paraíba e agregação dos 223 municípios | CSV compactado em ZIP | Outubro/2026 | Dados públicos |
| Cadastro de municípios brasileiros | Repositório Municípios Brasileiros – GitHub | https://github.com/kelvins/municipios-brasileiros | Municípios brasileiros, com filtragem dos 223 municípios da Paraíba | CSV | Outubro/2026 | Base pública |

## Descrição das fontes

### 1. População residente, área territorial e densidade demográfica

A base do Censo Demográfico 2022 do IBGE foi utilizada para obter informações sobre os municípios do estado da Paraíba.

Foram utilizadas principalmente as informações de população residente, área territorial e densidade demográfica.

A base possui informações para os 223 municípios da Paraíba e foi obtida em formato XLSX.

### 2. Agregados por Setores Censitários

A base de Agregados por Setores Censitários do Censo Demográfico 2022 foi utilizada para identificar a distribuição da população entre áreas urbanas e rurais.

A base original possui dados de setores censitários de todo o Brasil. Durante o tratamento, foram selecionados apenas os registros referentes ao estado da Paraíba.

Após a filtragem, foram obtidos 9.639 setores censitários correspondentes aos 223 municípios paraibanos.

Os dados foram agrupados por município e pela variável de situação do setor, classificada como Urbana ou Rural.

A partir desse processamento foram obtidas as seguintes informações:

- população rural;
- população urbana;
- população total;
- percentual da população rural.

### 3. Cadastro de municípios brasileiros

O cadastro de municípios foi utilizado como fonte auxiliar para identificação dos municípios brasileiros por meio do código IBGE.

Foram selecionados apenas os municípios pertencentes ao estado da Paraíba, totalizando 223 municípios.

Essa fonte foi utilizada como alternativa durante o processo de aquisição quando o acesso à API de localidades do IBGE apresentou indisponibilidade.

## Unidade de análise

A principal unidade de análise do projeto é o município.

Nesta etapa, o projeto trabalha com os 223 municípios do estado da Paraíba.

## Chaves de identificação e junção

A principal chave utilizada para identificar os municípios e permitir a integração entre diferentes bases é o código oficial do município definido pelo IBGE.

No conjunto de dados tratado, essa variável é denominada:

`codigo_ibge`

O nome do município (`municipio`) também é mantido para facilitar a leitura e interpretação dos dados, mas o código IBGE é utilizado como identificador principal.

## Dados processados

O processamento dos dados de população urbana e rural gerou uma base municipal contendo 223 registros e as seguintes variáveis:

- `codigo_ibge`: código oficial do município no IBGE;
- `municipio`: nome do município;
- `populacao_rural`: população residente em setores classificados como rurais;
- `populacao_urbana`: população residente em setores classificados como urbanos;
- `populacao_total`: soma das populações rural e urbana;
- `percentual_rural`: percentual da população municipal residente em áreas rurais.

O arquivo tratado é armazenado no diretório:

`data/processed/`

com o nome:

`populacao_urbana_rural_municipios_pb_2022.csv`

## Procedimento de obtenção e tratamento

Os dados originais foram obtidos a partir das fontes indicadas neste inventário.

O tratamento foi realizado em Python, utilizando principalmente a biblioteca pandas em notebook do Google Colab.

O procedimento incluiu:

1. leitura dos arquivos originais;
2. filtragem dos registros referentes ao estado da Paraíba;
3. identificação dos municípios por código IBGE;
4. separação dos setores classificados como urbanos e rurais;
5. agrupamento da população por município;
6. cálculo da população total;
7. cálculo do percentual da população rural;
8. validação da quantidade de municípios e de valores ausentes;
9. exportação da base tratada em formato CSV.

A base final contém os 223 municípios da Paraíba e não apresenta valores ausentes nas variáveis utilizadas nesta etapa do projeto.
