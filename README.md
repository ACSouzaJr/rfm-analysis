# Análise de Segmentação de Clientes (RFM)

## Visão Geral
Este projeto implementa uma análise de segmentação de clientes utilizando a metodologia **RFM** (Recency, Frequency, Monetary). Através de técnicas de Machine Learning, o projeto identifica diferentes perfis de consumidores com base em seu comportamento histórico de compras, permitindo estratégias de marketing mais assertivas e personalizadas.

## Objetivos
- Processar dados transacionais para extrair métricas de comportamento de compra.
- Calcular os indicadores de Recência (dias desde a última compra), Frequência (quantidade de compras) e Valor Monetário (total gasto).
- Agrupar clientes com perfis similares utilizando o algoritmo de clustering **K-Means**.
- Visualizar a distribuição dos segmentos e sugerir ações estratégicas para cada perfil identificado.

## Base de Dados
Os dados foram retirados do artigo **"[RFM-Based Customer Segmentation: A Pedagogical Case Study for Marketing Analytics Education](https://jame.scholasticahq.com/article/157562-rfm-based-customer-segmentation-a-pedagogical-case-study-for-marketing-analytics-education)"**. O arquivo original está localizado em `data/2855054_v1_data.csv`.

As principais colunas utilizadas são:
- `CustomerID`: Identificador único do cliente.
- `SaleID`: Identificador da transação.
- `SaleDate`: Data e hora da compra.
- `ItemValue`: Valor monetário do item/venda.
- `ItemDescription`: Descrição do produto.

## Metodologia
1. **Limpeza e Preparação:** Remoção de valores nulos, exclusão de clientes genéricos (ID 0) e tratamento de duplicatas.
2. **Engenharia de Atributos:** Cálculo das métricas R, F e M por cliente.
3. **Transformação de Dados:** Aplicação de escala logarítmica para mitigar a assimetria dos dados e padronização com `StandardScaler`.
4. **Clustering:** Utilização do algoritmo **K-Means**. O número ideal de grupos foi determinado através do **Método do Cotovelo (Elbow Method)** e da **Análise de Silhueta**.
5. **Análise Visual:** Uso de **PCA** (Principal Component Analysis) para visualização dos clusters em 2D e *Snake Plots* para comparação das características de cada grupo.

## Resultados
A análise identificou três segmentos principais de clientes:
- **Champions (Grupo 1):** Clientes com baixíssima recência, alta frequência e alto valor gasto. São os melhores clientes.
- **Novos/Promissores (Grupo 0):** Clientes que compraram recentemente, mas ainda possuem frequência e gastos moderados.
- **Em Risco/Hibernando (Grupo 2):** Clientes que não compram há muito tempo e possuem baixo histórico de frequência e valor.

## Como Executar
O projeto foi desenvolvido em Python, utilizando o gerenciador de pacotes `uv`.

1. **Pré-requisitos**
    - [Python](https://www.python.org/) (versão indicada no .python-version)
    - [uv](https://docs.astral.sh/uv/) instalado.

2. **Instalação**
    - Clone o repositório.
    - Sincronize o ambiente e instale as dependências:
    ```bash
    uv sync
    ```

3. **Execução:**
   - Abra o arquivo `rfm.ipynb`.
   - Execute todas as células para processar os dados, gerar os modelos de clustering e visualizar os gráficos resultantes.
