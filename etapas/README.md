# Etapas do Projeto — Mapeamento da Pastagem em Santa Catarina (2024)

Documentação detalhada de cada etapa do projeto de mapeamento das pastagens no estado de Santa Catarina para o ano de 2024, baseada no Relatório Técnico ATBD (Algorithm Theoretical Basis Document).

## Sumário das Etapas

| # | Etapa | Arquivo |
|:-:|:------|:--------|
| 1 | [Visão Geral e Introdução](./01_visao_geral.md) | `01_visao_geral.md` |
| 2 | [Integração de Dados de Referência](./02_integracao_dados.md) | `02_integracao_dados.md` |
| 3 | [Desenho Amostral e Inspeção Visual](./03_desenho_amostral.md) | `03_desenho_amostral.md` |
| 4 | [Processamento e Classificação](./04_processamento_classificacao.md) | `04_processamento_classificacao.md` |
| 5 | [Preparação de Dados e Refinamento](./05_preparacao_refinamento.md) | `05_preparacao_refinamento.md` |
| 6 | [Análise do Mapeamento](./06_analise_mapeamento.md) | `06_analise_mapeamento.md` |
| 7 | [Avaliação de Acurácia](./07_avaliacao_acuracia.md) | `07_avaliacao_acuracia.md` |

---

## Estrutura do Projeto

```
SC_Pasture/
├── etapas/                          ← Você está aqui
│   ├── README.md
│   ├── 01_visao_geral.md
│   ├── 02_integracao_dados.md
│   ├── 03_desenho_amostral.md
│   ├── 04_processamento_classificacao.md
│   ├── 05_preparacao_refinamento.md
│   ├── 06_analise_mapeamento.md
│   └── 07_avaliacao_acuracia.md
├── metodologia/
│   ├── README.md
│   └── Scripts/
├── Resultados/
│   ├── ATBD_MAPEAMENTO_DA_PASTAGEM_DE_SANTA_CATARINA.pdf
│   ├── Chave de Interpretação das Pastagens para o Estado de Santa Catarina.pdf
│   └── train_samples.geojson
├── imgs/
└── README.md
```

## Contexto

Este mapeamento foi realizado pela parceria entre **LAPIG/UFG**, **Remapgeo** e **Epagri**, utilizando imagens Sentinel-2A/B com 10 metros de resolução espacial, dados de referência do MapBiomas e Global Pasture Watch, e classificação supervisionada com o algoritmo Random Forest via Google Earth Engine (GEE).

## Referências

- [ATBD Completo (PDF)](../Resultados/ATBD_MAPEAMENTO_DA_PASTAGEM_DE_SANTA_CATARINA.pdf)
- [Chave de Interpretação (PDF)](../Resultados/Chave%20de%20Interpretação%20das%20Pastagens%20para%20o%20Estado%20de%20Santa%20Catarina.pdf)
- [Scripts do Projeto](../metodologia/Scripts/)
- [Metodologia](../metodologia/README.md)
- [Mapa Final — Pastagem SC](https://polianavi.github.io/pastagem_remap/)
