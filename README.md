🎬 Checkpoint #1 — 2025/2
IMDB Top 250 — Clusterização com KMeans

Nome: Thiago Almança da Silva — RM 558108
Prazo de entrega: 14/09/2025 às 23:59 (America/Sao_Paulo)

📁 Estrutura do Projeto
.
├── notebooks/
│   ├── 01_scrape_and_kmeans_synopsis.ipynb      # Scraping + clusterização por sinopse
│   └── 02_kmeans_all_features.ipynb              # Clusterização com todas as features
├── data/                                        # Gerada automaticamente durante a execução
│   ├── imdb_top250_raw.csv
│   ├── imdb_top250_k5_synopsis.csv
│   └── imdb_top250_k5_allfeatures.csv
├── requirements.txt
└── README.md

⚙️ Configuração do Ambiente

Criar e ativar um ambiente virtual

python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux/macOS
source .venv/bin/activate


Instalar as dependências

pip install -r requirements.txt

🚀 Execução dos Notebooks
Notebook 1 — 01_scrape_and_kmeans_synopsis.ipynb

Realiza web scraping dos 250 filmes do IMDB Top 250

Gera a base data/imdb_top250_raw.csv

Aplica TF-IDF na sinopse e KMeans (k=5)

Salva os resultados em data/imdb_top250_k5_synopsis.csv

Inclui análise e visualização 3D dos clusters por sinopse

Notebook 2 — 02_kmeans_all_features.ipynb

Carrega os dados gerados pelo Notebook 1

Inclui features adicionais: gêneros, notas, votos, ano e duração

Executa o KMeans (k=5) com todas as features combinadas

Salva data/imdb_top250_k5_allfeatures.csv

Gera métricas (Silhouette, Calinski-Harabasz, Davies-Bouldin)

Visualiza os clusters em 3D

Compara os resultados entre:

Modelo 1: apenas sinopse

Modelo 2: todas as features

📌 Entregáveis

Preencher no final do Notebook 2:

Insights e conclusões obtidas

Justificativa clara sobre qual modelo é o melhor

Subir este repositório completo no GitHub

Atualizar o PDF de entrega com o link do repositório

📊 Observações

O scraping pode demorar alguns minutos — aguarde a coleta completa dos 250 filmes.

Caso alguma execução falhe por mudanças no HTML do IMDb, rode novamente.

O diretório data/ é criado automaticamente ao salvar os resultados.
