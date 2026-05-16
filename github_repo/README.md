# 🏪 Melhores Compras – Centro de Retirada Automatizado

> Projeto desenvolvido para o Challenge FIAP × Mater Dei | 2TSCO | Fase 6 – Entrega Final (Sprint 4)

---

## 📋 Sobre o Projeto

A **Melhores Compras** enfrenta falhas recorrentes de entrega no interior do estado de São Paulo. Este projeto propõe uma solução baseada em **Inteligência Artificial** para automatizar e tornar mais seguro o processo de retirada de encomendas, combinando duas frentes:

1. **Clusterização Geográfica (K-Means)** — identifica os 5 pontos ideais para instalação de Centros de Distribuição com base em 653 ocorrências de falhas de entrega mapeadas por geolocalização.
2. **Reconhecimento Facial (OpenCV)** — verifica a identidade do destinatário no momento da retirada, garantindo que somente a pessoa correta retire a encomenda.

---

## 📁 Estrutura do Repositório

```
melhores-compras-centro-retirada/
│
├── atividade1_reconhecimento_FINAL.ipynb   # Notebook: Reconhecimento Facial
├── atividade2_clusterizacao_FINAL.ipynb    # Notebook: Clusterização K-Means
│
├── Fiap On - Fase 6 - Geolocalização Dataset - Asset.csv  # Dataset original
├── resumo_clusters.csv                     # Resumo dos 5 clusters gerados
│
├── resultado_reconhecimento.png            # Resultado visual do reconhecimento facial
├── matriz_distancias.png                   # Matriz de distâncias euclidianas
├── mapa_clusters.png                       # Mapa geográfico dos 5 clusters
├── valor_por_cluster.png                   # Gráfico de valor por centro de distribuição
├── elbow_silhouette.png                    # Gráfico Elbow + Silhouette
├── eda_logistica.png                       # Análise exploratória dos dados
│
├── zip_fotos/imagens/                      # Fotos para treino e teste do reconhecimento
│   ├── TomHolland/
│   ├── WillSmith/
│   ├── Neymar/
│   ├── Pele/
│   └── DS/
│
├── requirements.txt                        # Dependências do projeto
└── README.md                               # Este arquivo
```

---

## 🚀 Como Executar

### Pré-requisitos

- Python 3.8+
- Jupyter Notebook ou Google Colab

### 1. Clonar o repositório

```bash
git clone https://github.com/<seu-usuario>/melhores-compras-centro-retirada.git
cd melhores-compras-centro-retirada
```

### 2. Instalar as dependências

```bash
pip install -r requirements.txt
```

### 3. Executar os notebooks

Abra o Jupyter Notebook ou faça upload no Google Colab:

```bash
jupyter notebook
```

Execute na ordem:
1. `atividade1_reconhecimento_FINAL.ipynb`
2. `atividade2_clusterizacao_FINAL.ipynb`

> ⚠️ Certifique-se de que a pasta `zip_fotos/imagens/` e o arquivo CSV estão no mesmo diretório que os notebooks antes de executar.

---

## 🧠 Atividade 1 – Reconhecimento Facial

### Objetivo
Demonstrar a viabilidade de um sistema de reconhecimento facial automatizado para os centros de retirada.

### Algoritmo
Pipeline em dois estágios com OpenCV (sem redes neurais profundas):

| Etapa | Técnica |
|-------|---------|
| Detecção de face | Haar Cascade (`haarcascade_frontalface_default.xml`) |
| Extração de features | HOG (Histogram of Oriented Gradients) + Histograma HSV |
| Classificação | Distância Euclidiana (menor distância = identidade reconhecida) |

### Estratégia de Treino (Few-Shot Augmentation)
- 4 fotos por pessoa para treino, 1 foto para teste
- Para pessoas com poucas fotos reais, foram geradas variações sintéticas: brilho, contraste, rotação e espelho horizontal

### Resultado

| Métrica | Valor |
|---------|-------|
| Acurácia | **100%** |
| Pessoas testadas | 5 (Tom Holland, Will Smith, Neymar, Pelé, DS) |
| Identificações corretas | 5/5 |

---

## 📍 Atividade 2 – Clusterização Geográfica

### Objetivo
Determinar o número e a localização ideal dos centros de retirada com base na distribuição das falhas de entrega.

### Dataset
- **Arquivo:** `Fiap On - Fase 6 - Geolocalização Dataset - Asset.csv`
- **Registros:** 653
- **Colunas:** `latitude`, `longitude`, `price`

### Algoritmo: K-Means

| Parâmetro | Valor |
|-----------|-------|
| K (clusters) | **5** |
| Seleção do K | Método do Cotovelo (Elbow) + Coeficiente de Silhouette |
| Normalização | StandardScaler |
| Seed | 42 |

### Resultado dos 5 Centros de Distribuição

| Centro | Entregas | Valor Total | % do Total |
|--------|----------|-------------|------------|
| CD 00 | 137 | R$ 8.793,54 | 21,4% |
| CD 01 | 115 | R$ 7.426,35 | 18,0% |
| CD 02 | 108 | R$ 7.012,28 | 17,0% |
| CD 03 | 129 | R$ 7.595,52 | 18,4% |
| CD 04 | 164 | R$ 10.356,12 | 25,1% |
| **Total** | **653** | **R$ 41.183,81** | **100%** |

---

## 🛠️ Tecnologias Utilizadas

| Biblioteca | Uso |
|------------|-----|
| `opencv-python` | Detecção de face (Haar Cascade) |
| `numpy` | Operações vetoriais e cálculo de distâncias |
| `pandas` | Carregamento e tratamento do dataset |
| `scikit-learn` | K-Means, StandardScaler, Silhouette Score |
| `matplotlib` | Visualizações e gráficos |
| `Pillow` | Augmentação sintética de imagens |
| `kneed` | Detecção automática do cotovelo (Elbow Method) |

---

## 👥 Integrantes do Grupo

| Nome | RM |
|------|----|
| [Nome 1] | [RM] |
| [Nome 2] | [RM] |
| [Nome 3] | [RM] |
| [Nome 4] | [RM] |

---

## 🎓 Informações Acadêmicas

- **Instituição:** FIAP × Mater Dei
- **Curso:** 2TSCO
- **Disciplina:** Enterprise Challenge
- **Sprint:** 4 – Entrega Final (Fase 6)
- **Ano:** 2025

---

## 📺 Vídeo Pitch

▶️ [Assista ao pitch no YouTube](<link-do-youtube>)
