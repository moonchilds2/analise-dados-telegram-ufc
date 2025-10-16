# Análise e Limpeza de Dados: Dataset fakeTelegram.BR_2022

**Disciplina:** CKP9011 - Introdução à Ciência de Dados / CK0223 - Mineração de Dados
**Instituição:** Universidade Federal do Ceará (UFC)
**Atividade:** Lista de Exercícios 1 - Tratamento de Dados

## 📝 Descrição do Projeto

Este repositório documenta o processo completo de tratamento, limpeza e enriquecimento de dados aplicado ao dataset `fakeTelegram.BR_2022.csv`, como parte da avaliação da disciplina de Introdução à Ciência de Dados.

O objetivo principal é exercitar os conceitos de manipulação de dados, transformando um conjunto de dados brutos em uma base limpa, consistente e pronta para análises mais profundas. O trabalho abrange desde a identificação e tratamento de valores ausentes e duplicados até a engenharia de novos atributos (features) para extrair mais valor do conteúdo textual das mensagens.

## 🛠️ Tecnologias Utilizadas

* **Python 3**
* **Pandas:** Para manipulação e análise dos dados.
* **NumPy:** Para operações numéricas eficientes.
* **Jupyter Notebook:** Como ambiente de desenvolvimento e documentação.

## 📂 Estrutura do Repositório

.
├── data/
│   └── raw/
│       └── fakeTelegram.BR_2022.csv
├── notebooks/
│   └── 01_Analise_e_Limpeza_Dados.ipynb
├── .gitignore
├── README.md
└── requirements.txt

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

5.  **Execute o Notebook:**
    Abra o Jupyter Notebook `notebooks/01_Analise_e_Limpeza_Dados.ipynb` para ver e executar o passo a passo da análise.

---

## ✅ Tarefas Realizadas no Notebook

O notebook implementa todas as tarefas solicitadas na Lista de Exercícios 1:

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
    * **`sentiment`**: Classificação de sentimento (-1 para negativo, 0 para neutro, 1 para positivo).

4.  **Limpeza de Ruídos (Trava-Zaps):**
    * Implementação de uma função com múltiplas heurísticas para detectar e remover mensagens maliciosas do tipo "trava-zap".

Ao final do processo, o DataFrame está limpo, consistente e enriquecido com novos atributos prontos para a próxima etapa de análise.