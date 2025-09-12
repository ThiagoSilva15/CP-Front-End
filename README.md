📌 Checkpoint #1 (2025_2) — IMDB Top 250 (KMeans)
📂 Estrutura do Projeto
/
├── notebooks/
│   ├── 01_scrape_and_kmeans_synopsis.ipynb   # Web scraping + KMeans com sinopses
│   └── 02_kmeans_all_features.ipynb          # KMeans com todas as features + comparação
├── data/                                     # Gerada automaticamente na execução
├── requirements.txt                          # Dependências do projeto
└── README.md

⚙️ Configuração do Ambiente

Criar e ativar um ambiente virtual:

python -m venv .venv
source .venv/bin/activate   # Linux/Mac
.venv\Scripts\activate      # Windows


Instalar as dependências:

pip install -r requirements.txt

🚀 Execução dos Notebooks
Notebook 1 — Scraping + KMeans (sinopses)

Realiza o scraping das sinopses dos filmes do IMDB Top 250.

Aplica KMeans considerando apenas o texto (TF-IDF).

Salva os seguintes arquivos:

data/imdb_top250_raw.csv

data/imdb_top250_k5_synopsis.csv

Notebook 2 — KMeans com todas as features

Utiliza como entrada: sinopses + gêneros + notas + votos + ano + duração.

Aplica KMeans (k=5) com múltiplas variáveis.

Compara métricas entre os dois modelos (Silhouette, Calinski-Harabasz, Davies-Bouldin).

Salva:

data/imdb_top250_k5_allfeatures.csv

Exibe gráficos comparativos e análise dos clusters.

📊 Insights e Justificativa

Modelo 1 (sinopse): clusters temáticos interpretáveis, mas sensíveis a ruídos e limitações do texto.

Modelo 2 (todas as features): clusters mais coesos e balanceados, com melhor separação segundo métricas.

Conclusão: O Modelo 2 é superior, pois combina semântica (sinopse) com contexto (gênero, época, rating e duração), gerando grupos mais consistentes e úteis para análise.
