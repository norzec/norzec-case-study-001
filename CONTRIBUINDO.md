# 🤝 Contribuindo para NORZEC Case Study #001

Obrigado por considerar contribuir para este projeto! Este documento fornece diretrizes e instruções.

---

## 📋 Tipos de Contribuições Bem-vindas

### 🐛 Reportar Bugs
- Encontrou um erro no código?
- O relatório não renderiza corretamente?
- Abre uma Issue com:
  - Descrição clara do problema
  - Passos para reproduzir
  - Versão do Python e dependências
  - Screenshots se relevante

### 💡 Sugestões de Funcionalidades
- Ideias para melhorias?
- Extensões metodológicas?
- Abre uma Issue com:
  - Descrição clara da ideia
  - Caso de uso ou problema que resolve
  - Exemplos se possível

### 📚 Melhorias na Documentação
- Encontrou texto confuso?
- Quer traduzir para outro idioma?
- Faltam exemplos ou explicações?
- Submeta um Pull Request

### 🔬 Novas Análises ou Extensões
- Aplicar o método a outra localização?
- Implementar técnica alternativa (LSTM, XGBoost)?
- Adicionar validação extra?
- Submeta um Pull Request com:
  - Código bem documentado
  - Testes (se aplicável)
  - Novo notebook descrevendo a abordagem

### 🌍 Adaptações Regionais
- Dados para Moçambique, Angola, ou outra região africana?
- Comparativas entre países?
- Casos de uso específicos?
- Abra uma Issue ou Pull Request

---

## 🚀 Como Começar

### 1. Fork o Repositório

```bash
# No GitHub: clique em "Fork" (canto superior direito)
# Ou via CLI:
gh repo fork norzec-lda/case-study-001-temperature-reconstruction
```

### 2. Clone seu Fork

```bash
git clone https://github.com/SEU-USERNAME/case-study-001-temperature-reconstruction.git
cd case-study-001-temperature-reconstruction
```

### 3. Crie uma Branch

```bash
# Para feature nova:
git checkout -b feature/descricao-da-feature

# Para bug fix:
git checkout -b fix/descricao-do-bug

# Exemplo:
git checkout -b feature/adiciona-validacao-temporal
```

### 4. Faça suas Mudanças

- Edite ficheiros
- Crie notebooks
- Adicione dados
- Melhore documentação
- Sempre mantendo coerência com o projeto

### 5. Teste Localmente

```bash
# Se adicionou código Python:
python -m pytest tests/

# Se criou notebook, execute e verifique:
jupyter notebook notebooks/seu-notebook.ipynb
```

### 6. Commit com Mensagens Claras

```bash
git add .
git commit -m "Tipo: Descrição breve (máx 50 caracteres)

Descrição mais detalhada se necessário.
- Ponto 1
- Ponto 2

Closes #numero_da_issue (se aplicável)"
```

**Tipos de commit recomendados:**
- `feat:` Nova funcionalidade
- `fix:` Correção de bug
- `docs:` Documentação
- `style:` Formatação de código
- `refactor:` Refatoração sem mudança funcional
- `test:` Testes
- `chore:` Atualizações de dependências

**Exemplo:**
```bash
git commit -m "feat: Adiciona validação cruzada estratificada

- Implementa 5-fold stratified cross-validation
- Calcula desvio padrão das métricas
- Adiciona visualização de fold distribution

Closes #42"
```

### 7. Push para seu Fork

```bash
git push origin feature/descricao-da-feature
```

### 8. Abra um Pull Request

1. No GitHub, vá ao seu fork
2. Clique em "Pull Requests"
3. Clique em "New Pull Request"
4. Selecione:
   - **Base:** `norzec-lda/case-study-001-temperature-reconstruction` / `main`
   - **Compare:** `seu-fork` / `feature/sua-feature`
5. Preencha o formulário:

```markdown
## Descrição
Breve descrição do que foi mudado.

## Tipo de Mudança
- [ ] Bug fix
- [ ] Nova feature
- [ ] Melhoria na documentação
- [ ] Refatoração
- [ ] Outro:

## Como testar
Passos para validar a mudança:
1. ...
2. ...

## Checklist
- [ ] Meu código segue o estilo do projeto
- [ ] Atualizei a documentação
- [ ] Adicionei testes (se relevante)
- [ ] Todas os testes passam localmente
- [ ] Sem warnings desnecessários

## Referências
Relacionado a #issueNumber
```

---

## 📐 Padrões de Código

### Python
```python
# Imports organizados
import os
from pathlib import Path

import numpy as np
import pandas as pd
from sklearn.ensemble import RandomForestRegressor

# Docstrings em formato Google
def reconstruct_data(df: pd.DataFrame, missing_rate: float = 0.25) -> pd.DataFrame:
    """
    Reconstruct missing meteorological data using Random Forest.
    
    Args:
        df: Input DataFrame with variables
        missing_rate: Fraction of data to remove artificially (0-1)
        
    Returns:
        DataFrame with reconstructed values
        
    Raises:
        ValueError: If missing_rate not in [0, 1]
        
    Example:
        >>> df = pd.read_csv('data.csv')
        >>> reconstructed = reconstruct_data(df, missing_rate=0.25)
    """
    if not 0 <= missing_rate <= 1:
        raise ValueError("missing_rate deve estar entre 0 e 1")
    
    # Implementação...
    return df_reconstructed

# Type hints
def calculate_metrics(y_true: np.ndarray, y_pred: np.ndarray) -> dict:
    """Calculate MAE, RMSE, R²."""
    pass

# Constants em MAIÚSCULAS
RANDOM_STATE = 42
CV_FOLDS = 5
TEST_SIZE = 0.2
```

### Notebooks Jupyter
```python
# Célula 1: Imports
import pandas as pd
import numpy as np
from src.data_loader import load_data
from src.model import train_model

# Célula 2: Load Data
df = load_data('data/raw/chimoio.csv')
print(f"Shape: {df.shape}")
print(f"Missing values: {df.isnull().sum().sum()}")

# Célula 3: Analysis
# Comentários claros explicando cada passo
df_summary = df.describe()
display(df_summary)

# Célula final: Conclusões
# - Listado claro de descobertas
# - Próximos passos
```

### Markdown
```markdown
# Título Nível 1
## Título Nível 2
### Título Nível 3

**Bold** e *itálico*

- Lista com bullet
- Outro item

1. Lista numerada
2. Outro item

```python
# Bloco de código
print("Hello")
```

[Link de texto](https://exemplo.com)

| Coluna 1 | Coluna 2 |
|---|---|
| Dados | Dados |
```

---

## 📝 Documentação

### Docstrings obrigatórias em Python
```python
def funcao(param: type) -> type:
    """
    Uma linha resumida do que a função faz.
    
    Descrição mais detalhada (opcional), explicando:
    - Comportamento importante
    - Casos especiais
    
    Args:
        param: Descrição do parâmetro
        
    Returns:
        Descrição do return
        
    Raises:
        ExceptionType: Quando esta exceção é levantada
        
    Example:
        >>> resultado = funcao(valor)
        >>> print(resultado)
        valor processado
    """
```

### Comentários em código
```python
# ❌ Evite: comentários óbvios
x = 5  # Atribui 5 a x

# ✅ Faça: comentários que explicam o porquê
x = 5  # Usa 5 como threshold baseado em literature review
```

---

## 🧪 Testes

Se adicionar funcionalidade nova, inclua testes:

```python
# tests/test_model.py
import pytest
from src.model import train_model

def test_train_model_returns_estimator():
    """Test que train_model retorna um estimador sklearn."""
    X = np.random.rand(100, 5)
    y = np.random.rand(100)
    
    model = train_model(X, y)
    
    assert hasattr(model, 'predict')
    assert hasattr(model, 'score')

def test_train_model_with_missing_raises():
    """Test que função lida com dados faltantes."""
    X = np.random.rand(100, 5)
    X[0, 0] = np.nan
    y = np.random.rand(100)
    
    with pytest.raises(ValueError):
        train_model(X, y)
```

Executar:
```bash
pytest tests/ -v
```

---

## 🌍 Tradução

Se quiser traduzir documentação ou código:

### Ficheiros a traduzir
- `README.md` → `README_PT.md` (se houver versão EN)
- Comentários em código
- Docstrings
- Nomes de variáveis

### Manter coerência
- Use glossário do projeto
- Consulte traduções anteriores
- Coordene com maintainers

---

## 🔄 Processo de Review

Quando submeter Pull Request:

1. **Automated Checks**
   - GitHub Actions verifica:
     - Formatação de código
     - Linting
     - Testes

2. **Manual Review**
   - Pelo menos um maintainer revê
   - Feedback em comentários
   - Iteração se necessário

3. **Merge**
   - Aprovado e squash merged
   - Branch eliminada
   - Mencionado em CHANGELOG

---

## 📋 Checklist para Pull Request

Antes de submeter, certifique-se:

- [ ] Código segue estilo do projeto
- [ ] Adicionei docstrings/comentários
- [ ] Atualizei README se necessário
- [ ] Adicionei testes se aplicável
- [ ] Testes passam localmente (`pytest` ou equivalente)
- [ ] Sem warnings Python
- [ ] Commit messages são claras
- [ ] Nenhuma credencial ou dados sensíveis inclusos
- [ ] Imagens/gráficos são legíveis (não pixelados)

---

## 🐛 Reportar Bugs

Quando abrir uma Issue de bug:

```markdown
## Descrição do Bug
Descrição clara e breve.

## Passos para Reproduzir
1. Faça isso
2. Depois isso
3. Resultado: XXX (esperado: YYY)

## Comportamento Esperado
Descrição clara.

## Ambiente
- Python version: 3.9.2
- OS: Ubuntu 20.04
- Pandas: 1.3.0
- scikit-learn: 0.24.0

## Código Relevante
```python
# Bloco de código que causa o bug
df = pd.read_csv('data.csv')
model.fit(df)  # <- Erro aqui
```

## Screenshots
[Se aplicável]

## Logs/Tracebacks
```
Traceback (most recent call last):
  File "script.py", line 10, in <module>
    ...
ValueError: ...
```
```

---

## 💬 Código de Conduta

Esperamos que todos os contribuidores:

- ✅ Sejam respeitosos
- ✅ Forneçam feedback construtivo
- ✅ Reconheçam contribuições alheias
- ✅ Focam no problema, não na pessoa
- ✅ Aceitam crítica com abertura

---

## 🙏 Reconhecimento

Todos os contribuidores são reconhecidos em:

- `CONTRIBUTORS.md` (lista de contribuidores)
- Commits history
- Releases notes

---

## ❓ Dúvidas?

- 📧 Email: norzecmz@gmail.com
- 💬 GitHub Discussions: [link quando ativado]
- 📱 WhatsApp: wa.me/258878787963

---

**Obrigado por contribuir para NORZEC! 🚀**

*Matematizando Incertezas*
