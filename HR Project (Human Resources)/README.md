
# Segmentação de Funcionários com Aprendizado Não Supervisionado (K-Means & PCA)


## 1. Contexto e Motivação

Utilizando questionamentos diários sobre capacitações e dados dentro do RH, me perguntei:

Existem perfis latentes de funcionários quando variáveis demográficas, financeiras e comportamentais são analisadas simultaneamente?

A motivação é compreender a estrutura interna e a heterogeneidade da força de trabalho, utilizando técnicas de aprendizado não supervisionado, especialmente úteis quando não há uma variável-alvo explícita. Ademais, é também entender como uma empresa funciona e se essas abordagens gerariam cursos e capacitações específicas para cada tipo de funcionário

## 2. Conjunto de Dados e Seleção de Variáveis

O conjunto de dados contém informações demográficas, econômicas e comportamentais sobre os funcionários.
As seguintes variáveis foram selecionadas para a análise de Machine Learning, a EDA foram utilizadas as mais importantes para a análise em questão.

Age – idade do funcionário

MonthlyIncome – renda mensal

NumCompaniesWorked – número de empresas anteriores

JobSatisfaction – satisfação no trabalho (autoavaliada)

WorkLifeBalance – percepção de equilíbrio entre vida pessoal e profissional

Essas variáveis foram escolhidas intencionalmente para representar dimensões conceituais distintas:

Trajetória de carreira
Status econômico
Mobilidade profissional
Bem-estar subjetivo

## 3. Análise Exploratória dos Dados (EDA)

A fase exploratória incluiu:

Estatísticas descritivas (média, desvio padrão, amplitude)
Análise de distribuição por meio de boxplots
Análise de correlação

A EDA não teve como objetivo inferência causal, mas sim compreender a estrutura dos dados, sua dispersão e possíveis limitações.

## 4. Pré-processamento dos Dados
### 4.1 Escalonamento das Variáveis

Como o K-Means depende da distância Euclidiana, todas as variáveis foram padronizadas utilizando normalização Z-score:

z = (x − μ) / σ

Isso garante que:
Todas as variáveis contribuam igualmente para o processo de clusterização
Nenhuma variável domine o cálculo de distância apenas por sua escala

## 5. Clusterização com K-Means
### 5.1 Escolha do Número de Clusters

O número de clusters foi definido com base em:

Método do Cotovelo (Inércia): avalia a redução da variância intra-cluster
Silhouette Score: mede coesão e separação entre clusters

Ambos os critérios indicaram k = 3 como um compromisso adequado entre interpretabilidade e estrutura.

### 5.2 Ajuste do Modelo

O K-Means foi ajustado no espaço de variáveis padronizadas, com múltiplas inicializações para reduzir a sensibilidade à escolha inicial dos centroides.

Cada funcionário foi atribuído a um dos três clusters, criando uma nova variável categórica (Cluster).

# 6. Interpretação dos Clusters (Análise Central)

A interpretação dos clusters foi realizada com base nas médias padronizadas das variáveis originais, e não nas projeções da PCA.

Como as variáveis estão padronizadas:

Valores positivos indicam níveis acima da média
Valores negativos indicam níveis abaixo da média

Essa abordagem permite a caracterização objetiva de cada cluster com base nas variáveis originais, preservando a interpretabilidade.

## 7. Análise de Componentes Principais (PCA)
### 7.1 Objetivo da PCA

A PCA foi aplicada exclusivamente para fins de visualização, não sendo utilizada para clusterização ou tomada de decisão.

Os dois primeiros componentes principais explicam aproximadamente:

PC1 ≈ 33%
PC2 ≈ 20%

Total ≈ 53% da variância

Isso indica que a estrutura dos dados é intrinsecamente multidimensional, limitando o poder explicativo de projeções em duas dimensões.

### 7.2 Interpretação dos Loadings da PCA

Para interpretar adequadamente os resultados da PCA, foram analisados os loadings das variáveis.

PC1 — Dimensão de Senioridade de Carreira

A PC1 é majoritariamente influenciada por:

Age (0.66)
MonthlyIncome (0.60)
NumCompaniesWorked (0.44)
Variáveis comportamentais contribuem minimamente.

Interpretação:
A PC1 representa uma dimensão latente de senioridade de carreira/trajetória profissional, capturando experiência acumulada, progressão de renda e histórico profissional.

PC2 — Dimensão de Trade-off Comportamental

A PC2 é dominada por variáveis comportamentais:

JobSatisfaction (+0.77)
WorkLifeBalance (−0.61)

Os sinais opostos indicam um trade-off, e não uma escala unidimensional de bem-estar.

Interpretação:
A PC2 reflete uma tensão comportamental entre satisfação no trabalho e percepção de equilíbrio vida-trabalho.

### 7.3 Papel da PCA neste Projeto

A PCA é utilizada estritamente como ferramenta de visualização para projetar os clusters em duas dimensões.

As definições e interpretações dos clusters baseiam-se nos perfis das variáveis padronizadas, garantindo rigor metodológico e evitando interpretações excessivas de projeções de baixa dimensionalidade.

8. Considerações Finais

Este projeto demonstra como técnicas de aprendizado não supervisionado podem ser aplicadas a dados de RH para revelar perfis latentes de funcionários, mantendo rigor estatístico.

Principais aprendizados:

Segmentações relevantes podem emergir sem tarefas de previsão
Variáveis comportamentais adicionam nuances críticas além de fatores demográficos e financeiros
Análise de Machine Learning
Python
Estatística
Análise de Dados.

A PCA deve apoiar a interpretação, e não substituí-la

[EN]

# Employee Segmentation with Unsupervised Learning (K-Means & PCA)
## 1. Context and Motivation

Using daily questions about training and data within HR, I asked myself:

Are there latent employee profiles when demographic, financial, and behavioral variables are analyzed simultaneously?

The motivation is to understand the internal structure and heterogeneity of the workforce using unsupervised learning techniques, which are especially useful when no explicit target variable is available. Additionally, it is also about understanding how a company operates and whether these approaches would generate specific courses and training programs for each type of employee.

## 2. Dataset and Feature Selection

The dataset contains demographic, economic, and behavioral information about employees.
The following variables were selected for the Machine Learning analysis, while the EDA used the most important features for the analysis in question.

Age – employee age
MonthlyIncome – monthly salary
NumCompaniesWorked – number of previous employers
JobSatisfaction – self-reported job satisfaction
WorkLifeBalance – perceived work-life balance

These variables were intentionally chosen to represent distinct conceptual dimensions:

Career trajectory
Economic status
Professional mobility
Subjective well-being

## 3. Exploratory Data Analysis (EDA)

The exploratory phase included:

Descriptive statistics (mean, standard deviation, range)
Distribution analysis via boxplots
Correlation analysis

The EDA did not aim for causal inference, but rather to understand the data structure, its dispersion, and potential limitations.

## 4. Data Preprocessing
### 4.1 Feature Scaling

Since K-Means relies on Euclidean distance, all variables were standardized using Z-score normalization:

z = (x − μ) / σ

This ensures that:

All features contribute equally to the clustering process

No variable dominates the distance calculation solely due to scale

## 5. K-Means Clustering
### 5.1 Choosing the Number of Clusters

The number of clusters was defined based on:

Elbow Method (Inertia): evaluates the reduction of within-cluster variance
Silhouette Score: measures cluster cohesion and separation

Both criteria suggested k = 3 as a reasonable compromise between interpretability and structure.

### 5.2 Model Fitting

K-Means was fitted on the standardized feature space, with multiple initializations to reduce sensitivity to centroid initialization.

Each employee was assigned to one of the three clusters, creating a new categorical variable (Cluster).

## 6. Cluster Interpretation (Core Analysis)

Cluster interpretation was performed using standardized feature means, not PCA projections.

Since features are standardized:

Positive values indicate above-average levels
Negative values indicate below-average levels

This approach allows objective profiling of each cluster based on the original variables, preserving interpretability.

## 7. Principal Component Analysis (PCA)
### 7.1 Purpose of PCA

PCA was applied exclusively for visualization purposes, not for clustering or decision-making.

The first two principal components explain approximately:

PC1 ≈ 33%
PC2 ≈ 20%

Total ≈ 53% of the variance

This indicates that the data structure is intrinsically multidimensional, limiting the explanatory power of 2D projections.

### 7.2 Interpretation of PCA Loadings

To properly interpret PCA results, feature loadings were analyzed.

PC1 — Career Seniority Dimension

PC1 is primarily driven by:

Age (0.66)
MonthlyIncome (0.60)
NumCompaniesWorked (0.44)

Behavioral variables contribute minimally.

Interpretation:
PC1 represents a latent career seniority / professional trajectory dimension, capturing accumulated experience, income progression, and professional history.

PC2 — Behavioral Trade-off Dimension

PC2 is dominated by behavioral variables:

JobSatisfaction (+0.77)
WorkLifeBalance (−0.61)

The opposite signs indicate a trade-off, not a unidimensional well-being scale.

Interpretation:
PC2 reflects a behavioral tension between job satisfaction and perceived work-life balance.

### 7.3 Role of PCA in This Project

PCA is used strictly as a visualization tool to project clusters into two dimensions.

Cluster definitions and interpretations rely on standardized feature profiles, ensuring methodological rigor and avoiding overinterpretation of low-dimensional projections.

## 8. Final Remarks

This project demonstrates how unsupervised learning techniques can be applied to HR data to reveal latent employee profiles while maintaining statistical rigor.

Key takeaways:

Meaningful segmentation can emerge without prediction tasks
Behavioral variables add critical nuance beyond demographic and financial factors
Machine Learning Analysis
Python
Statistics
Data Analysis
PCA should support interpretation, not replace it
