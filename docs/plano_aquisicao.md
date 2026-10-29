# Plano de Aquisição de Dados

Este documento descreve como as bases utilizadas no projeto TPAE-2 são obtidas, processadas e atualizadas.

O projeto utiliza principalmente dados públicos do Censo Demográfico 2022, disponibilizados pelo Instituto Brasileiro de Geografia e Estatística (IBGE).

## Plano de aquisição

| Fonte | Método de obtenção | Arquivo / Endpoint | Frequência | Parâmetros / Filtros | Responsável | Data prevista | Procedimento de atualização |
|---|---|---|---|---|---|---|---|
| População residente, área territorial e densidade demográfica – Censo 2022 | Download de arquivo disponibilizado pelo IBGE | `2_1_Populacao_residente_Area_territorial_Densidade_demografica_xlsx.zip` / `tabela_2_1_PB.xlsx` | Conforme novas divulgações do IBGE | Estado da Paraíba | Equipe do projeto | Outubro/2026 | Baixar novamente o arquivo oficial, executar o notebook de aquisição e substituir a base processada após validação |
| Agregados por Setores Censitários – Censo 2022 | Download de arquivo disponibilizado pelo IBGE | `Agregados_por_setores_basico_BR_20260520.zip` / `Agregados_por_setores_basico_BR.csv` | Conforme novas divulgações do IBGE | `CD_UF = 25` para selecionar a Paraíba | Equipe do projeto | Outubro/2026 | Baixar a versão mais recente, executar novamente o tratamento e validar os 223 municípios |
| Cadastro de municípios brasileiros | Leitura de arquivo CSV disponibilizado em repositório público | `municipios.csv` | Quando necessário | `codigo_uf = 25` para selecionar a Paraíba | Equipe do projeto | Outubro/2026 | Consultar a versão disponível da base e executar novamente a filtragem dos municípios da Paraíba |

## 1. População residente, área territorial e densidade demográfica

### Método de obtenção

Os dados são obtidos a partir dos arquivos públicos disponibilizados pelo IBGE referentes ao Censo Demográfico 2022.

O arquivo utilizado no projeto é:

`2_1_Populacao_residente_Area_territorial_Densidade_demografica_xlsx.zip`

Dentro do arquivo compactado, a tabela utilizada para a Paraíba é:

`tabela_2_1_PB.xlsx`

### Tratamento

O arquivo é descompactado e lido em Python utilizando a biblioteca pandas.

São selecionadas as informações referentes aos municípios da Paraíba, resultando em uma base com 223 municípios.

As principais informações utilizadas são:

- nome do município;
- população residente;
- área territorial;
- densidade demográfica.

## 2. Agregados por Setores Censitários

### Método de obtenção

A base é obtida por download dos dados de Agregados por Setores Censitários do Censo Demográfico 2022 disponibilizados pelo IBGE.

O arquivo utilizado é:

`Agregados_por_setores_basico_BR_20260520.zip`

O arquivo CSV presente no ZIP é:

`Agregados_por_setores_basico_BR.csv`

### Parâmetros e filtros

A base original contém setores censitários de todo o Brasil.

Para selecionar somente os setores pertencentes à Paraíba é utilizado:

`CD_UF = 25`

Após a filtragem, são obtidos 9.639 registros de setores censitários relacionados aos 223 municípios da Paraíba.

### Tratamento

Os registros são agrupados utilizando:

- `CD_MUN`;
- `NM_MUN`;
- `SITUACAO`.

A variável `SITUACAO` permite distinguir setores classificados como:

- Urbana;
- Rural.

A população é agregada por município e situação.

Posteriormente são calculadas:

- população rural;
- população urbana;
- população total;
- percentual da população rural.

## 3. Cadastro de municípios brasileiros

### Método de obtenção

Durante o desenvolvimento, foi prevista a consulta à API de localidades do IBGE para obtenção da relação de municípios da Paraíba.

Como o serviço apresentou indisponibilidade durante a execução, foi utilizada como alternativa uma base pública de municípios brasileiros disponibilizada em formato CSV.

O arquivo utilizado é:

`municipios.csv`

### Parâmetros

Para selecionar os municípios da Paraíba é utilizado:

`codigo_uf = 25`

O resultado esperado é uma relação com os 223 municípios do estado.

Essa base possui função auxiliar no processo de identificação dos municípios.

## Notebook de aquisição

Os procedimentos de aquisição e tratamento são registrados em notebook Python, permitindo que as etapas sejam reproduzidas.

O notebook utilizado para essa etapa é:

`notebooks/01_aquisicao_dados_ibge.ipynb`

O notebook registra as etapas de:

1. carregamento das bases;
2. leitura dos arquivos;
3. filtragem da Paraíba;
4. tratamento dos dados;
5. agregação por município;
6. criação de variáveis derivadas;
7. validação dos resultados;
8. exportação dos arquivos processados.

## Validação

Após o tratamento da base de população urbana e rural, são realizadas verificações sobre:

- quantidade de municípios;
- estrutura das colunas;
- existência de valores ausentes;
- consistência das variáveis calculadas.

A base final de população urbana e rural possui:

- 223 municípios;
- 6 variáveis;
- nenhum valor ausente nas variáveis utilizadas.

## Atualização dos dados

Caso uma nova versão dos dados seja disponibilizada, o procedimento previsto é:

1. acessar novamente a fonte correspondente;
2. baixar a versão atualizada do arquivo;
3. manter uma cópia do arquivo original quando permitido;
4. executar novamente o notebook de aquisição e tratamento;
5. verificar a quantidade de municípios e possíveis valores ausentes;
6. comparar os resultados com a versão anterior;
7. exportar novamente a base processada;
8. registrar a atualização no repositório.

## Segurança e versionamento

O projeto utiliza apenas dados públicos.

Senhas, tokens, chaves de acesso, dados pessoais, documentos internos ou bases restritas não devem ser adicionados ao repositório.

Arquivos muito grandes ou que não possam ser redistribuídos devem ser substituídos por instruções que permitam sua obtenção a partir da fonte original.
