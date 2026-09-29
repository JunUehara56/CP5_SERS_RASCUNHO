# Checkpoint 2 – Aplicações de Machine Learning para dados de energia

Projeto desenvolvido para a disciplina de **Soluções em Energias Renováveis e Sustentáveis (SERS)**, do curso de **Ciência da Computação da FIAP**.

O repositório reúne as atividades do **Checkpoint 2**, utilizando técnicas de Machine Learning aplicadas a dados de estabilidade de redes elétricas.

O projeto utiliza como base o conjunto de dados **Electrical Grid Stability Simulated Data**, disponibilizado pela **UCI Machine Learning Repository**.

Fonte dos dados: [Electrical Grid Stability Simulated Data – UCI](https://archive.ics.uci.edu/dataset/471/electrical+grid+stability+simulated+data)

## Integrantes

- **Tommaso da C. Nagliatti** — RM 572147
- **Arthur Maziviero Faria** — RM 573928
- **Jun Uehara** — RM 570537
- **Felipe de Souza Gallo** — RM 569680
- **Matheus Martins Lacerda** — RM 570843
- **Roberson Reguero Luiz Junior** — RM 573031

## Estrutura do repositório

```text
CP5_SERS/
│
├── README.md
├── dados/
│   └── Data_for_UCI_named.csv
├── parte_1_classificacao/
│   └── classificacao_estabilidade.ipynb
└── parte_2_regressao/
    └── regressao_estabilidade.ipynb
````

# 1. Classificação

Arquivo:

```text
classificacao_estabilidade.ipynb
```

Nesta etapa foi desenvolvido um modelo de classificação utilizando **Regressão Logística** para prever a condição de estabilidade da rede elétrica.

A variável `stabf` foi utilizada como variável target, representando as classes de estabilidade da rede.

Foram realizadas etapas como:

* carregamento e inspeção dos dados;
* análise das variáveis;
* preparação dos dados;
* separação dos dados em treino e teste;
* treinamento do modelo;
* geração das previsões;
* avaliação dos resultados;
* análise da matriz de confusão;
* interpretação dos resultados.

# 2. Regressão

Arquivo:

```text
regressao_estabilidade.ipynb
```

Nesta etapa foram desenvolvidos dois modelos de **Regressão Linear** para prever o valor numérico da variável `stab`.

## Modelo 1 - Cinco variáveis com maior correlação

O primeiro modelo utilizou as cinco variáveis que apresentaram maior correlação absoluta com `stab`:

* `g3`
* `g2`
* `tau2`
* `g1`
* `tau3`

Foram utilizados os dados separados em conjuntos de treinamento e teste, com 80% dos registros para treinamento e 20% para teste.

O modelo apresentou os seguintes resultados:

* **R²:** 0,401770
* **MAE:** 0,023310
* **MSE:** 0,000811

## Modelo 2 - Variáveis `tau` e `g`

O segundo modelo utilizou todas as variáveis cujos nomes começam com `tau` ou `g`:

* `tau1`
* `tau2`
* `tau3`
* `tau4`
* `g1`
* `g2`
* `g3`
* `g4`

O modelo também foi treinado e avaliado utilizando a mesma divisão dos dados em treinamento e teste.

O modelo apresentou os seguintes resultados:

* **R²:** 0,645229
* **MAE:** 0,017553
* **MSE:** 0,000481

## Comparação dos modelos

| Modelo   | Variáveis utilizadas                                   |       R² |      MAE |      MSE |
| -------- | ------------------------------------------------------ | -------: | -------: | -------: |
| Modelo 1 | `g3`, `g2`, `tau2`, `g1`, `tau3`                       | 0,401770 | 0,023310 | 0,000811 |
| Modelo 2 | `tau1`, `tau2`, `tau3`, `tau4`, `g1`, `g2`, `g3`, `g4` | 0,645229 | 0,017553 | 0,000481 |

A comparação dos modelos foi realizada utilizando as métricas **R², MAE e MSE**, conforme solicitado na atividade.

Os resultados mostram que a utilização de todas as variáveis iniciadas por `tau` ou `g` apresentou melhor desempenho nas três métricas analisadas.

## Análise das variáveis

Para a seleção das cinco variáveis utilizadas no primeiro modelo, foi calculada a correlação das variáveis numéricas com `stab`.

As cinco variáveis com maior correlação absoluta foram:

* `g3`: 0,308235
* `g2`: 0,293601
* `tau2`: 0,290975
* `g1`: 0,282774
* `tau3`: 0,280700

Também foram gerados gráficos de dispersão para visualizar a relação entre cada uma dessas variáveis e `stab`.

## Conclusão da regressão

A comparação dos resultados permitiu analisar o impacto da seleção das variáveis sobre o desempenho dos modelos.

O Modelo 1, utilizando apenas as cinco variáveis com maior correlação absoluta, apresentou R² de **0,401770**.

Já o Modelo 2, utilizando todas as variáveis iniciadas por `tau` ou `g`, apresentou R² de **0,645229**, além de valores menores de MAE e MSE.

Dessa forma, a utilização do conjunto mais amplo de variáveis resultou em uma melhoria nas métricas de avaliação utilizadas.
