# Análise de Empresas de Transporte Multimodal

## Sobre o projeto

Este projeto apresenta uma análise exploratória de dados de empresas de transporte multimodal, utilizando o Power BI para construção de dashboards interativos.

O objetivo é analisar a distribuição geográfica, a evolução temporal, a concentração das empresas por estado e município e a situação de adesão ao Decreto.

## Fonte dos dados

A análise utiliza uma base de dados de operadores de transporte multimodal.

A tabela utilizada no Power BI é:

`operador_transporte_multimodal`

## Ferramentas utilizadas

- Power BI
- DAX
- GitHub

## Perguntas analisadas

### 1. Quantas empresas de transporte multimodal existem e como elas estão distribuídas pelo território brasileiro?

O dashboard apresenta a quantidade total de empresas distintas, considerando o CNPJ como identificador, e mostra sua distribuição geográfica por meio de um mapa.

**Visualizações:** cartão e mapa.

### 2. Quais estados concentram a maior quantidade de empresas multimodais?

A distribuição por Unidade da Federação permite identificar os estados que concentram a maior quantidade de empresas multimodais.

**Visualização:** gráfico de barras por UF.

### 3. Como evoluiu a quantidade de empresas multimodais ao longo dos anos?

A série temporal apresenta a evolução da quantidade de empresas de acordo com o ano de vigência registrado na base.

**Visualização:** gráfico de linhas.

### 4. Qual é a situação das empresas quanto à adesão ao Decreto?

A análise identifica as empresas cujo campo `m` possui o valor `"sim"`. O dashboard apresenta a quantidade de empresas com adesão e seu percentual em relação ao total.

**Visualizações:** cartão, gráfico de rosca e indicador percentual.

### 5. Quais municípios concentram a maior quantidade de empresas multimodais?

O ranking apresenta os dez municípios com maior quantidade de empresas multimodais na base analisada.

**Visualização:** gráfico de barras.

## Medidas DAX

### Total de empresas

```DAX
Total Empresas =
DISTINCTCOUNT(
    operador_transporte_multimodal[cnpj]
)
```

### Adesão ao Decreto

```DAX
Adesão ao Decreto =
CALCULATE(
    DISTINCTCOUNT(
        operador_transporte_multimodal[cnpj]
    ),
    operador_transporte_multimodal[m] = "sim"
)
```

### Percentual de adesão

```DAX
% Adesão ao Decreto =
DIVIDE(
    [Adesão ao Decreto],
    [Total Empresas],
    0
)
```

### Empresas sem adesão

```DAX
Sem Adesão ao Decreto =
[Total Empresas] - [Adesão ao Decreto]
```

## Dashboards

### Página 1 — Visão geral

A primeira página apresenta:

- total de empresas;
- distribuição geográfica;
- empresas por estado;
- evolução das empresas por ano;
- ranking dos dez municípios com maior quantidade de empresas;
- indicador de adesão ao Decreto.

### Página 2 — Evolução e adesão

A segunda página apresenta:

- evolução temporal;
- situação de adesão ao Decreto;
- percentual de adesão;
- tabela detalhada dos operadores.

## Conclusão

Os dashboards permitem analisar diferentes aspectos dos operadores de transporte multimodal, combinando informações temporais e geográficas.

A análise permite observar a concentração das empresas em determinados estados e municípios, acompanhar a evolução dos registros ao longo dos anos e analisar a situação de adesão ao Decreto na base de dados.

## Estrutura do projeto

```text
analise-empresas-multimodais/
├── README.md
├── dados/
│   └── empresasMultimodais.csv
├── imagens/
│   └── dashboard.png
└── powerbi/
    └── empresasMultimodais.pbix
```
