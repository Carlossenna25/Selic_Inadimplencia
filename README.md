# Impacto da Selic na inadimplência (SFN vs SNCC)

## 📌 Objetivo
Relatório em **Quarto (R)** que estima o impacto de choques contracionistas na taxa **Selic** sobre a **inadimplência** do **Sistema Financeiro Nacional (SFN)** e do **Sistema Nacional de Crédito Cooperativo (SNCC)**, com dados mensais a partir de 2012.

A identificação é feita via **VAR** e **Funções Resposta ao Impulso (IRF)** com **intervalos de confiança via bootstrap (1.000 repetições)**.

## Estrutura
- `*.qmd`: relatório principal (Quarto)
- `data/` (opcional): bases auxiliares (se aplicável)
- `scripts/` (opcional): funções e rotinas de apoio

## Fontes de dados
- Banco Central do Brasil (SGS/BCB) — séries econômicas (ex.: Selic, inadimplência, etc.)
- IBGE/SIDRA — indicadores complementares (quando aplicável)
- Sistema de Informação de Crédito - SCR

## Dados (arquivos grandes)

Este repositório **não versiona** as planilhas/dados brutos do SCR quando **> 100 MB** (limite prático do GitHub e para manter o repositório leve).

Os dados foram obtidos a partir do conjunto **SCR.Data** do Banco Central do Brasil (BCB):

- Catálogo de dados abertos (recurso SCR.Data):  
  https://dadosabertos.bcb.gov.br/dataset/scr_data/resource/529ce436-b070-48b8-99f2-7b07bca04ecf?inner_span=True

### Download dos arquivos mensais (Versão 1 do SCR.Data)

Os arquivos `.ZIP` com os dados mensais podem ser baixados via:

https://www.bcb.gov.br/pda/desig/planilha_{ANO}.zip

Substituindo `{ANO}` pelo ano correspondente. Exemplo (2025):

https://www.bcb.gov.br/pda/desig/planilha_2025.zip

### Como usar neste projeto

1. Baixe os arquivos `.ZIP` do(s) ano(s) necessário(s).
2. Extraia/organize os dados em uma pasta local (ex.: `data/raw/`).
3. Execute os scripts/notebooks do projeto para tratamento e construção das bases de análise.

---

## 📦 Metodologia
- Modelos VAR estimados com dados mensais (a partir de 2012)
- Identificação via choques exógenos na Selic
- Funções Resposta ao Impulso (IRF)
- Intervalos de confiança obtidos por **bootstrap (1.000 repetições)**
- Testes de diagnóstico: autocorrelação, heterocedasticidade e normalidade

---

## 📊 Variáveis
| Variável | Descrição |
|--------|----------|
| inad_sfn | Inadimplência – Sistema Financeiro Nacional |
| inad_sncc | Inadimplência – Sistema Nacional de Crédito Cooperativo |
| selic | Taxa Selic |
| ipca | Inflação (IPCA) |
| ibc_br | Índice de atividade econômica |
| desemprego | Taxa de desocupação |
| comprometimento | Comprometimento da renda com juros |

---

## Como reproduzir
### Pré-requisitos
- R (recomendado: versão recente)
- Quarto
- RStudio (opcional)

### Instalação de pacotes (exemplo)
Abra o R e instale os pacotes usados no relatório:

```r
install.packages(c(
  "tidyverse", "vroom", "lubridate",
  "GetBCBData", "vars", "tseries"
))
