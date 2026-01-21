# Objetico principal

Exercício com o intuito de identificar tipos de falhas mecânicas com base em padrões reportados por sensores do dataset "Machinery Fault Dataset" (MAFAULDA)


# Dataset

O banco de dados contém dados de sensores em um simulador de falhas mecânicas (MFS).
Foram consideradas duas classes:
Normal
Imbalance (diferentes níveis de desbalanceamento)


# Pré-processamento

1 - StandardScaler e Estatísticas:
RMS
Média
Desvio padrão
Skewness
Kurtosis

Padronização com StandardScaler

Essas features resumem o comportamento global do sinal e são utilizadas em manutenção preditiva por serem interpretáveis e confiáveis.


2 - Aplicação da Transformada Rápida de Fourier:
Extração das primeiras componentes do espectro

Falhas mecânicas costumam apresentar discrepâncias específicas nos dados, o que torna a FFT uma técnica viável no diagnóstico de falhas.


# Modelos
Random Forest Classifier:
Seguro contra o ruído dos dados
Boa performance sem causar overfitting
Interpretabilidade e generealização relativa

XGBoost Classifier:
Utilizado com features extraídas via FFT
Alta capacidade de modelagem não linear
Forte desempenho em dados tabulares
Amplamente usado em aplicações industriais