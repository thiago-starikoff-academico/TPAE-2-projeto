# TPAE-2-projeto

# 📊 Infraestrutura da Informação na Paraíba

**Curso:** Técnicas de Pesquisa e Análise Econômica II (PSAE00320)  
**Turma:** 012026.2  
**Professor:** Aléssio Almeida

---

## 1. Sobre o projeto

O projeto busca construir uma base de dados que ajude a identificar quais regiões da Paraíba apresentam maior carência de acesso à informação.

A proposta está relacionada ao programa **Paraíba Sem Dívidas**, do CORECON-PB, que busca ampliar o conhecimento da população sobre educação financeira.

**Pergunta de pesquisa:** Como o acesso à informação afeta o conhecimento familiar em educação financeira na Paraíba?

**Objetivo:** Mapear a relação entre acesso à informação e educação financeira, identificando regiões que podem necessitar de maior atenção.

A Entrega 5 concentra-se na obtenção, limpeza e tratamento dos dados municipais, preparando a base para análises posteriores.

## 2. Equipe

- Thiago Ramirez Balotta Starikoff
- João Marcos Nery da Silva
- Cauã Antero do Nascimento

## 3. Fontes de dados

Foram utilizadas quatro bases do IBGE, com dados referentes ao Censo Demográfico de 2022:

| Fonte | Informação utilizada |
|---|---|
| Agregados por Setores Censitários | População urbana e rural |
| Tabela 4714 | População municipal oficial para conferência |
| Tabela 9543 | Taxa de alfabetização da população de 15 anos ou mais |
| Tabela 10295 | Rendimento nominal mensal domiciliar per capita médio |

Os dados foram selecionados para os 223 municípios do estado da Paraíba.

As informações sobre as fontes estão documentadas em `docs/inventario_fontes.md`.

## 4. Estrutura do repositório

- `data/raw/` — arquivos originais utilizados no processamento.
- `data/processed/` — pasta destinada aos dados tratados.
- `notebooks/` — notebooks do projeto.
- `docs/` — documentação e dicionário de dados.
- `outputs/` — pasta destinada aos produtos gerados.

Os arquivos finais da Entrega 5 também estão disponíveis na raiz do repositório.

## 5. Obtenção, limpeza e tratamento

O processamento foi desenvolvido em Python, utilizando principalmente a biblioteca pandas.

As etapas realizadas foram:

1. Leitura dos arquivos originais do IBGE.
2. Seleção dos setores censitários da Paraíba.
3. Identificação de valores ausentes e duplicidades.
4. Exclusão de cinco setores sem classificação urbana ou rural, todos com população igual a zero.
5. Agregação da população urbana e rural por município.
6. Cálculo da população total e do percentual rural.
7. Tratamento dos dados de alfabetização e renda.
8. Integração das bases municipais.
9. Validação e exportação da base final.

## 6. Base final tratada

**Arquivo:** `base_municipal_pb_tratada.csv`

A base final contém **223 municípios e 8 variáveis**:

| Variável | Descrição |
|---|---|
| `codigo_ibge` | Código de identificação do município |
| `municipio` | Nome do município |
| `populacao_rural` | População residente em áreas rurais |
| `populacao_urbana` | População residente em áreas urbanas |
| `populacao_total` | Soma das populações rural e urbana |
| `percentual_rural` | Percentual da população residente em áreas rurais |
| `taxa_alfabetizacao` | Taxa de alfabetização da população de 15 anos ou mais |
| `renda_per_capita` | Rendimento nominal mensal domiciliar per capita médio |

## 7. Validação dos dados

As verificações realizadas identificaram:

- 223 municípios na base final.
- Nenhum valor ausente nas oito variáveis.
- Nenhum código municipal duplicado.
- Nenhuma população negativa.
- Nenhuma inconsistência na soma das populações urbana e rural.
- Nenhum percentual rural ou taxa de alfabetização fora do intervalo de 0% a 100%.
- Nenhuma renda per capita negativa.

A população agregada dos setores censitários totalizou **3.974.687 habitantes**, enquanto a Tabela 4714 do IBGE apresentou **3.974.495 habitantes**.

A diferença de 192 habitantes, localizada em Alhandra e Jacaraú, foi mantida como limitação documentada.

## 8. Integração das bases

A unidade de análise é o município.

O código IBGE foi preservado como identificador da base final. As informações de alfabetização e renda foram integradas utilizando os nomes padronizados dos municípios, com validação das correspondências.

## 9. Arquivos da Entrega 5

- `TPAE_II_Entrega_5_notebook_limpo.ipynb` — notebook de processamento.
- `base_municipal_pb_tratada.csv` — base municipal tratada.
- `E05_equipe06_qualidade_dados_revisado (1).pdf` — relatório de qualidade.
- `docs/dicionario_dados.md` — dicionário das variáveis.

## 10. Reprodução

Para reproduzir o processamento:

1. Abrir o notebook da Entrega 5 no Google Colab.
2. Executar todas as células em sequência.
3. O notebook obtém os arquivos originais disponibilizados no repositório.
4. São realizados os tratamentos, as integrações e as validações.
5. A base final é exportada em CSV.

## 11. Segurança

O projeto utiliza dados públicos do IBGE.

Senhas, tokens, chaves de acesso e informações restritas não devem ser adicionados ao repositório.
