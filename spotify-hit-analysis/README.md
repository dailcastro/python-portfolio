# Spotify Hit Analysis


## Português (PT-BR) -- ## English below (EN)

Este projeto tem como objetivo analisar quais características numéricas do áudio estão associadas a músicas que se tornam hits, utilizando dados do Spotify.
A proposta foi investigar o fenômeno musical a partir de atributos técnicos do som, sem considerar informações externas como nome do artista, popularidade prévia, marketing ou identidade visual, além de outras variáveis textuais.

O foco principal do projeto é aprendizado, interpretação estatística e prática em Machine Learning, utilizando Python.

### Análise Exploratória dos Dados

Antes do ajuste do modelo, foi realizada uma análise exploratória dos dados com intuito de entender e adentrar mais acerca das variáveis trabalhadas do banco de dados. O objetivo foi compreender as características, entender a distribuição das variáveis numéricas, entender as correlações e o comportamento dos atributos musicais. Entre as variáveis analisadas estão danceability, loudness, energy, valence, tempo e acousticness, que representam aspectos físicos e perceptivos do som, como intensidade, ritmo, presença de voz e características acústicas das faixas.

### Modelagem

A variável hit foi criada a partir da popularidade, sendo binária, ou seja, "hit" = 1 e "não-hit" = 0. Por isso, a escolha da Regressão Logística, a qual nos fornece métricas para avaliação binária e torna-se mais interpretável de modo geral, seja estatisticamente falando ou não.

Etapas principais:

-Separação dos dados em treino e teste com estratificação da variável resposta
-Padronização das variáveis numéricas (StandardScaler) --> Basicamente aquele cálculo de (X-Média) / (desvio-padrão)
-Ajuste do modelo com class_weight="balanced" para lidar com o desbalanceamento entre hits e não-hits
-Análise dos coeficientes e odds ratios

### Multicolinearidade e VIF

Durante a análise, foi identificado que diversas variáveis apresentam alta correlação entre si, o que resultou em valores elevados de VIF (Variance Inflation Factor). Do ponto de vista estatístico, VIFs elevados indicam a presença de multicolinearidade, a qual pode inflar as variâncias dos coeficientes e dificultar uma inferência causal isolada. No entanto, neste projeto, a decisão de manter as variáveis, mesmo com VIF alto, foi tomada de forma consciente. Isso se deve ao fato de que as features representam diferentes dimensões do som, mas são naturalmente correlacionadas, como ocorre, por exemplo, entre loudness e energy. A remoção de variáveis centrais como energy ou loudness comprometeria a interpretação semântica e musical do fenômeno analisado. Além disso, o objetivo do estudo não foi a otimização da performance preditiva nem a realização de inferência causal estrita, mas sim a compreensão do comportamento conjunto das características musicais. Dessa forma, priorizou-se a interpretação e o contexto musical em detrimento de critérios técnicos isolados.

### Interpretação do resultado

Os coeficientes do modelo representam o efeito das variáveis no log-odds de uma música se tornar um hit, considerando todas as features previamente padronizadas. A análise dos resultados indica que loudness apresentou uma forte associação positiva com o sucesso, enquanto danceability também demonstrou um impacto relevante. Por outro lado, variáveis com coeficientes negativos contribuem para explicar a diversidade de estilos musicais, reforçando a ideia de que não existe uma única fórmula para o sucesso comercial. É importante destacar que o modelo não estabelece relações de causalidade e que há inúmeros fatores não observáveis — como estratégias de marketing, timing de lançamento, popularidade do artista e aspectos culturais — que exercem influência significativa sobre o sucesso de uma música.


## English (EN)

This project aims to analyze which numerical audio characteristics are associated with songs that become hits, using Spotify data. The proposal is to investigate the musical phenomenon through technical sound attributes, without considering external information such as artist name, prior popularity, marketing, visual identity, or other textual variables.

The main focus of the project is learning, statistical interpretation, and hands-on practice in Machine Learning, using Python.

### Exploratory Data Analysis

Before fitting the model, an exploratory data analysis was conducted in order to better understand the variables in the dataset. The goal was to examine the characteristics of the data, understand the distribution of numerical variables, analyze correlations, and observe the behavior of musical attributes. Among the analyzed variables are danceability, loudness, energy, valence, tempo, and acousticness, which represent physical and perceptual aspects of sound such as intensity, rhythm, vocal presence, and acoustic properties of the tracks.

### Modeling

The hit variable was created based on popularity and defined as binary, where “hit” = 1 and “non-hit” = 0. Therefore, Logistic Regression was chosen, as it provides appropriate metrics for binary classification and is generally more interpretable, both from a statistical perspective and in practical terms.

Main steps:

-Splitting the data into training and test sets with stratification of the target variable
-Standardization of numerical variables (StandardScaler), essentially applying the transformation (X − mean) / standard deviation
-Model fitting with class_weight="balanced" to handle class imbalance between hits and non-hits
-Analysis of coefficients and odds ratios

### Multicollinearity and VIF

During the analysis, it was identified that several variables exhibit high correlation with each other, resulting in elevated Variance Inflation Factor (VIF) values. From a classical statistical standpoint, high VIF values indicate the presence of multicollinearity, which can inflate coefficient variances and make isolated causal inference more difficult. However, in this project, the decision to retain the variables despite high VIF values was made consciously. This is because the features represent different dimensions of sound that are naturally correlated, as is the case with loudness and energy. Removing core variables such as energy or loudness would compromise the semantic and musical interpretation of the phenomenon under analysis. Moreover, the objective of the study was not to optimize predictive performance nor to perform strict causal inference, but rather to understand the joint behavior of musical characteristics. Therefore, interpretation and musical context were prioritized over isolated technical criteria.

### Interpretation of the Results

The model coefficients represent the effect of each variable on the log-odds of a song becoming a hit, considering that all features were previously standardized. The results indicate that loudness shows a strong positive association with success, while danceability also demonstrates a relevant impact. On the other hand, variables with negative coefficients help explain the diversity of musical styles, reinforcing the idea that there is no single formula for commercial success. It is important to emphasize that the model does not establish causality and that many unobservable factors—such as marketing strategies, release timing, artist popularity, and cultural aspects—play a significant role in determining the success of a song.
