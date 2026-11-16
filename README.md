# OPULINE | Análise de Vendas com Power BI

## Sobre o projeto

Este projeto foi desenvolvido durante um curso da **Alura**, acompanhando as aulas práticas e aplicando os conhecimentos apresentados pelo instrutor.

O objetivo foi desenvolver habilidades em análise de dados, utilizando o Power BI para realizar o tratamento, a modelagem e a visualização de informações comerciais.

Durante o curso, pratiquei a construção de dashboards interativos, criação de indicadores, utilização de medidas DAX e organização dos dados para análise.

## Ferramentas e tecnologias utilizadas

- **Power BI Desktop:** criação dos dashboards e relatórios interativos.
- **Power Query:** preparação e transformação dos dados.
- **DAX (Data Analysis Expressions):** criação de medidas e indicadores.
- **Modelagem de Dados:** organização das tabelas e seus relacionamentos.
- **Visualização de Dados:** construção de gráficos, indicadores e filtros interativos.

## Dashboard de Vendas

![Dashboard de Vendas](imagens/dashboard_vendas.png)

O dashboard apresenta uma visão geral do desempenho comercial, incluindo:

- Faturamento total de aproximadamente R$ 714 mil.
- 2.103 itens vendidos.
- Acompanhamento de metas.
- Evolução da receita entre 2021 e 2024.
- Distribuição geográfica das vendas.
- Análise do faturamento por categoria.

## Dashboard de Produtos

![Dashboard de Produtos](imagens/dashboard_produtos.png)

O dashboard permite explorar o desempenho dos produtos comercializados, utilizando:

- Ranking dos produtos vendidos.
- Gráfico de dispersão para comparação de indicadores.
- Filtros por origem, categoria e subcategoria.
- Seleção de períodos para análise.

## Modelagem de Dados

![Modelagem de Dados](imagens/modelo_dados.png)

Durante o desenvolvimento, pratiquei a organização e o relacionamento entre tabelas, incluindo informações de produtos, pedidos, categorias, marcas, calendário e metas.

A modelagem permite integrar diferentes informações para construir análises no Power BI.

## Medidas DAX Utilizadas

Durante o desenvolvimento do projeto OPULINE, realizado como atividade prática de um curso da Alura, utilizei a linguagem DAX (*Data Analysis Expressions*) para criar medidas e indicadores que auxiliam na análise do desempenho das vendas.

### 1. Faturamento

```dax
Faturamento =
SUMX(
    fPedidos,
    fPedidos[quantidade] * RELATED(dProdutosFinais[Preço])
)
```

**Objetivo:** calcular o faturamento total, multiplicando a quantidade de cada pedido pelo preço do produto correspondente.

**Funções utilizadas:**
- `SUMX`: percorre os registros da tabela de pedidos e soma os resultados das multiplicações.
- `RELATED`: busca o preço correspondente na tabela de produtos relacionada.

### 2. Faturamento Médio

```dax
FaturamentoMédio =
AVERAGEX(
    fPedidos,
    fPedidos[quantidade] * RELATED(dProdutosFinais[Preço])
)
```

**Objetivo:** calcular o valor médio das linhas de pedidos, considerando a quantidade multiplicada pelo preço do produto.

**Funções utilizadas:**
- `AVERAGEX`: calcula a média dos resultados de uma expressão avaliada para cada registro.
- `RELATED`: recupera o preço do produto na tabela relacionada.

### 3. Meta Máxima

```dax
MetáMaxima =
IF(
    [Faturamento] < [SomaMetas],
    [SomaMetas] * 1.2,
    [Faturamento]
)
```

**Objetivo:** definir um valor de referência para a escala de visualização de metas. Quando o faturamento está abaixo da meta, utiliza 120% da meta; caso contrário, utiliza o próprio faturamento.

**Função utilizada:**
- `IF`: avalia uma condição e retorna resultados diferentes conforme ela seja verdadeira ou falsa.

### 4. Meta S2Door

```dax
MetaS2Door = 8
```

**Objetivo:** estabelecer um valor fixo de referência igual a 8, utilizado como meta em um indicador do relatório.

### 5. Quantidade

```dax
Quantidade =
SUM(fPedidos[quantidade])
```

**Objetivo:** calcular a quantidade total de itens registrados nos pedidos.

**Função utilizada:**
- `SUM`: soma os valores de uma coluna numérica.

### 6. Soma das Metas

```dax
SomaMetas =
AVERAGE(dMetaMensal[Meta])
```

**Objetivo:** calcular a média dos valores registrados na coluna de metas mensais.

**Função utilizada:**
- `AVERAGE`: calcula a média aritmética dos valores numéricos de uma coluna.

### Conhecimentos praticados

Com essas medidas, pratiquei:

- Criação de medidas utilizando DAX.
- Utilização de funções de agregação, como `SUM` e `AVERAGE`.
- Cálculos iterativos com `SUMX` e `AVERAGEX`.
- Recuperação de informações entre tabelas relacionadas com `RELATED`.
- Aplicação de condições lógicas com `IF`.
- Construção de indicadores de faturamento, quantidade e metas.

## Power Query

O Power Query foi utilizado durante as atividades práticas de preparação dos dados para análise.

Esta seção poderá ser complementada com as transformações realizadas durante o curso.

## Processo de aprendizado

Além dos dashboards principais, o arquivo contém páginas auxiliares utilizadas durante as aulas para praticar diferentes tipos de gráficos, parâmetros e funcionalidades do Power BI.

Essas páginas foram mantidas no arquivo original como registro do aprendizado, mas ocultadas da apresentação principal para proporcionar uma navegação mais organizada.

## Origem do projeto

Projeto educacional desenvolvido acompanhando as aulas da plataforma **Alura**, como parte dos meus estudos e desenvolvimento de habilidades em Power BI e Análise de Dados.
