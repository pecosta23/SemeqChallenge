# Objetico principal

Exercício com o intuito de identificar tipos de falhas mecânicas com base em padrões reportados por sensores do dataset "Machinery Fault Dataset" (MAFAULDA)


# Dataset

O banco de dados contém dados de sensores em um simulador de falhas mecânicas (MFS).
Foram consideradas duas classes:
Normal e Imbalance (diferentes níveis de desbalanceamento)


# Pré-processamento

1 - StandardScaler e Estatísticas:
RMS, Média, Desvio padrão, Skewness, e Kurtosis com Padronização no StandardScaler

Essas features resumem o comportamento global do dados e são utilizadas em manutenção preditiva por serem interpretáveis e confiáveis.


2 - Aplicação da Transformada Rápida de Fourier:
Extração das primeiras componentes do espectro

Falhas mecânicas costumam apresentar discrepâncias específicas nos dados, o que torna a FFT uma técnica viável no diagnóstico de falhas.


# Modelos

Random Forest Classifier:
Seguro contra o ruído dos dados
com boa performance sem causar overfitting,
interpretabilidade e generealização relativa

XGBoost Classifier:
Utilizado com features extraídas via FFT,
alta capacidade de modelagem não linear,
forte desempenho em dados tabulares,
usado em aplicações industriais


# Sobre os modelos e resultados

A escolha do modelo depende do contexto operacional enquanto o Random Forest apresentou melhor equilíbrio conseguindo generalizar mais os dados, o XGBoost mostrou-se mais sensível à detecção de falhas, sendo mais adequado para cenários onde a prioridade é evitar falhas não detectadas. 

Entretanto, essa sensibilidade veio acompanhada de um aumento significativo de falsos positivos na classe "normal", o que não seria recomendado para um modelo de produção. Por isso, o RandomFoverest se destaca por seu resultado mais equilibrado e generalizado.

Tentei modificar o pré-processamento de diversas maneiras, mas não obtive um resultado satisfatório.


# Resolução

O que eu vejo nos modelos é um potencial de crescimento bom de análise para o XGB em casos de "imbalance", ao mesmo tempo utilizaria o resultado da classe "normal" do modelo RandomForest, essa combinação acertaria os pontos críticos de ambas as classes em um mundo utópico. As discrepâncias que o XGB apresenta na classe "normal" ao meu conhecimento é uma limitação do modelo, contudo, continuarei a tentar melhorar seu desempenho.