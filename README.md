# Dashboard de Compras Públicas de Saúde — Banco de Preços em Saúde (BPS) 2020–2026

> Mini-Projeto Avaliativo — Módulo 2 (Visualização de Dados e Business Intelligence) — SCTEC/SENAI-SC
> Autor: Sérgio Fonseca Leite Junior

## 1. Objetivo do projeto

<!-- Em 3-4 linhas: o que o dashboard entrega e para quem. -->

## 2. Contextualização do problema

<!-- Por que preços/compras públicas de saúde importam. Reaproveite o contexto do BPS. -->

## 3. Fonte dos dados

- Banco de Preços em Saúde (BPS) — Ministério da Saúde
- Portal Brasileiro de Dados Abertos: https://dadosabertos.saude.gov.br/dataset/bps
- Dicionário de dados oficial: https://dadosabertos.saude.gov.br/dataset/bps/resource/0e76f527-5e7e-417d-9d0b-f46d00afb717
- Período utilizado: arquivos anuais .csv de 2020 a 2026 (7 arquivos)

## 4. Procedimentos para baixar e concatenar as bases

<!-- Passo a passo real do que você fez: onde baixou, como nomeou os arquivos, ferramenta usada para concatenar (python/excel/power query), link do script (scripts/concatenar_bases.py). -->

## 5. Tratamentos e transformações realizadas

- Leitura dos 7 arquivos anuais (2020-2026) com separador `;` e encoding UTF-8.
- Verificação de estrutura: os 7 anos apresentam schema idêntico (36 colunas,
  mesmos nomes de coluna em todos os anos) — nenhuma discrepância de nomenclatura
  ou de colunas ausentes/extras entre os anos.
- Observação relevante: o volume de registros cai de forma expressiva a partir
  de 2023. Anos 2020-2022 concentram entre ~85 mil e ~90 mil registros/ano,
  enquanto 2023-2025 apresentam entre ~28 mil e ~34 mil registros/ano, e 2026
  (parcial, ano em curso) tem 11 mil registros até o momento da coleta.
- (a completar após Sprint 2: tratamento de nulos, duplicados e tipos de dado)
- Verificação de valores nulos: identificados nulos e esperados em
  campos que não se aplicam a todo item (ex: `vl_capacidade`, `un_fornecimento`,
  `registro_anvisa`, `nu_ata`, `ds_observacao`) — mantidos como estão, pois
  representam ausência real de informação, não erro. Nenhum nulo encontrado nas
  colunas usadas nos KPIs principais (valor total, preço unitário, quantidade,
  fornecedor).
- Encontrados nulos pontuais em `no_instituicao` (8 a 95 registros por ano,
  conforme o ano), coluna usada no KPI "Instituições compradoras". Como essas
  linhas mantêm valores financeiros válidos, optou-se por preencher com o rótulo
  "Não informado" em vez de remover o registro, evitando perda de dado financeiro
  real por causa de um único campo ausente.

<!-- Encoding, nulos, duplicados, padronização de colunas, datas, valores monetários. Liste discrepâncias entre anos e como foram resolvidas (ver docs/discrepancias-entre-anos.md). -->

## 6. Descrição das principais colunas utilizadas

| Coluna | Descrição | Tipo |
| ------ | ----------- | ---- |
|        |             |      |

## 7. Definição dos KPIs e métricas

| KPI                                 | Fórmula/Lógica                 | Observação                                                    |
| ----------------------------------- | -------------------------------- | --------------------------------------------------------------- |
| Valor total registrado              | SOMA(preco_total)                |                                                                 |
| Quantidade total de itens comprados | SOMA(quantidade)                 |                                                                 |
| Número de registros de compra      | CONTAGEM(linhas)                 |                                                                 |
| Instituições compradoras          | CONTAGEM DISTINTA(instituição) |                                                                 |
| Fornecedores                        | CONTAGEM DISTINTA(fornecedor)    |                                                                 |
| Preço unitário médio ponderado   | valor total / quantidade total   | Interpretar com cautela ao filtrar produtos/unidades diferentes |

## 8. Link ou imagens do dashboard

<!-- Link público do Looker Studio ou Power BI + prints em dashboard/imagens/ -->

## 9. Principais análises e descobertas

<!-- Bullets com os achados mais relevantes por estado/instituição/produto/fornecedor/tempo. -->

## 10. Recomendações baseadas nos dados

<!-- 3-5 recomendações objetivas para gestão pública/negociação de compras. -->

## 11. Limitações identificadas

<!-- Ex: variações de preço não implicam sobrepreço automaticamente; possíveis lacunas na base; diferenças de estrutura entre anos. -->

## 12. Instruções para reprodução do projeto

```bash
# 1. Clonar o repositório
git clone https://github.com/engsergioleite/bps-saude-dashboard.git

# 2. Baixar os csv de 2020-2026 do portal BPS e salvar em data/raw/

# 3. Rodar o script de concatenação
python scripts/concatenar_bases.py

# 4. Abrir data/processed/BPS_20_26_SergioLeite.csv no Looker Studio / Power BI
```

## Vídeo de apresentação

Link: (inserir link do vídeo, hospedado no repositório ou YouTube não listado)
