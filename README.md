# 📊 Projeto Estatística Aplicada ao E-commerce (Olist)

## Status do Projeto
[![Linguagem Principal](https://img.shields.io/badge/Linguagem-Jupyter%20Notebook-blue.svg)](https://jupyter.org/)
[![Status](https://img.shields.io/badge/Status-Concluído%20(Planejamento%20e%20Análise)-success)](https://github.com/Cecimedeiros/Projeto-Estatistica)
[![Dataset](https://img.shields.io/badge/Dataset-Olist%20E--commerce-orange)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

---

## 🎯 Descrição do Projeto

Este projeto tem como objetivo principal aplicar técnicas de **Estatística Descritiva** e **Estatística Inferencial** para analisar o desempenho de uma plataforma de e-commerce brasileira (baseado no dataset público da **Olist**).

O estudo segue uma pipeline de Data Science, desde a limpeza inicial dos dados até a geração de relatórios com *insights* acionáveis e robustez estatística, utilizando **Intervalos de Confiança (IC)** para validar as conclusões de negócio.

---

## 🛠️ Tecnologias Utilizadas

O projeto foi desenvolvido em **Python** utilizando o ambiente **Jupyter Notebook** e as seguintes bibliotecas:

| Categoria | Ferramenta | Descrição |
| :--- | :--- | :--- |
| **Linguagem** | Python | Linguagem de programação principal. |
| **Ambiente** | JupyterLab | Utilizado para desenvolver e documentar a análise. |
| **Manipulação** | `Pandas`, `NumPy` | Estruturação e cálculos eficientes de dados. |
| **Visualização** | `Matplotlib`, `Seaborn` | Criação de gráficos para a Análise Exploratória de Dados (EDA). |
| **Estatística** | `SciPy`, `Statsmodels` | Execução de testes estatísticos e cálculo de Intervalos de Confiança. |

---

## 🚀 Estrutura e Fases da Análise

O projeto foi estruturado em seis fases modulares, refletidas nos *notebooks* e na documentação:

### 1. ⚙️ Fase de Setup e Compreensão dos Dados

* Configuração do ambiente de desenvolvimento.
* Carregamento e inspeção inicial dos múltiplos arquivos `.csv` do dataset.
* Definição e documentação do **Diagrama Entidade-Relacionamento (DER)**.

### 2. 🧼 Fase de Limpeza e Preparação (Data Cleaning)

* Tratamento de tipos de dados (datas, monetários).
* Estratégias de tratamento para valores nulos (e.g., em datas de entrega).
* Verificação de integridade e tratamento de duplicatas.

### 3. 🧩 Fase de Engenharia de Atributos (Feature Engineering)

* Criação da **Tabela Fato (Master Table)**, unindo dados de pedidos, clientes, pagamentos e produtos.
* Cálculo de **KPIs** (Key Performance Indicators) essenciais, como:
    * **Ticket Médio** (`Total_Pedido`).
    * **Tempo de Entrega** (`delivery_lead_time_days`).
    * **Atraso de Entrega** (`delivery_delay_days`).
    * Proporções de **Frete** (`freight_share`).

### 4. 📈 Análise Exploratória de Dados (EDA)

* Geração de tabelas de medidas descritivas (média, mediana, quartis).
* Visualizações gráficas (Histogramas, Boxplots, Gráficos de Barras e Linha) para entender a distribuição de KPIs financeiros, logísticos e de pagamento.
* Análise de **Sazonalidade** e **Correlação** entre as variáveis.

### 5. 🔬 Análise Inferencial 

* Verificação das suposições estatísticas
* Cálculo e interpretação de **Intervalos de Confiança de 95%** para a média do **Ticket Médio**, **Atraso Médio** e proporções de **Atraso** e **Cancelamento**.

### 6. 📄 Montagem do Relatório e Entrega

* Estruturação de um **Relatório Analítico** consolidando as conclusões.
* Criação de um **Sumário Executivo** com os principais *insights* de negócio.

---

## 🏃 Como Executar o Projeto

Para replicar esta análise, siga os passos abaixo:

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/Cecimedeiros/Projeto-Estatistica.git](https://github.com/Cecimedeiros/Projeto-Estatistica.git)
    cd Projeto-Estatistica
    ```
2.  **Crie e ative o ambiente virtual (opcional, mas recomendado):**
    ```bash
    python -m venv venv
    # No Linux/macOS
    source venv/bin/activate
    # No Windows (CMD/PowerShell)
    .\venv\Scripts\activate
    ```
3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Baixe o Dataset:**
    * Baixe o dataset "Brazilian E-Commerce Public Dataset by Olist" do Kaggle (link na seção "Dataset e Fontes").
    * Descompacte os arquivos `.csv` e coloque-os na pasta `data/` do projeto.
5.  **Inicie o JupyterLab:**
    ```bash
    jupyter lab
    ```
6.  Abra e execute os *notebooks* em ordem sequencial: `01_data_cleaning.ipynb`, `02_eda.ipynb`, `03_statistical_inference.ipynb`, e `04_kpis_insights.ipynb`.

---

## 📚 Dataset e Fontes

* **Dataset Principal:** [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
* **Ferramenta para DER:** [dbdiagram.io](https://dbdiagram.io/home) (mencionada na documentação).
* **Relatório Analítico:** [Análise de Dados do E-commerce da Olist](https://docs.google.com/document/d/1tBM2px2vRkQY8Znir0d2MBHUOaSJqfRHwGgpZsUXcj0/edit?tab=t.0#heading=h.nkk3jc8d0p43)

---

## ✍️ Autores

**Cecília Medeiros || André Braga**
