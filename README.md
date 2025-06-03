
# 📊 Análise de Vendas - Projeto Power BI BDAPB

Este projeto apresenta uma análise completa dos dados de vendas utilizando **Power BI**. A solução abrange desde a importação e modelagem dos dados até a criação de indicadores e dashboards interativos.

---

## ✅ Etapas Realizadas

### 1. Importação das Bases

Todas as bases **CSV** foram importadas no Power BI Desktop, nomeadas e ajustadas conforme o seu conteúdo.

**Bases utilizadas:**

- `Clientes.csv`
- `Produtos.csv`
- `Notas Fiscais.csv`
- `Departamento.csv`
- `Lojas.csv`

---

### 2. Modelagem dos Dados

- Criados relacionamentos entre as tabelas:
  - `Notas Fiscais` ligada a `Clientes`, `Produtos`, `Departamento` e `Lojas` através dos campos de código.
  
- Desenvolvida uma **Tabela Calendário** utilizando a linguagem **M** no Power Query:

```m
let
    StartDate = #date(2016, 1, 1),
    EndDate = #date(2022, 12, 31),
    DateList = List.Dates(StartDate, Duration.Days(EndDate - StartDate)+1, #duration(1,0,0,0)),
    Table = Table.FromList(DateList, Splitter.SplitByNothing(), {"Date"})
in
    Table
```

- Posteriormente, adicionadas as colunas:
  - `Ano`
  - `Mês`
  - `Trimestre`

---

### 3. Transformação e Limpeza dos Dados

- ✅ Conversão de colunas de datas para o tipo **datetime**.
- ✅ Conversão de valores financeiros de **string** para **float**.
- ✅ Correção de inconsistências de codificação (acentuação, espaços).
- ✅ Normalização de campos como **Departamento** e **Localidade**, quando necessário.
- ✅ Limpeza da primeira linha da coluna `Departamento` que estava fora de formatação.
- ✅ Ajustes nas tabelas `Clientes` e `Lojas`: correção da localidade de `"são Paulo"` → `"São Paulo"` via transformação e substituição de valores.

---

### 4. Criação da Tabela NF/PRODUTO

Criada uma tabela mesclando `Notas Fiscais` e `Produtos` para obter o **Valor Unitário (VL_Produto)** e permitir análises mais detalhadas sobre os itens vendidos.

- Mesclagem feita pelo campo `Cod_Produto`.
- Possibilitou cálculos mais precisos, como o **Valor de Venda**.

---

### 5. Criação de Colunas Calculadas

Criada a coluna **Valor Venda** para determinar o valor de cada transação:

```dax
Valor Venda = 'Notas Fiscais'[Quantidade] * RELATED(Produtos[VL_Produto])
```

---

### 6. Desenvolvimento dos Indicadores

#### 1. Evolução de Vendas Mensal
- **Gráfico:** Linha ou Área
- **Eixo Y:** Valor Venda
- **Eixo X:** Ano e Mês (com Drill Down)

---

#### 2. Melhor Dia de Vendas
- **Visual:** Matriz ou Tabela com Data e Valor Venda.
- **Função:** `MAXX` para encontrar o maior valor de vendas por ano.

---

#### 3. Análise de Meta
- **Meta definida:** R$ 700 mil por ano (2017 a 2020).
- **Gráfico:** Colunas Clusterizadas
  - **Eixo X:** Ano
  - **Eixo Y:** Soma de Valor Venda
- Linha de constante representando a meta incluída.

---

#### 4. Quantidade Total Vendida por Loja
- **Gráfico:** Barras Horizontais
  - **Eixo Y:** Lojas
  - **Eixo X:** Soma de Quantidade

---

#### 5. Quantidade Máxima por Cidade e Departamento
- **Gráfico:** Barras Empilhadas ou Matriz
  - **Eixo X:** Cidade
  - **Eixo Y:** Quantidade Máxima
  - **Legenda:** Departamento

---

#### 6. Preço Médio e Mediana por Departamento
- **Visual:** Matriz mostrando:
  - Departamento
  - Preço Médio
  - Mediana

**Medidas criadas:**

```dax
Preço Médio = AVERAGEX(Produtos, Produtos[VL_Produto])
Mediana = MEDIANX(Produtos, Produtos[VL_Produto])
```

---

#### 7. Vendas x Custo
- **Gráfico:** Linhas comparando:
  - Valor Total Venda
  - Valor Total Custo

---

#### 8. Margem de Crescimento de Vendas (12 meses)

**Medida DAX:**

```dax
Crescimento = 
VAR VendasAtual = [Total Vendas]
VAR VendasAnterior = CALCULATE([Total Vendas], DATEADD('Calendario'[Date], -12, MONTH))
RETURN DIVIDE(VendasAtual - VendasAnterior, VendasAnterior, 0)
```

- **Gráfico:** Linhas mostrando a evolução da margem de crescimento.

---

#### 9. Acumulado Móvel de Vendas (últimos 3 anos)

**Medida DAX:**

```dax
Acumulado Móvel = 
CALCULATE(
    [Total Vendas],
    DATESINPERIOD('Calendario'[Date], MAX('Calendario'[Date]), -365, DAY)
)
```

- **Gráfico:** Demonstração do acumulado móvel.

---

#### 10. Perfil de Compra por Idade

**Coluna calculada:**

```dax
Perfil Idade = 
SWITCH(
    TRUE(),
    Clientes[Idade] < 30, "Jovem",
    Clientes[Idade] > 65, "Idoso",
    "Adulto"
)
```

- Criado filtro de idade para facilitar a análise.
- **Gráfico:** Colunas empilhadas ou pizza representando o percentual de valor de compra por perfil.

---

#### 11. Tabela Consolidada de Datas

**Medidas criadas:**

```dax
Data Primeira Venda = MIN('Notas Fiscais'[Data Venda])
Data Última Venda = MAX('Notas Fiscais'[Data Venda])
Diferença em Dias = DATEDIFF([Data Primeira Venda], [Data Última Venda], DAY)
```

**Formatação condicional com ícones:**

| Faixa de Dias | Ícone   |
|---------------|---------|
| 0 a 1405      | ✅ Verde |
| 1406 a 1420   | ⚠️ Amarelo |
| > 1421        | ❌ Vermelho |

- Configuração realizada no painel de formatação condicional do Power BI.

---

### 7. Personalização Visual

- Definida cor de fundo padrão do relatório: **RGB(21, 37, 76)**.
- Aplicada formatação condicional na tabela consolidada de datas para destacar a diferença de vendas.
- Criado filtro de idade para análises específicas sobre o perfil de compra.

---

## 🚀 Resultado

O projeto resultou em um dashboard interativo e visualmente consistente, possibilitando análises estratégicas sobre as vendas, comportamento dos clientes e desempenho das lojas.

---

## 🛠️ Tecnologias Utilizadas

- Power BI Desktop
- Linguagem M (Power Query)
- DAX (Data Analysis Expressions)
