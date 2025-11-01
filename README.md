# Projeto-Estatistica

# Fase 1: Setup do Ambiente e Compreensão dos Dados
Ambiente:

[ ] Criar a pasta do projeto (ex: projeto_ecommerce).

[ ] Criar um ambiente virtual (venv) dentro da pasta.

[ ] Ativar o ambiente virtual.

[ ] Instalar as bibliotecas: pip install jupyterlab pandas numpy matplotlib seaborn scipy statsmodels.

Dados:

[ ] Baixar o dataset da Olist (Kaggle).

[ ] Descompactar os arquivos .csv na pasta do projeto.

[ ] Iniciar o JupyterLab (jupyter lab).

[ ] Criar um novo notebook (ex: analise_ecommerce.ipynb).

Inspeção:

[ ] Carregar os principais CSVs em DataFrames (ex: orders, order_items, payments, customers, products).

[ ] Executar .info() em cada DataFrame para listar colunas, tipos de dados e contagem de nulos.

[ ] Executar .head() em cada DataFrame para inspecionar visualmente os dados.

[ ] Executar .describe() nas colunas numéricas para ver estatísticas básicas (média, min, max, quartis).

Esquema (Entregável):

[ ] Identificar e listar as Chaves Primárias (PK) e Estrangeiras (FK) de cada tabela.

[ ] Desenhar o Diagrama Entidade-Relacionamento (DER) (ex: usando dbdiagram.io).

[ ] Salvar o DER como uma imagem (PNG/PDF) para anexar ao relatório.

# ☐ Fase 2: Limpeza e Preparação dos Dados (Data Cleaning)
Tipos de Dados:

[ ] Converter todas as colunas de data/hora para datetime (ex: order_purchase_timestamp, order_delivered_customer_date, order_estimated_delivery_date).

[ ] Garantir que colunas monetárias (ex: price, freight_value, payment_value) sejam do tipo float.

Tratamento de Nulos:

[ ] Analisar (.isnull().sum()) colunas com dados nulos (ex: order_delivered_customer_date).

[ ] Documentar a estratégia: os nulos na data de entrega são, em sua maioria, pedidos cancelados ou não enviados? (ex: filtrar apenas order_status == 'delivered').

[ ] Tratar nulos em colunas categóricas (ex: product_category_name) se necessário (ex: preencher com "desconhecida").

Limpeza de Strings:

[ ] Padronizar colunas categóricas (ex: product_category_name, customer_state) para minúsculas e remover espaços extras (.lower().strip()).

Integridade e Duplicatas:

[ ] Verificar se order_id é único na tabela orders (.duplicated().sum()).

[ ] Verificar se customer_id é único na tabela customers.

[ ] Decidir o "grão" da análise: a análise será por pedido (order_id) ou por item de pedido? (Sugestão: agregar os dados no nível do pedido).

Outliers:

[ ] Calcular os limites (ex: Regra IQR) para colunas-chave: price, freight_value.

[ ] Documentar a % de outliers e a decisão (ex: "Mantidos para análise, pois representam compras de alto valor legítimas").

# ☐ Fase 3: Engenharia de Atributos (Feature Engineering)
Criação da Tabela Fato (Master Table):

[ ] Join 1: Unir orders com customers (via customer_id).

[ ] Join 2: Unir a tabela resultante com order_payments (via order_id).

[ ] Join 3: Unir a tabela resultante com order_items (via order_id).

[ ] Join 4: Unir a tabela resultante com products (via product_id).

Agregação por Pedido:

[ ] Agregar os dados no nível order_id.

[ ] Calcular Subtotal por pedido (soma de price dos itens).

[ ] Calcular Frete por pedido (soma de freight_value dos itens).

[ ] Calcular Total_Pedido (soma de payment_value dos pagamentos) -> Este será seu "Ticket Médio".

Criação dos KPIs (colunas):

[ ] delivery_lead_time_days = (order_delivered_customer_date - order_purchase_timestamp).dt.days.

[ ] delivery_delay_days = (order_delivered_customer_date - order_estimated_delivery_date).dt.days.

[ ] is_late = 1 se delivery_delay_days > 0, 0 caso contrário (use np.where).

[ ] is_confirmed = 1 se order_status == 'delivered', 0 caso contrário (defina sua regra de "Confirmado").

[ ] is_canceled = 1 se order_status == 'canceled', 0 caso contrário.

[ ] freight_share = Frete / Total_Pedido (cuidado com divisão por zero).

[ ] order_month (ex: order_purchase_timestamp.dt.month).

[ ] order_year (ex: order_purchase_timestamp.dt.year).

[ ] customer_region (Mapear customer_state para Regiões: 'SP' -> 'Sudeste', 'BA' -> 'Nordeste', etc.).

# ☐ Fase 4: Análise Exploratória de Dados (EDA)
Análise Descritiva (Tabelas):

[ ] Gerar tabela de medidas descritivas (média, mediana, Q1, Q3, std) para: Total_Pedido, Frete, delivery_lead_time_days, delivery_delay_days.

Visualização (Gráficos):

[ ] KPIs Financeiros: Histograma e Boxplot do Total_Pedido (Ticket Médio).

[ ] KPIs Logísticos: Histograma e Boxplot do delivery_lead_time_days (Prazo de Entrega).

[ ] KPIs Logísticos: Gráfico de Barras da Taxa de Atraso (is_late.mean()) por customer_region.

[ ] KPIs Pagamento: Gráfico de Barras (ou Pizza) da contagem de pedidos por payment_type.

[ ] KPIs Pagamento: Gráfico de Barras da Taxa de Cancelamento (is_canceled.mean()) por payment_type.

[ ] KPIs Produto: Gráfico de Barras (Top 15) da Receita por product_category_name.

[ ] KPIs Sazonalidade: Gráfico de Linha da Receita (Total_Pedido.sum()) por Mês/Ano.

[ ] Correlação: Heatmap de correlação entre as variáveis numéricas (Total_Pedido, Frete, delivery_lead_time_days, is_late).

# ☐ Fase 5: Análise Inferencial (Rigor Estatístico)
Verificação de Suposições:

[ ] Plotar Histograma e QQ-Plot do Total_Pedido para checar normalidade.

[ ] Documentar a não normalidade e justificar o uso do Teorema Central do Limite (TCL) devido ao grande tamanho da amostra (N).

Intervalos de Confiança (IC) de 95%:

[ ] Calcular e reportar o IC 95% para a Média do Total_Pedido (Ticket Médio).

[ ] Calcular e reportar o IC 95% para a Média do delivery_delay_days (Atraso Médio).

[ ] Calcular e reportar o IC 95% para a Proporção de is_late (Taxa de Atraso).

[ ] Calcular e reportar o IC 95% para a Proporção de is_canceled (Taxa de Cancelamento).

Documentação:

[ ] Escrever a interpretação de cada IC em linguagem de negócio (ex: "Com 95% de confiança, o verdadeiro ticket médio de todos os clientes está entre R$ X e R$ Y.").

# ☐ Fase 6: Montagem do Relatório e Entrega
Estrutura do Relatório:

[ ] Criar um documento (.md ou Google Doc/Word) com as seções: Sumário Executivo, Dados & Método, EDA, Análise Inferencial, Conclusões.

Conteúdo:

[ ] Dados & Método: Adicionar o DER (da Fase 1) e descrever as principais decisões de limpeza e feature engineering (Fases 2 e 3).

[ ] EDA: Selecionar e inserir os gráficos e tabelas mais relevantes da Fase 4, com uma breve interpretação para cada um.

[ ] Inferência: Apresentar os resultados da Fase 5 (os ICs e suas interpretações).

[ ] Conclusões: Listar limitações (ex: "Dataset não possui dados de desconto") e sugerir próximos passos.

[ ] Sumário Executivo (Escrever por último): Resumir os 3-5 achados mais importantes e acionáveis do estudo.

# Entrega Final:

[ ] Limpar e comentar o Notebook Jupyter.

[ ] Rodar o notebook do início ao fim ("Restart Kernel and Run All Cells").

[ ] Exportar o relatório final para PDF.

[ ] Criar um arquivo .zip contendo:

Relatorio_Analitico.pdf

analise_ecommerce.ipynb

(Opcional) A imagem do DER.png

-------------------------------------
# DER
https://dbdiagram.io/home
# Dataset
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
# Docs
https://docs.google.com/document/d/1v-STInnRTq2ZK3R7JGL8Foiwf2uE2n9ELy94gF9GbSg/edit?usp=sharing
