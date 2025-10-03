# 🎬 Checkpoint CP1 — IMDB Top 250 (KMeans)

**Aluno:** Thiago Almança da Silva — RM558108 


---

## 🎯 Objetivo

Aplicar técnicas de **processamento de texto** e **clusterização** com **K-Means** sobre os 250 filmes mais bem avaliados do IMDB, agrupando obras semelhantes a partir de **sinopses**, **gêneros** e **atributos numéricos** (nota, votos, ano e duração). Foram desenvolvidos **dois modelos** para comparação de desempenho e qualidade dos clusters.

---

## 🧭 Visão Geral da Abordagem

1. **Coleta**: web scraping dos 250 filmes do *IMDB Top 250*.
2. **Limpeza & Pré-processamento**: padronização de colunas (sinopse, nota, votos, ano, duração, gêneros).
3. **Representação dos dados**:

   * Texto: **TF-IDF** das sinopses.
   * Gêneros: **One-Hot Encoding**.
   * Atributos numéricos: **padronização** (z-score).
4. **Redução de dimensionalidade**: **TruncatedSVD** (configurável nos notebooks).
5. **Clusterização**: **KMeans (k = 5)**.
6. **Avaliação**: *Silhouette Score*, *Calinski–Harabasz* e *Davies–Bouldin*.
7. **Visualização**: projeção **3D** dos clusters com Matplotlib.

> **Por que SVD?** Para reduzir ruído/colinearidade do espaço TF‑IDF e acelerar o KMeans em alta dimensão, preservando variância relevante.

---

## ⚙️ Modelos Construídos

### 🔹 Modelo 1 — apenas sinopse

* Vetorização **TF-IDF** da sinopse.
* **TruncatedSVD** para redução de dimensionalidade.
* **KMeans (k = 5)**.

### 🔹 Modelo 2 — todas as features

* **TF-IDF** da sinopse + **One-Hot** de gêneros + **atributos numéricos padronizados** (nota, votos, ano, duração).
* **TruncatedSVD** para compactação do espaço combinado.
* **KMeans (k = 5)**.

---

## 📊 Métricas de Avaliação

| Modelo                           | Silhouette ↑ | Calinski–Harabasz ↑ | Davies–Bouldin ↓ |
| -------------------------------- | :----------: | :-----------------: | :--------------: |
| **Modelo 1 — apenas sinopse**    |   **0.13**   |         1.44        |       1.46       |
| **Modelo 2 — todas as features** |     0.07     |       **2.80**      |     **0.93**     |

**Interpretação**
O **Modelo 2** apresentou **maior coesão e separação** entre clusters (↑ Calinski–Harabasz, ↓ Davies–Bouldin) ao incorporar múltiplas variáveis além do texto. Embora o *Silhouette* tenha sido levemente menor, o ganho nas outras métricas e a melhor separação visual favorecem o **Modelo 2** como vencedor.

---

## 🔎 Insights e Exemplos de Clusters

* **Crime/Drama clássicos**
* **Fantasia/Aventura épica**
* **Sci‑fi/Ação modernos**
* **Históricos/Biográficos**
* **Thrillers psicológicos / arthouse**

> **Observação:** O **Modelo 1** tende a formar grupos **mais temáticos** (pelas palavras‑chave das sinopses), porém com **baixa coesão interna**. O **Modelo 2** produz **clusters mais equilibrados**, combinando **conteúdo** (sinopse) e **contexto** (gêneros, votos, nota, ano, duração).

---

## 🗂️ Estrutura do Projeto

```
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
```

---

## ⚙️ Como Executar

### 1) Pré‑requisitos

* **Python 3.10+**
* **pip** e **venv**
* Navegador/driver compatível, se necessário para o scraping

### 2) Criar e ativar o ambiente virtual

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux/macOS
source .venv/bin/activate
```

### 3) Instalar dependências

```bash
pip install -r requirements.txt
```

### 4) Executar os notebooks

* **Notebook 1**: scraping + KMeans (sinopse)
  Saída: `data/imdb_top250_k5_synopsis.csv`

* **Notebook 2**: KMeans (todas as features)
  Saída: `data/imdb_top250_k5_allfeatures.csv`

> As **figuras 3D** dos clusters são geradas nos próprios notebooks.

---

## 📦 Saídas Geradas

* `data/imdb_top250_raw.csv`: base bruta pós-scraping.
* `data/imdb_top250_k5_synopsis.csv`: clusters pelo Modelo 1.
* `data/imdb_top250_k5_allfeatures.csv`: clusters pelo Modelo 2.

---

## 🧪 Reprodutibilidade

* Defina `random_state` do KMeans e do SVD nos notebooks para reexecuções consistentes.
* `k` é **configurável** (experimente junto com método do **cotovelo** e *silhouette média*).

---

## 🚀 Melhorias Futuras

* Testar **embeddings semânticos** (ex.: *Sentence Transformers*).
* Explorar **DBSCAN**, **HDBSCAN** e **Spectral Clustering**.
* **Ajustar pesos** entre texto e atributos numéricos.
* **Variação de k** (métodos de *elbow* e *silhouette*).
* **Automatizar** atualização da base via **scraping agendado** (cron/Cloud Scheduler).

---

## 🧩 Limitações

* TF‑IDF captura bem termos, mas **não** relações semânticas profundas.
* KMeans pressupõe clusters esféricos; dados reais podem violar essa hipótese.
* Qualidade do scraping pode variar se a estrutura do site mudar.

---


## 🎬 Checkpoint CP2 — IMDB Top 250 (Recommender via Clusterização)

Aluno: Thiago Almança da Silva — RM558108

Disciplina: Front End & Mobile Development — 2º semestre (2025_2)
Entrega: 03/10/2025 às 23:59 via Teams
Apresentação: 03/10/2025 (todos do grupo)

## 🎯 Objetivo

Desenvolver um sistema de recomendação de filmes a partir da clusterização do IMDB Top 250 utilizando PyCaret e Streamlit, com dois métodos de interação:

Escolha de sinopse: usuário seleciona entre 3–5 sinopses anônimas → recebe recomendações do cluster correspondente.

Sinopse escrita: usuário digita uma descrição de filme → modelo classifica em cluster → recomendações geradas.

(Opcional: enriquecimento de sinopses com IA Generativa.)

## 🧭 Abordagem

Pré-processamento:

TF-IDF nas sinopses

One-Hot Encoding de gêneros

Padronização (z-score) em atributos numéricos (ano, votos, nota, duração)

Clusterização:

PyCaret (AutoML clustering)

Comparação de modelos com métricas: Silhouette, Calinski–Harabasz, Davies–Bouldin

Seleção final: melhor modelo escolhido pela combinação das métricas e testes práticos.

Recomendações: seleção dos 5 filmes mais próximos do centróide do cluster + ajuste por nota/votos.

## 🖥️ WebApp (Streamlit)

Interface simples e responsiva.

Dois métodos de recomendação (escolha ou texto).

Resultados apresentados com lista de 5 filmes recomendados.

Atualização automática com --server.runOnSave true.

## ⚙️ Como Executar
1. Pré-requisitos

Python 3.10+

Dependências listadas em requirements.txt

2. Instalar dependências
pip install -r requirements.txt

3. Executar o app

No terminal/PowerShell:

cd C:\Users\thi18\Downloads\projeto-imdb-recommender
streamlit run notebooks\webapp\app.py --server.runOnSave true


A aplicação abrirá automaticamente no navegador em http://localhost:8501/.

## 🗂️ Estrutura do Projeto
.
├── notebooks/
│   ├── 01_preprocessing.ipynb         # limpeza e preparação
│   ├── 02_pycaret_clustering.ipynb    # treino e comparação de modelos
│   └── webapp/
│       └── app.py                     # aplicação Streamlit
├── data/                              # datasets gerados (raw e clusters)
├── requirements.txt
└── README.md

## 📦 Entregáveis

PDF com nome dos integrantes + links do WebApp deployado e repositório GitHub.

WebApp publicado (Heroku, Streamlit Cloud ou similar).

Repositório GitHub com notebooks + app.

## 🚀 Melhorias Futuras

Testar embeddings semânticos (Sentence Transformers).

Explorar DBSCAN/HDBSCAN.

Ajustar pesos entre texto e atributos.

Deploy em Streamlit Cloud para compartilhamento rápido.
