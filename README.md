# Desafio Técnico – Ciência de Dados (Programa Lighthouse)

Este projeto realiza uma **análise exploratória de dados (EDA)** sobre filmes, treina um modelo preditivo e permite gerar previsões com base nos dados do IMDb.

---

## Pré-requisitos

- Python 3.10 ou superior  
- Jupyter Notebook  
- Pip  

---

## Instalação

**1. Clone o repositório ou baixe os arquivos:**

```bash
git clone https://github.com/tcalmeida/indicium-lh-cd.git
cd indicium-lh-cd
```

**2. Instale as dependências:**
```bash
pip install -r requirements.txt
```

Configuração

Antes de executar o notebook, crie um aquivo variável de ambiente (.env) apontando para caminho do banco de dados:
`DB_IMDB=caminho/do/banco_de_dados`

## Execução

**3. Execução do Notebook:**

Inicie o Jupyter Notebook:
```bash
jupyter notebook
```

Abra o arquivo: Relatorio_de_analises_e_EDA.ipyn

## Uso do Modelo (`modelo_nota_imdb.pkl`)

Após executar o notebook e gerar o modelo, você pode utilizá-lo para prever a nota do IMDb de um filme com base em algumas variáveis.

### Exemplo de código:

```python
import joblib
import pandas as pd

# Carregar o modelo
model = joblib.load("modelo_nota_imdb.pkl")

# Criar um novo filme para prever a nota
novo_filme = {
    'Released_Year': 1994,
    'Runtime': 142,
    'Meta_score': 80.0,
    'No_of_Votes': 2343110,
    'Gross': 28341469
}

# Transformar em DataFrame
novo_filme_df = pd.DataFrame([novo_filme])

# Fazer a previsão
nota_prevista = model.predict(novo_filme_df)
print(f"Nota prevista do IMDb: {nota_prevista[0]:.1f}")
```

**Observações:**

- As colunas devem ter os mesmos nomes e tipos do dataset original (Released_Year, Runtime, Meta_score, No_of_Votes, Gross).

- O modelo foi treinado com regressão linear, portanto funciona melhor para filmes cujos valores das variáveis estão dentro do mesmo intervalo do conjunto de treino.

- O arquivo modelo_nota_imdb.pkl deve estar no mesmo diretório do script que o carrega.

