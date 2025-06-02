# 📊 Projeto de Análise de Vendas - BDAPB

## 📌 Descrição do Projeto

Este projeto consiste em realizar análises de vendas utilizando a base de dados da empresa fictícia **BDAPB**. O objetivo é fornecer à Diretoria de Vendas informações consolidadas e de fácil interpretação, por meio de relatórios e dashboards interativos criados no **Power BI**.

---

## 🗂️ Bases de Dados

As bases fornecidas para o projeto estão em formato **CSV**:

- **Cliente**: Cadastro de clientes
- **Produtos**: Produtos disponíveis na loja
- **Notas Fiscais**: Gestão de vendas
- **Departamento**: Nome e descrição dos departamentos
- **Lojas**: Identificação das lojas

Além disso, será necessária a criação de uma **Tabela Calendário** no Power BI (preferencialmente utilizando a linguagem **M** ou outro recurso equivalente).

---

## 🎯 Objetivos e Indicadores

Com base nas tabelas fornecidas, a Diretoria deseja acompanhar os seguintes indicadores, com possibilidade de análise dinâmica por: **Data**, **Estado da Loja** e **Nome do Produto**.

### ✅ Indicadores Solicitados

1. Evolução de vendas mensal nos últimos dois anos, com possibilidade de Drill Down por **Ano** e **Mês**.
2. Melhor dia de vendas em cada ano.
3. Comparativo com a **meta de R$ 700 mil** entre 2017 e 2020, destacando os anos em que a meta foi superada.
4. Quantidade total vendida por loja.
5. Quantidade máxima vendida nas cidades e por departamentos, visualizados no mesmo gráfico.
6. Preço médio e mediana por departamento.
7. Comportamento do **valor total de vendas vs. valor total de custo** ao longo do período.
8. Margem de crescimento de vendas por unidade nos últimos 12 meses.
9. Acumulado móvel de vendas anual, considerando apenas os **3 últimos anos**.
10. Perfil de compra por idade (% do valor de compra):
    - Menor que 30 anos → **Jovem**
    - De 30 a 65 anos → **Adulto**
    - Acima de 65 anos → **Idoso**
11. Tabela consolidada com:
    - Data da primeira venda por produto
    - Data da última venda por produto
    - Diferença em dias entre a primeira e a última venda
    - Formatação condicional com ícones:
      - ✅ **Verde**: 0 a 1405 dias
      - ⚠️ **Amarelo**: 1406 a 1420 dias
      - ❌ **Vermelho**: acima de 1421 dias
12. Total de vendas por gênero e localidade, utilizando o gráfico **"Tornado"** (disponível na AppSource do Power BI).
13. Produtos mais vendidos por departamento apresentados em **cartões**, fixos e não afetados por filtros.
14. Análises adicionais criadas a critério do analista para demonstrar domínio técnico (**mínimo: 1 aba extra**).
15. Encaminhamento do arquivo **.pbix** via e-mail.
16. Layout e Organização:
    - Capa e abas seguindo padrão visual para melhor interpretação dos resultados.
    - Filtros aplicados conforme necessidade, visando maior flexibilidade na análise.
    - Gráficos adequados para cada análise.
    - Garantia da **qualidade dos dados** com ajustes no Power Query, se necessário.
    - Utilização de **paleta de cores personalizada** no Power BI.

---

## 💡 Diferenciais Avaliados

- Integração de dados realizada dentro do Power BI ou através de:
  - **Pentaho**
  - **Integration Services (SSIS)**
  - **Python**
  
- Uso de **medidas DAX** para cálculo de indicadores.
- Definição correta de **relacionamentos entre tabelas**.
- Garantia da **qualidade de dados** no Power Query.

---

## 🛠️ Tecnologias Utilizadas

- **Power BI** (incluindo Power Query e DAX)
- **M Language** (para tabela calendário, se aplicável)
- **CSV** para importação de dados
- Ferramentas auxiliares opcionais:
  - **Pentaho**
  - **SSIS**
  - **Python**

---

## 🎨 Layout e Visualização

- Estrutura do relatório organizada com **menu inicial** e **abas** de dashboards.
- **Filtros** aplicados de forma a garantir flexibilidade na análise.
- **Gráficos** escolhidos de acordo com a melhor visualização de cada indicador.
- **Paleta de cores personalizada** para identidade visual.
- Garantia de **dados limpos e qualificados** para análises confiáveis.

---

## 🚀 Como Executar o Projeto

1. Abrir o **Power BI Desktop**.
2. Importar as bases de dados **CSV**.
3. Criar a **Tabela Calendário**.
4. Realizar o **relacionamento correto** entre as tabelas.
5. Desenvolver as **análises conforme as instruções**.
6. Aplicar o **layout padrão** e a **paleta de cores**.
7. Exportar o arquivo **.pbix** finalizado.

---
