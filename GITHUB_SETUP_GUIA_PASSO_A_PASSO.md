# 📖 Passo a Passo — Publicar no GitHub

## RESUMO RÁPIDO

```
1. Criar repositório no GitHub
2. Clonar para o computador
3. Organizar ficheiros localmente
4. Fazer commit e push
5. Configurar GitHub Pages
6. Publicar relatório online
```

**Tempo total:** ~15 minutos

---

## ⚙️ PRÉ-REQUISITOS

Antes de começar, certifique-se que tem:

- [x] Conta GitHub criada (github.com)
- [x] Git instalado no computador (`git --version` no terminal)
- [x] Acesso ao terminal / Linha de Comando

### Verificar se Git está instalado

```bash
git --version
# Resultado esperado: git version 2.x.x ou superior
```

Se não tiver Git, instale em:
- **Windows:** https://git-scm.com/download/win
- **Mac:** `brew install git`
- **Linux:** `sudo apt install git`

---

## 📋 PASSO 1 — CRIAR O REPOSITÓRIO NO GITHUB

### 1.1 Ir para GitHub

1. Acesse https://github.com
2. Faça login com a sua conta
3. Clique no ícone `+` (canto superior direito)
4. Selecione **"New repository"**

### 1.2 Configurar o repositório

Preencha o formulário:

```
Repository name:
  case-study-001-temperature-reconstruction

Description:
  Reconstrução de dados meteorológicos com Machine Learning.
  Estudo de caso NORZEC — 99% de precisão com 25% de lacunas.

Visibility:
  ☑ Public (para que fique visível)

Initialize this repository with:
  ☑ Add a README file (vamos substitui depois)
  ☑ Add .gitignore (Python)
  ☑ Choose a license: MIT License
```

3. Clique **"Create repository"**

✅ **Repositório criado!**

---

## 🖥️ PASSO 2 — CLONAR O REPOSITÓRIO PARA O COMPUTADOR

### 2.1 Copiar o link HTTPS

No GitHub (página do repositório novo):

```
1. Clique no botão verde "Code"
2. Copie a URL HTTPS (ex: https://github.com/seu-username/case-study-001-temperature-reconstruction.git)
```

### 2.2 Abrir o terminal

```bash
# Windows: Abra "Command Prompt" ou "PowerShell"
# Mac/Linux: Abra "Terminal"
```

### 2.3 Navegar para a pasta de trabalho

```bash
# Exemplo: criar em Documentos
cd Documents

# Ou qualquer pasta que preferir
```

### 2.4 Clonar o repositório

```bash
git clone https://github.com/seu-username/case-study-001-temperature-reconstruction.git

# Exemplo completo:
git clone https://github.com/francisconoris/case-study-001-temperature-reconstruction.git
```

Resultado esperado:

```
Cloning into 'case-study-001-temperature-reconstruction'...
remote: Enumerating objects: 4, done.
✓ Repositório clonado com sucesso!
```

### 2.5 Entrar na pasta do repositório

```bash
cd case-study-001-temperature-reconstruction
```

✅ **Repositório pronto localmente!**

---

## 📂 PASSO 3 — ORGANIZAR FICHEIROS LOCALMENTE

### 3.1 Criar a estrutura de pastas

Abra o Explorador de Ficheiros (Windows) ou Finder (Mac) e crie:

```
case-study-001-temperature-reconstruction/
│
├─ README.md                    # (já existe)
├─ LICENSE                      # (já existe)
├─ .gitignore                   # (já existe)
│
├─ data/
│  ├─ raw/
│  └─ processed/
│
├─ notebooks/
│
├─ src/
│
├─ results/
│  ├─ figures/
│  └─ metrics/
│
├─ reports/
│
└─ requirements.txt
```

### 3.2 Adicionar ficheiros principais

#### A. Substituir o README.md

1. Na pasta do repositório, abra `README.md` com editor de texto
2. **Delete todo o conteúdo**
3. **Copie o conteúdo do README que criei** (arquivo `/mnt/user-data/outputs/README.md`)
4. **Cole no ficheiro** e **guarde**

#### B. Adicionar o Relatório HTML

1. Copie o ficheiro `NORZEC_CaseStudy001_Report.html` para a pasta `reports/`
   ```bash
   # Ou manualmente: arrastar o ficheiro até reports/ no Explorador
   ```

#### C. Criar `requirements.txt`

Abra um editor de texto (Notepad, VS Code, etc.) e crie o ficheiro `requirements.txt`:

```txt
# Data & Analysis
pandas==2.1.4
numpy==1.26.3
scikit-learn==1.3.2
scipy==1.11.4

# Visualization
matplotlib==3.8.2
seaborn==0.13.0
plotly==5.18.0

# Jupyter & Notebooks
jupyter==1.0.0
jupyterlab==4.0.9
ipython==8.18.1

# Additional utilities
python-dotenv==1.0.0
```

Guarde como `requirements.txt` na raiz do repositório.

#### D. Criar `.gitignore` (se não existir)

O `.gitignore` deve estar lá automaticamente (GitHub criou). Se não tiver, crie com:

```txt
# Jupyter Notebook
.ipynb_checkpoints/
*.ipynb_checkpoints

# Python
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
env/
venv/
ENV/
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
*.egg-info/
.installed.cfg
*.egg

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Project specific
data/raw/*
!data/raw/.gitkeep
results/
.env
```

#### E. Criar ficheiros vazios estruturais

Para que as pastas apareçam no Git (mesmo sem ficheiros), crie ficheiros `.gitkeep`:

```bash
# Terminal:
touch data/raw/.gitkeep
touch data/processed/.gitkeep
touch notebooks/.gitkeep
touch src/__init__.py
touch results/.gitkeep
touch results/figures/.gitkeep
touch results/metrics/.gitkeep
```

### 3.3 Estrutura final

A pasta deve parecer assim:

```
case-study-001-temperature-reconstruction/
│
├─ README.md                         ✓ (substituído)
├─ LICENSE                           ✓ (MIT)
├─ .gitignore                        ✓ (Python)
├─ requirements.txt                  ✓ (novo)
│
├─ data/
│  ├─ raw/
│  │  └─ .gitkeep
│  └─ processed/
│     └─ .gitkeep
│
├─ notebooks/
│  └─ .gitkeep
│
├─ src/
│  └─ __init__.py
│
├─ results/
│  ├─ figures/
│  │  └─ .gitkeep
│  ├─ metrics/
│  │  └─ .gitkeep
│  └─ .gitkeep
│
└─ reports/
   └─ NORZEC_CaseStudy001_Report.html  ✓ (novo)
```

✅ **Estrutura pronta!**

---

## 🔄 PASSO 4 — FAZER COMMIT E PUSH

### 4.1 Abrir o terminal na pasta do repositório

```bash
# Se já não estiver lá:
cd case-study-001-temperature-reconstruction
```

### 4.2 Verificar status

```bash
git status

# Resultado esperado: mudanças pendentes (ficheiros vermelhos)
```

### 4.3 Adicionar todos os ficheiros

```bash
git add .

# Verifica:
git status

# Resultado: ficheiros agora em verde (staging area)
```

### 4.4 Fazer commit

```bash
git commit -m "Initial commit: Case Study #001 repository structure and documentation"
```

Resultado esperado:

```
[main xxxxxxx] Initial commit: Case Study #001 repository structure...
 X files changed, XXX insertions(+)
 create mode 100644 README.md
 create mode 100644 requirements.txt
 ...
```

### 4.5 Fazer push (enviar para GitHub)

```bash
git push origin main

# Resultado esperado:
# Enumerating objects: ...
# ✓ Tudo enviado!
```

✅ **Repositório enviado para GitHub!**

---

## 🌐 PASSO 5 — ATIVAR GITHUB PAGES

GitHub Pages permite que o relatório HTML seja visualizado online.

### 5.1 Ir às configurações do repositório

1. No GitHub (página do repositório)
2. Clique em **"Settings"** (aba no topo)
3. No menu lateral esquerdo, clique em **"Pages"**

### 5.2 Configurar GitHub Pages

1. Em **"Build and deployment"**:
   - **Source:** Selecione `Deploy from a branch`
   - **Branch:** Selecione `main`
   - **Folder:** Selecione `/ (root)`
   
2. Clique **"Save"**

### 5.3 Aguardar publicação

Espere 1-2 minutos. Verá uma mensagem verde:

```
✓ Your site is published at:
  https://seu-username.github.io/case-study-001-temperature-reconstruction/
```

Copie este URL — é o seu site publicado!

---

## 📱 PASSO 6 — ACESSAR O RELATÓRIO ONLINE

### 6.1 Ver o relatório

Abra no navegador:

```
https://seu-username.github.io/case-study-001-temperature-reconstruction/reports/NORZEC_CaseStudy001_Report.html
```

Exemplo completo:

```
https://francisconoris.github.io/case-study-001-temperature-reconstruction/reports/NORZEC_CaseStudy001_Report.html
```

✅ **Relatório publicado online!**

---

## 🎯 RESUMO DO QUE FICOU PUBLICADO

```
GitHub Repository:
  https://github.com/seu-username/case-study-001-temperature-reconstruction

Relatório HTML (online):
  https://seu-username.github.io/case-study-001-temperature-reconstruction/reports/NORZEC_CaseStudy001_Report.html

README (documentação):
  https://github.com/seu-username/case-study-001-temperature-reconstruction#readme

Código-fonte:
  https://github.com/seu-username/case-study-001-temperature-reconstruction/tree/main/src
```

---

## 🔄 PRÓXIMAS ATUALIZAÇÕES

Quando quiser adicionar mais conteúdo (notebooks, dados, etc.):

### A. Adicione os ficheiros localmente

```bash
# Copie os ficheiros para as pastas apropriadas
# Ex: colocar notebook em notebooks/
```

### B. Faça commit e push

```bash
cd case-study-001-temperature-reconstruction
git add .
git commit -m "Add: Jupyter notebooks for exploratory analysis"
git push origin main
```

### C. Repositório atualiza automaticamente

GitHub atualiza em segundos. Site também.

---

## 🛠️ TROUBLESHOOTING

### Problema: "fatal: not a git repository"

**Solução:**

```bash
# Certifique-se que está na pasta certa:
cd case-study-001-temperature-reconstruction

# Ou clone novamente
git clone https://github.com/seu-username/case-study-001-temperature-reconstruction.git
```

### Problema: "error: src refspec main does not match any"

**Solução:**

```bash
# Certifique-se que fez commit primeiro:
git status

# Se houver mudanças não commitadas:
git add .
git commit -m "mensagem"
git push origin main
```

### Problema: "Permission denied (publickey)"

**Solução:** Configure SSH ou use HTTPS com token:

```bash
# Use HTTPS com credenciais do GitHub
git clone https://seu-username:seu-token@github.com/seu-username/repo.git
```

### Problema: Relatório HTML não aparece online

**Solução:**

```bash
# Aguarde 2-3 minutos após o push
# Verificar URL (substitua "seu-username"):
https://seu-username.github.io/case-study-001-temperature-reconstruction/reports/NORZEC_CaseStudy001_Report.html

# Limpar cache do navegador (Ctrl+Shift+Delete ou Cmd+Shift+Delete)
```

---

## 📊 CHECKLIST FINAL

Antes de considerar terminado:

- [ ] Repositório criado no GitHub
- [ ] Clonado para o computador
- [ ] Estrutura de pastas criada
- [ ] README.md substituído com conteúdo correto
- [ ] requirements.txt adicionado
- [ ] NORZEC_CaseStudy001_Report.html em `reports/`
- [ ] .gitignore configurado
- [ ] Ficheiros adicionados e commitados
- [ ] Push feito para GitHub
- [ ] GitHub Pages ativado
- [ ] Relatório acessível online

✅ **PUBLICADO COM SUCESSO!**

---

## 📢 PRÓXIMO PASSO — DIVULGAÇÃO

Quando estiver tudo online, publique no LinkedIn com:

```
🔬 Case Study #001 — Reconstrução de Dados Meteorológicos

Está no ar o nosso primeiro case study público!

11 anos de dados meteorológicos, 25% de lacunas,
99% de precisão na reconstrução com Machine Learning.

→ Relatório técnico completo: [link do GitHub Pages]
→ Código-fonte aberto: [link do repositório]

Dados imperfeitos não significam decisões imperfeitas.

#NORZEC #MachineLearning #DataScience #OpenSource
#Mozambique
```

---

## 💬 DÚVIDAS?

Qualquer problema, avise. Posso ajudar com:
- Configurações Git
- Estrutura do repositório
- GitHub Pages
- Markdown no README
- Organização de ficheiros

---

**NORZEC — Matematizando Incertezas**

*Junho 2026*
