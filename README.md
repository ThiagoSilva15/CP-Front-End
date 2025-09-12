Abaixo está o seu README.md do Checkpoint #1 – IMDB Top 250 (KMeans) reestruturado no mesmo formato profissional e visual do exemplo que você mostrou (iFood/PyCaret):

🎬 Checkpoint CP1 – IMDB Top 250 (KMeans)
👨‍🎓 Aluno

RM558108 — Thiago Almança da Silva

🎯 Objetivo

Aplicar técnicas de processamento de texto e clusterização com KMeans sobre os 250 filmes mais bem avaliados do IMDB, com o objetivo de agrupar filmes semelhantes com base em suas sinopses, gêneros e atributos numéricos (nota, votos, ano e duração).
Foram desenvolvidos dois modelos distintos para comparação de desempenho e qualidade dos clusters.

⚙️ Etapas Realizadas

Coleta e pré-processamento dos dados

Web scraping dos 250 filmes do IMDB Top 250

Limpeza e padronização das colunas (sinopse, nota, votos, ano, duração, gêneros)

Modelo 1 — apenas sinopse

Vetorização TF-IDF do texto

Redução de dimensionalidade com TruncatedSVD

Clusterização com KMeans (k=5)

Modelo 2 — todas as features

Combinação de TF-IDF (sinopse), gêneros (one-hot), e atributos numéricos padronizados

Redução de dimensionalidade com TruncatedSVD

Clusterização com KMeans (k=5)

Avaliação e visualização

Cálculo das métricas:

Silhouette Score

Calinski-Harabasz Index

Davies-Bouldin Index

Gráficos 3D dos clusters com Matplotlib

🧪 Comparativo dos Modelos
Modelo	Silhouette ↑	Calinski-Harabasz ↑	Davies-Bouldin ↓
Modelo 1 — apenas sinopse	0.13	1.44	1.46
Modelo 2 — todas as features	0.07	2.80	0.93

O Modelo 2 apresentou maior coesão e separação entre os clusters, principalmente por incluir múltiplas variáveis além do texto.
Apesar de a Silhouette ter sido levemente inferior (efeito comum ao adicionar mais dimensões), o Calinski-Harabasz aumentou e o Davies-Bouldin caiu, indicando clusters mais densos e bem definidos.

📊 Insights e Conclusões

Os clusters capturaram grupos coerentes de filmes como:

Crime/Drama clássicos

Épicos de fantasia/aventura

Sci-fi/ação modernos

Filmes históricos/biográficos

Thrillers psicológicos/arthouse

O Modelo 1 gerou grupos mais temáticos (palavras-chave), porém menos coesos.

O Modelo 2 criou grupos mais consistentes e equilibrados, pois considera tanto o conteúdo (sinopse) quanto o contexto (gêneros, votos, nota, ano, duração).

Assim, o Modelo 2 foi escolhido como melhor por apresentar métricas mais robustas e clusters menos difusos visualmente.

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

⚙️ Como Executar

Criar e ativar um ambiente virtual:

python -m venv .venv

# Windows
.venv\Scripts\activate

# Linux/macOS
source .venv/bin/activate


Instalar as dependências:

pip install -r requirements.txt


Executar os notebooks:

Notebook 1: scraping + KMeans (sinopse) → gera imdb_top250_k5_synopsis.csv

Notebook 2: KMeans (todas as features) → gera imdb_top250_k5_allfeatures.csv

🔍 Possíveis Melhorias Futuras

Testar embeddings semânticos (Sentence Transformers) para sinopses

Explorar outros algoritmos de clusterização (DBSCAN, HDBSCAN, Spectral)

Ajustar pesos relativos entre texto, gêneros e atributos numéricos

Experimentar outros valores de k usando métodos como Elbow e Silhouette média

Implementar pipeline automática para coleta e atualização da base

🔗 Links

📓 Notebooks no Colab: [inserir link]

🐙 Repositório no GitHub: [inserir link]
