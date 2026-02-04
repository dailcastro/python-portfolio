
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
###4.1 Escalonamento das Variáveis

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
A PC1 representa uma dimensão latente de senioridade de carreira / trajetória profissional, capturando experiência acumulada, progressão de renda e histórico profissional.

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
