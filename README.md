# Impacto da Selic na inadimplência (SFN vs SNCC)

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
- https://dadosabertos.bcb.gov.br/dataset/scr_data/resource/529ce436-b070-48b8-99f2-7b07bca04ecf?inner_span=True

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
