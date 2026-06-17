# NORZEC Case Study #001
## Reconstrução Inteligente de Dados Meteorológicos com Machine Learning

**Autores:** NORZEC, LDA  
**Data:** Junho 2026  
**Localização:** Chimoio, Moçambique  
**Fonte de Dados:** NASA POWER LARC  

---

## 📋 Resumo Executivo

Este repositório contém a análise completa e metodologia para reconstrução de séries temporais meteorológicas incompletas utilizando Machine Learning. 

**Situação:** 11 anos de dados meteorológicos com 25% de valores faltantes  
**Solução:** Random Forest + validação estatística rigorosa  
**Resultado:** 99.09% de precisão (R² = 0.9909)  

Dados incompletos **não precisam significar decisões imperfeitas.**

---

## 🎯 Contexto do Problema

Em muitos projetos científicos e operacionais na África, dados meteorológicos incompletos são uma barreira recorrente:

- Sensores quebram ou deixam de funcionar
- Interrupções no monitoramento causam lacunas temporais
- Falhas operacionais resultam em observações perdidas

Quando 25% dos dados desaparecem, a maioria dos projetos:
- Interrompe análises
- Reduz confiança em decisões
- Aumenta custos de recolha de novos dados

**NORZEC demonstra:** usando Machine Learning pragmático e validado, é possível recuperar essas informações com fidelidade suficiente para análises robustas.

---

## 📊 Dados Utilizados

### Fonte
**NASA POWER LARC** — Plataforma de dados climáticos de alta resolução espacial
- **Coordenadas:** 19.1164°S, 33.4833°E (Chimoio, Moçambique)
- **Período:** 2015–2025 (11 anos)
- **Resolução:** Dados diários agregados a mensais (80 observações)

### Variáveis
| Variável | Unidade | Tipo | Descrição |
|---|---|---|---|
| T2M | °C | Alvo | Temperatura Média Diária |
| T2M_MAX | °C | Preditor | Temperatura Máxima Diária |
| T2M_MIN | °C | Preditor | Temperatura Mínima Diária |
| RH2M | % | Preditor | Umidade Relativa |
| PRECTOTCORR | mm | Preditor | Precipitação Total Corrigida |
| WS2M | m/s | Preditor | Velocidade do Vento |
| ALLSKY_SFC_SW_DWN | W/m² | Preditor | Radiação Solar Incidente |
| PS | kPa | Preditor | Pressão Atmosférica |
| T2MDEW | °C | Preditor | Ponto de Orvalho |

---

## 🔬 Metodologia

### Abordagem em 7 Etapas

1. **Dados Originais** — Aquisição de 80 observações mensais (9 variáveis)
2. **Introdução de Falhas** — Remoção artificial de 25% (160 valores) para simular cenário real
3. **Análise Exploratória** — Estatísticas descritivas e detecção de outliers
4. **Matriz de Correlação Física** — Validação de relações entre variáveis
5. **Treinamento de Random Forest** — Modelo com 100 árvores, 5-fold CV, random_state=42
6. **Reconstrução das Lacunas** — Predição dos valores removidos
7. **Validação Estatística** — MAE, RMSE, R², distribuição de erros

### Técnicas Aplicadas

- **Algoritmo:** Random Forest (scikit-learn)
- **Validação:** 5-fold Stratified Cross-Validation
- **Métricas:** MAE, RMSE, R², Coeficiente de Gini
- **Análise de Importância:** Feature Importance (Gini)
- **Distribuição de Erros:** Histograma + normalidade

---

## 📈 Resultados

### Métricas Principais

```
R² (Coeficiente de Determinação):  0.9909 (99.09%)
MAE (Erro Médio Absoluto):         0.25°C
RMSE (Raiz do Erro Quadrático):    0.33°C
```

### Interpretação

O modelo explica **99.09% da variância** em temperatura, com:
- Erro médio inferior a **0.3°C** — fidelidade suficiente para análises climáticas
- Distribuição de erros centrada em zero — sem viés sistemático
- **1.004 registros de teste** validados — amostra robusta

### Feature Importance

| Variável | Importância (Gini) |
|---|---|
| T2M_MIN | 0.6445 (64.45%) |
| T2M_MAX | 0.3410 (34.10%) |
| T2MDEW | 0.0072 |
| PS | 0.0030 |
| WS2M | 0.0014 |
| RH2M | 0.0013 |
| ALLSKY_SFC_SW_DWN | 0.0011 |
| PRECTOTCORR | 0.0005 |

**Conclusão:** Temperatura mínima e máxima dominam, respondendo por ~98% da capacidade preditiva. Isso demonstra **coerência física** do modelo — por definição termodinâmica, a temperatura média é determinada pelos extremos diários.

---

## 🔍 Descobertas Principais

1. **Coerência Física Comprovada:** O modelo não aprendeu padrões spurious, mas capturou relações termodinâmicas reais
2. **Robustez em Dados Incompletos:** Mesmo com 25% faltando, o modelo reconstruiu com precisão excepcional
3. **Aplicação Prática:** A metodologia é transferível para outras localizações e períodos

---

## 💡 Aplicações Práticas

Este método pode ser aplicado em múltiplos contextos:

| Setor | Aplicação |
|---|---|
| 🌾 **Agricultura** | Zoneamento agroclimático, cálculo de índices de déficit hídrico |
| 🌧️ **Recursos Hídricos** | Séries de precipitação para modelagem hidrológica |
| ⚡ **Energia** | Completação de bases de geração solar/eólica |
| 🏥 **Saúde Pública** | Estudos ambientais e epidemiológicos (malária, dengue) |
| 🏗️ **Infraestrutura** | Monitoramento climático para planejamento urbano |
| 🌍 **Monitoramento Ambiental** | Reconstituição de séries históricas em observatórios |

---

## 📂 Estrutura do Repositório

```
case-study-001-temperature-reconstruction/
│
├─ README.md                          # Este ficheiro
├─ CONTRIBUINDO.md                    # Diretrizes para contribuições
├─ LICENSE                            # MIT License
│
├─ data/
│  ├─ raw/
│  │  └─ chimoio_2015_2025_raw.csv   # Dados brutos NASA POWER LARC
│  │
│  ├─ processed/
│  │  ├─ chimoio_with_missing.csv     # Dados com 25% faltantes
│  │  └─ chimoio_reconstructed.csv    # Dados após reconstrução
│  │
│  └─ README_DATA.md                  # Documentação de dados
│
├─ notebooks/
│  ├─ 01_exploratory_analysis.ipynb    # EDA + estatísticas descritivas
│  ├─ 02_missing_data_simulation.ipynb # Introdução de falhas
│  ├─ 03_random_forest_training.ipynb  # Treinamento do modelo
│  └─ 04_validation_analysis.ipynb     # Validação e análise de erros
│
├─ src/
│  ├─ __init__.py
│  ├─ data_loader.py                  # Carregamento e tratamento de dados
│  ├─ model.py                        # Definição e treinamento do Random Forest
│  ├─ validation.py                   # Cálculo de métricas e análises
│  └─ visualizations.py               # Geração de gráficos
│
├─ results/
│  ├─ figures/
│  │  ├─ correlation_matrix.png
│  │  ├─ before_after_comparison.png
│  │  ├─ feature_importance.png
│  │  └─ error_distribution.png
│  │
│  ├─ metrics/
│  │  ├─ validation_metrics.json
│  │  └─ cross_validation_scores.json
│  │
│  └─ summary.txt                     # Resumo dos resultados
│
├─ reports/
│  ├─ NORZEC_CaseStudy001_Report.html  # Relatório técnico completo (HTML)
│  └─ NORZEC_CaseStudy001_Report.pdf   # Versão em PDF
│
├─ requirements.txt                    # Dependências Python
├─ setup.py                            # Setup para instalação
│
└─ .gitignore                          # Ficheiros a ignorar no Git

```

---

## 🚀 Como Começar

### Pré-requisitos

- Python 3.8+
- pip ou conda

### Instalação

1. **Clone o repositório**
```bash
git clone https://github.com/norzec-lda/case-study-001-temperature-reconstruction.git
cd case-study-001-temperature-reconstruction
```

2. **Crie um ambiente virtual**
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate     # Windows
```

3. **Instale as dependências**
```bash
pip install -r requirements.txt
```

### Executar a Análise

1. **Jupyter Notebooks** — Execute na ordem:
```bash
jupyter notebook notebooks/01_exploratory_analysis.ipynb
jupyter notebook notebooks/02_missing_data_simulation.ipynb
jupyter notebook notebooks/03_random_forest_training.ipynb
jupyter notebook notebooks/04_validation_analysis.ipynb
```

2. **Scripts Python** — Ou execute como módulo:
```bash
python -m src.model --input data/raw/chimoio_2015_2025_raw.csv
```

3. **Ver relatório**
```bash
# Abra em navegador
open reports/NORZEC_CaseStudy001_Report.html
```

---

## 📊 Reproduzibilidade

Este estudo segue **padrões de pesquisa reproduzível:**

✅ **Dados públicos** — NASA POWER LARC (acesso aberto)  
✅ **Código aberto** — GitHub (MIT License)  
✅ **Metodologia documentada** — README + docstrings  
✅ **Random seed fixo** — `random_state=42` em todos os modelos  
✅ **Métricas completas** — MAE, RMSE, R², distribuição de erros  

### Reproduzir os Resultados

```bash
# Executar todo o pipeline
python -m src.model \
  --input data/raw/chimoio_2015_2025_raw.csv \
  --missing-rate 0.25 \
  --seed 42 \
  --output results/
```

Resultado esperado:
```
R² = 0.9909
MAE = 0.25°C
RMSE = 0.33°C
```

---

## 📚 Referências

### Datasets
- **NASA POWER LARC:** https://power.larc.nasa.gov/
- **Coordenadas:** Chimoio, Moçambique (19.1164°S, 33.4833°E)

### Metodologia
- Breiman, L. (2001). Random Forests. *Machine Learning*, 45(1), 5-32.
- Hastie, T., Tibshirani, R., & Friedman, J. (2009). *The Elements of Statistical Learning*. Springer.

### Contexto Africano
- WFP (2024). Food Security Updates — Mozambique
- FEWS NET (2024). Famine Early Warning Systems Network

---

## 👥 Autores

**NORZEC, LDA**  
📍 Chimoio, Moçambique  
📧 norzecmz@gmail.com  
🌐 norzec.github.io  
📱 wa.me/258878787963  

**Liderança:** Francisco José Noris (CEO & PhD Fellow em Engenharia Agrícola)

---

## 📄 Licença

Este projeto está licenciado sob a **MIT License** — veja `LICENSE` para detalhes.

Resumidamente: Use livremente em projetos académicos, comerciais ou pessoais. Atribua a NORZEC nos créditos.

---

## 🤝 Contribuições

Valorizamos contribuições!

1. Faça fork do repositório
2. Crie uma branch para a sua feature (`git checkout -b feature/melhoria`)
3. Commit as mudanças (`git commit -am 'Adiciona melhoria'`)
4. Push para a branch (`git push origin feature/melhoria`)
5. Abra um Pull Request

Veja `CONTRIBUINDO.md` para detalhes.

---

## ⭐ Citação

Se usar este trabalho em pesquisa ou publicações, cite como:

```bibtex
@dataset{norzec2026,
  author = {Noris, Francisco José and NORZEC, LDA},
  title = {Case Study #001: Intelligent Reconstruction of Meteorological Data with Machine Learning},
  year = {2026},
  url = {https://github.com/norzec-lda/case-study-001-temperature-reconstruction},
  note = {Chimoio, Mozambique. Data source: NASA POWER LARC}
}
```

---

## ❓ FAQ

**P: Posso usar este código para minha localização?**  
R: Sim! O código é genérico. Basta trocar o dataset pela sua localização e executar.

**P: Por que Random Forest em vez de LSTM ou outras técnicas?**  
R: Random Forest foi escolhido por: (1) robustez com dados incompletos, (2) interpretabilidade (feature importance), (3) baixa necessidade de tuning, (4) validação estatística clara.

**P: Os dados são reais ou simulados?**  
R: **100% reais**. Dados de NASA POWER LARC. Os 25% faltantes foram removidos artificialmente para simular cenários reais.

**P: Posso adaptar para outros fenómenos (precipitação, radiação)?**  
R: Sim. A metodologia é agnóstica ao domínio — funciona para qualquer variável contínua com correlação entre preditores.

---

## 📞 Suporte

- 📧 Email: norzecmz@gmail.com
- 💬 WhatsApp: wa.me/258878787963
- 🌐 Website: norzec.github.io
- 📱 Instagram: @norzec_lda
- 🔗 LinkedIn: linkedin.com/company/norzec-lda

---

## 🎯 Impacto

Este case study demonstra como Machine Learning pragmático contorna barreiras recorrentes em contextos de **recursos limitados**. Na África, dados incompletos não devem ser barreira para análises robustas.

**NORZEC — Matematizando Incertezas**

---

*Última atualização: Junho 2026*
