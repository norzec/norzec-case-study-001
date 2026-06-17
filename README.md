# NORZEC Case Study #001

## Reconstrução Inteligente de Dados Meteorológicos com Machine Learning

**NORZEC, LDA**
**Chimoio, Moçambique**
**Junho de 2026**

---

## Visão Geral

Este estudo demonstra como técnicas de Machine Learning podem ser utilizadas para reconstruir séries meteorológicas incompletas, reduzindo perdas de informação e aumentando a confiabilidade de análises climáticas, ambientais e agroclimáticas.

Utilizando dados meteorológicos da NASA POWER para Chimoio, Moçambique, simulou-se um cenário operacional real com 25% de dados ausentes. Em seguida, aplicou-se um modelo Random Forest para reconstrução das observações faltantes.

### Resultado Principal

* R² = 0.9909
* MAE = 0.25 °C
* RMSE = 0.33 °C

Os resultados indicam elevada capacidade de reconstrução da variável temperatura média, preservando a coerência física do sistema atmosférico analisado.

---

## Contexto

A indisponibilidade de dados meteorológicos é um problema recorrente em diversas regiões do mundo, especialmente em contextos com limitações de infraestrutura de monitoramento.

Falhas de sensores, interrupções operacionais e lacunas históricas comprometem:

* Estudos climáticos;
* Zoneamento agroclimático;
* Modelagem hidrológica;
* Planejamento energético;
* Avaliações de risco ambiental.

Este estudo investiga até que ponto algoritmos de Machine Learning podem recuperar informações ausentes sem comprometer a qualidade analítica dos dados.

---

## Dados Utilizados

### Fonte

NASA POWER (Prediction Of Worldwide Energy Resources)

https://power.larc.nasa.gov

### Localização

Chimoio, Moçambique

* Latitude: 19.1164° S
* Longitude: 33.4833° E

### Variáveis Utilizadas

| Variável          | Descrição                       |
| ----------------- | ------------------------------- |
| T2M               | Temperatura média               |
| T2M_MAX           | Temperatura máxima              |
| T2M_MIN           | Temperatura mínima              |
| RH2M              | Humidade relativa               |
| PRECTOTCORR       | Precipitação                    |
| WS2M              | Velocidade do vento             |
| ALLSKY_SFC_SW_DWN | Radiação solar                  |
| PS                | Pressão atmosférica             |
| T2MDEW            | Temperatura do ponto de orvalho |

---

## Metodologia

O fluxo metodológico foi composto por sete etapas:

1. Aquisição dos dados meteorológicos.
2. Controle de qualidade e pré-processamento.
3. Introdução artificial de 25% de valores ausentes.
4. Análise exploratória dos dados.
5. Treinamento de modelo Random Forest.
6. Reconstrução das observações removidas.
7. Avaliação estatística da reconstrução.

### Algoritmo

Random Forest Regressor

### Configuração

* 100 árvores
* random_state = 42
* Validação cruzada
* Avaliação por métricas de regressão

### Métricas

* Coeficiente de determinação (R²)
* Erro médio absoluto (MAE)
* Raiz do erro quadrático médio (RMSE)

---

## Principais Resultados

### Desempenho

| Métrica | Valor   |
| ------- | ------- |
| R²      | 0.9909  |
| MAE     | 0.25 °C |
| RMSE    | 0.33 °C |

### Importância das Variáveis

O modelo identificou como principais preditores:

1. Temperatura mínima (T2M_MIN)
2. Temperatura máxima (T2M_MAX)

Juntas, estas variáveis representam aproximadamente 98% da importância preditiva do modelo.

Este resultado é fisicamente consistente, uma vez que a temperatura média é fortemente condicionada pelos extremos térmicos diários.

---

## Aplicações Potenciais

A metodologia pode ser aplicada em:

### Agricultura

* Zoneamento agroclimático
* Calendários agrícolas
* Seguros paramétricos

### Recursos Hídricos

* Modelagem hidrológica
* Estudos de disponibilidade hídrica

### Energia

* Séries climáticas para energia solar
* Estudos de potencial eólico

### Saúde Pública

* Modelagem ambiental de doenças sensíveis ao clima

### Planeamento Territorial

* Avaliações de risco climático
* Infraestrutura resiliente

---

## Estrutura do Repositório

```text
norzec-case-study-001/
│
├── README.md
├── CONTRIBUINDO.md
├── LICENSE
│
├── data/
│   ├── raw/
│   │   └── nasa_power_chimoio_raw.csv
│   │
│   └── processed/
│       ├── nasa_power_chimoio_with_missing.csv
│       └── nasa_power_chimoio_reconstructed.csv
│
├── figures/
│   ├── 01_correlation_matrix.png
│   ├── 02_reconstruction_main.png
│   ├── 03_before_after_carousel.png
│   └── 04_feature_importance_carousel.png
│
├── metrics/
│   ├── metrics.csv
│   ├── descriptive_statistics.csv
│   └── feature_importance.csv
│
├── src/
│   └── criar_boletim_FINAL.py
│
└── docs/
```

---

## Visualizações

O repositório inclui:

* Matriz de correlação entre variáveis meteorológicas;
* Comparação entre dados originais e reconstruídos;
* Importância das variáveis preditoras;
* Métricas de desempenho do modelo.

---

## Reprodutibilidade

Este estudo foi desenvolvido com foco em transparência e reprodutibilidade.

Características:

* Dados públicos;
* Metodologia documentada;
* Código aberto;
* Controle de aleatoriedade;
* Métricas de validação reportadas.

---

## Referências

Breiman, L. (2001). Random Forests. Machine Learning, 45(1), 5–32.

Hastie, T., Tibshirani, R., Friedman, J. (2009). The Elements of Statistical Learning. Springer.

NASA POWER Data Access Viewer:

https://power.larc.nasa.gov

---

## Sobre a NORZEC

A NORZEC atua na interseção entre ciência de dados, inteligência climática, geotecnologias e suporte à decisão.

Áreas de atuação:

* Inteligência climática;
* Monitoramento ambiental;
* Ciência de dados geoespaciais;
* Gestão de riscos;
* Planeamento territorial.

---

## Licença

Este projeto está licenciado sob a MIT License.

Consulte o arquivo LICENSE para mais informações.

---

## Contato

NORZEC, LDA

Email: [norzecmz@gmail.com](mailto:norzecmz@gmail.com)

GitHub: https://github.com/norzec

LinkedIn: https://www.linkedin.com/company/norzec

Website institucional: em desenvolvimento

---

## Impacto

Dados incompletos não precisam resultar em decisões incompletas.

Este case study demonstra como abordagens robustas de Machine Learning podem ampliar a utilidade de séries climáticas históricas, fortalecendo aplicações em agricultura, recursos hídricos, energia e gestão de riscos em contextos de recursos limitados.

**NORZEC — Inteligência para transformar dados em decisão.**
