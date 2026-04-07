# Etapa 6 — Análise do Mapeamento

> Comparação de estimativas de área de pastagem entre fontes de dados

---

## 6.1. Estimativas de Área

As estimativas de área de pastagem obtidas pelas diferentes fontes apresentaram resultados distintos para o estado de Santa Catarina.

### Comparação de Áreas

| Fonte | Área (hectares) | Classes Incluídas |
|:------|:----------------|:------------------|
| **Mapa de pastagem final (LAPIG)** | **1.439.037** | Pastagem (classificação binária refinada e auditada) |
| **MapBiomas** | 1.433.668 | Pastagem (15) + Campestre (12) |

### Diferença entre Fontes

| Métrica | Valor |
|:--------|:------|
| Diferença absoluta | ~5.369 hectares |
| Diferença relativa | **-0,37%** |

> A área do mapa de pastagem final totalizou aproximadamente **1.439.037 hectares**, valor muito próximo ao estimado pelo MapBiomas (**1.433.668 hectares**), com diferença absoluta de apenas ~5.369 hectares (-0,37%).

---

## 6.2. Interpretação

A proximidade dos valores entre o mapeamento LAPIG e o produto MapBiomas reforça a consistência metodológica do projeto, demonstrando que:

- A classificação com Random Forest a 10m de resolução (Sentinel-2) consegue capturar de forma fiel as áreas de pastagem do estado
- O processo de refinamento e auditoria manual contribuiu para um resultado final alinhado com bases de referência consolidadas
- A diferença de -0,37% está dentro de uma margem aceitável para mapeamentos em escala estadual

---

## Dados de Saída desta Etapa

| Variável | Tipo de Dado |
|:---------|:-------------|
| Classificação com filtro de moda 5×5 | Raster (classificação base) |
| Classificação Refinada | Raster (classificação beta) |
| Classificação Auditada | Raster (classificação final) |

---

## Scripts Relacionados

| Script | Linguagem | Descrição |
|:-------|:----------|:----------|
| [`split_panel.js`](../metodologia/Scripts/split_panel.js) | JavaScript (GEE) | Visualização comparativa em paralelo dos dados |
| [`mascara_estrato_amostral_Mapbiomas_GPW.js`](../metodologia/Scripts/mascara_estrato_amostral_Mapbiomas_GPW.js) | JavaScript (GEE) | Comparação entre resultado e bases de referência |

---

**Etapa anterior:** [Etapa 5 — Estratégias de Refinamento](./05_refinamento.md)  
**Próxima etapa:** [Etapa 7 — Avaliação de Acurácia](./07_avaliacao_acuracia.md)
