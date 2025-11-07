# Análise de Dados de Mensagens do Telegram (Listas 1 e 2)

**Disciplina:** CKP9011 - Introdução à Ciência de Dados / CK0223 - Mineração de Dados

**Instituição:** Universidade Federal do Ceará (UFC)

**Atividade:** Listas de Exercícios 1 e 2 - Tratamento e Análise de Dados

## 📝 Descrição do Projeto

Este repositório documenta o processo completo de análise de dados aplicado ao dataset `fakeTelegram.BR_2022.csv`, como parte da avaliação da disciplina de Introdução à Mineração e Ciência de Dados.

O projeto é dividido em duas etapas principais:
1.  **Limpeza e Engenharia de Atributos (Lista 1):** Foco no pré-processamento pesado dos dados brutos usando Pandas, tratando valores nulos, duplicados, inconsistências e criando *features* (como `sentiment`, `words`, `sharings`).
2.  **Análise Avançada (Lista 2):** Foco na extração de insights usando um banco de dados analítico (OLAP) de alta performance, o **DuckDB**, para executar 25 consultas complexas nos dados limpos.

## 🛠️ Tecnologias Utilizadas

* **Python 3**
* **Pandas:** Para manipulação e limpeza inicial dos dados.
* **NumPy:** Para operações numéricas eficientes.
* **Jupyter Notebook:** Como ambiente de desenvolvimento e documentação.
* **DuckDB:** Para consultas analíticas (OLAP) de alta performance em SQL.
* **PyArrow / FastParquet:** Para salvar e ler dados no formato colunar Parquet.
* **Scikit-learn:** Para análise de N-gramas (Item e.21 da Lista 2).
* **NLTK:** (Opcional, para listas de stop words).

## 📂 Estrutura do Repositório
 ```
.
├── data/
│   ├── raw/
│   │   └── fakeTelegram.BR_2022.csv
│   └── processed/
│       └── clean_file.parquet
├── notebooks/
│   ├── 01_Limpeza_e_Engenharia.ipynb  <-- (Trabalho da Lista 1)
│   └── 02_Analise_com_DuckDB.ipynb    <-- (Trabalho da Lista 2)
├── .gitignore
├── README.md
└── requirements.txt
 ```
## 🚀 Como Usar

Para replicar esta análise, siga os passos abaixo:

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/analise-dados-telegram-ufc.git](https://github.com/seu-usuario/analise-dados-telegram-ufc.git)
    cd analise-dados-telegram-ufc
    ```

2.  **Crie um ambiente virtual (recomendado):**
    ```bash
    python -m venv .venv
    source .venv/bin/activate  # No Windows: .venv\Scripts\activate
    ```

3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Adicione o dataset:**
    Faça o download do arquivo `fakeTelegram.BR_2022.csv` a partir do link fornecido na atividade e coloque-o dentro da pasta `data/raw/`.

5.  **Execute os Notebooks:**
    Para a experiência completa, execute os notebooks na ordem numérica:
    * **`01_Limpeza_e_Engenharia.ipynb`**: Para realizar a limpeza inicial e gerar o dataset com as colunas de engenharia de atributos (como `sentiment`). *Nota: O segundo notebook depende do primeiro ter sido rodado para criar a coluna `sentiment` no CSV original.*
    * **`02_Analise_com_DuckDB.ipynb`**: Para carregar os dados limpos, exportar para Parquet e executar as 30 consultas analíticas.

---

## ✅ Tarefas Realizadas

Este projeto implementa todas as tarefas das Listas 1 e 2.

### Notebook 01: Limpeza e Engenharia de Atributos (Lista 1)

Este notebook foca na limpeza pesada dos dados brutos e na criação de novas features (engenharia de atributos).

1.  **Análise de Valores Nulos:**
    * Identificação e listagem das posições (células) com valores faltantes.
    * Contagem total de linhas com valores faltantes.
    * Contagem de valores nulos por coluna (feature).

2.  **Verificação de Duplicatas e Inconsistências:**
    * Identificação e listagem de todas as linhas inteiramente duplicadas.
    * Validação de domínio para encontrar valores com tipo de dado incorreto.
    * Análise de inconsistências lógicas entre colunas.

3.  **Engenharia de Atributos:**
    * **`caracteres`**: Criação de uma coluna com a contagem de caracteres de cada mensagem.
    * **`words`**: Criação de uma coluna com a contagem de palavras de cada mensagem.
    * **`viral`**: Coluna booleana (0 ou 1) que identifica se o texto de uma mensagem aparece em outras linhas.
    * **`sharings`**: Contagem exata da frequência de cada texto no dataset.
    * **`sentiment`**: Classificação de sentimento (-1 para negativo, 0 para neutro, 1 para positivo) usando um classificador baseado em regras.

4.  **Limpeza de Ruídos (Trava-Zaps):**
    * Implementação de uma função com múltiplas heurísticas para detectar e remover mensagens maliciosas do tipo "trava-zap".

### Notebook 02: Análise Avançada com DuckDB (Lista 2)

Este notebook utiliza os dados limpos do primeiro (incluindo a coluna `sentiment`) e aplica consultas analíticas de alta performance usando DuckDB.

* **Preparação:** Os dados limpos são exportados para o formato **Parquet** (`clean_file.parquet`) e registrados como uma tabela virtual no DuckDB.
* **Análise (Item e):** Execução de **30 consultas SQL analíticas** para responder questões de negócio, incluindo:
    * Contagens de usuários, grupos e tipos de mídia.
    * Rankings (Top 30) de URLs, domínios e usuários mais ativos (total, texto e mídia).
    * Análise de viralidade (mensagens compartilhadas em grupos distintos).
    * Análise de N-gramas (unigramas, bigramas, trigramas) com `scikit-learn`.
    * Ranking de usuários mais "otimistas" e "pessimistas" com base no score de sentimento.
    * Análise de comprimento das mensagens e atividade por dia.
    * Busca por palavras-chave (`ILIKE`) para "FACÇÃO CRIMINOSA" e "SEGURANÇA".
