# analise-dados-socioambientais-emissoes
Modelagem e cruzamento de bases complexas do SEEG, INPE/MapBiomas e IBGE para extração de insights quantitativos sobre emissões de gases de efeito estufa e indicadores ambientais.
---

### Repositório 2: `analise-dados-socioambientais-emissoes`

```markdown
# 🌍 Análise de Dados Socioambientais e Emissões de GEE (Bases Públicas)

![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![SQL](https://img.shields.io/badge/SQL-Modelagem%20Relacional-lightgrey)

## 🎯 Objetivo do Projeto
Modelagem, limpeza e cruzamento de bases públicas brasileiras de grande escala para extração de *insights* quantitativos sobre a dinâmica de **emissões de Gases de Efeito Estufa (GEE)**, mudanças no uso da terra e atividade econômica regional.

O projeto busca aplicar técnicas de ciência de dados e econometria aplicada para avaliar a intensidade de carbono por setor produtivo e unidade federativa, fornecendo subsídios analíticos para estudos de transição energética e risco climático.

---

## 🗄️ Fontes de Dados Utilizadas

* **SEEG (Sistema de Estimativas de Emissões e Remoções de Gases de Efeito Estufa):** Séries históricas de emissões por setor (Agropecuária, Energia, Processos Industriais, Mudança de Uso da Terra e Resíduos).
* **INPE / MapBiomas:** Dados anuais de cobertura e uso do solo, desmatamento e recomposição florestal por bioma e estado.
* **IBGE (SIDRA / Contas Regionais):** Indicadores macroeconômicos, PIB estadual/setorial e variáveis demográficas para normalização das emissões pela atividade econômica.

---

## 🏗️ Arquitetura e Metodologia

1. **Ingestão e Limpeza (`Python`):**
   - Tratamento de arquivos CSV/XLSX volumosos com `pandas` e `numpy`, padronização de chaves geográficas (código IBGE de municípios/estados) e tratamento de valores ausentes.
2. **Armazenamento e Cruzamento (`SQL`):**
   - Estruturação de um banco de dados relacional (SQLite / PostgreSQL) para cruzar tabelas fato (emissões e área desmatada) com tabelas dimensão (território, setor econômico e PIB).
   - Criação de *queries* analíticas com *CTEs* e *Window Functions* para calcular taxas de variação anual e intensidade de emissões ($tCO_2e / \text{PIB}$).
3. **Análise Exploratória e Visualização (`Python`):**
   - Geração de séries temporais e correlações estatísticas entre expansão econômica e pressão ambiental por região.

---

## 📂 Estrutura do Repositório

```text
├── data/
│   ├── raw/                 # Dicionários de dados e amostras das bases SEEG, MapBiomas e IBGE
│   └── processed/           # Tabelas normalizadas por chave geográfica e ano
├── sql/
│   ├── schema.sql           # DDL para criação das tabelas relacionais
│   └── queries_analiticas.sql # Consultas de cruzamento entre emissões, uso da terra e PIB
├── notebooks/
│   ├── 01_limpeza_seeg_ibge.ipynb
│   └── 02_analise_exploratoria.ipynb
└── README.md
