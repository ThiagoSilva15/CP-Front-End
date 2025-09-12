🎬 Checkpoint #1 — 2025/2
IMDB Top 250 — Clusterização com KMeans

Nome: Thiago Almança da Silva — RM 558108


📁 Estrutura do Projeto
.
├── notebooks/
│   ├── 01_scrape_and_kmeans_synopsis.ipynb      # Scraping + clusterização por sinopse
│   └── 02_kmeans_all_features.ipynb              # Clusterização com todas as features
├── data/                                        # Gerada automaticamente durante a execução
│   ├── imdb_top250_raw.csv
│   ├── imdb_top250_k5_synopsis.csv
│   └── imdb_top250_k5_allfeatures.csv
├── requirements.txt                             # Dependências do projeto
└── README.md

⚙️ Configuração do Ambiente
1. Criar e ativar um ambiente virtual
python -m venv .venv

# Windows
.venv\Scripts\activate

# Linux/macOS
source .venv/bin/activate

2. Instalar as dependências
pip install -r requirements.txt

🚀 Execução dos Notebooks
📌 Notebook 1 — Scraping + KMeans (apenas sinopse)

Realiza scraping dos filmes do IMDB Top 250

Vetorização TF-IDF das sinopses

KMeans (k=5) apenas com dados textuais

Gera os arquivos:

data/imdb_top250_raw.csv

data/imdb_top250_k5_synopsis.csv

Inclui gráficos 3D dos clusters

📌 Notebook 2 — KMeans com todas as features

Utiliza como entrada: sinopses + gêneros + notas + votos + ano + duração

Aplica o mesmo processo de vetorização + escalonamento + KMeans (k=5)

Compara com o Modelo 1 (apenas sinopse)

Gera os arquivos:

data/imdb_top250_k5_allfeatures.csv

Produz métricas (Silhouette, Calinski-Harabasz, Davies-Bouldin)

Mostra gráficos 3D e análise comparativa dos clusters

✅ Entregáveis

Preencher no final do Notebook 2:

📌 Insights e conclusões obtidas

🏆 Justificativa sobre qual modelo é o melhor

Subir este projeto completo no GitHub

Inserir o link do repositório no PDF de entrega

⚡ Observações

O scraping pode levar alguns minutos — aguarde a coleta completa.

Caso ocorra falha por mudanças no HTML do IMDb, execute novamente.

O diretório data/ é criado automaticamente durante a execuçã
