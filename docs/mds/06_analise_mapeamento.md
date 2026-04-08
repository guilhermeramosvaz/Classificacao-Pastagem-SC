# Etapa 6 — Análise do Mapeamento

---

## 6.1. Estimativas de Área

As estimativas de área de pastagem obtidas pelas diferentes fontes apresentaram resultados distintos para o estado de Santa Catarina. A área do mapa de pastagem final, totalizou aproximadamente 1.439.037 hectares. O produto MapBiomas, que inclui a classe Pastagem(15) e a classe Campestre (12), estimou uma área de pastagem de 1.433.668 hectares, valor muito próximo ao mapa de pastagem final elaborado pelo LAPIG com diferença absoluta de cerca de 5.369 hectares (-0,37%).

---

## Dados de Saída

| Variável | Tipo de Dado |
| :---: | :---: |
| Regiões de inspeção | vetor |
| Chave de Interpretação | pdf |
| Pontos de treino | vetor |
| Malha quadriculada da área de estudo | vetor |
| Arquivos refinados por semana | raster |
| Arquivos auditados por semana | raster |
| Classificação com filtro de moda 5x5 | raster |
| Classificação Refinada | raster |
| Classificação Auditada | raster |
| Pontos visitados em campo | tabela |

---

## Scripts Relacionados

- [split_panel.js](../metodologia/Scripts/split_panel.js) — JavaScript (GEE) — Visualização de comparativo em paralelo de dados
- [mascara_estrato_amostral_Mapbiomas_GPW.js](../metodologia/Scripts/mascara_estrato_amostral_Mapbiomas_GPW.js) — JavaScript (GEE) — Visualização de comparação entre resultado e bases

Ao final dos processamentos os dados gerados são novamente inseridos no GEE para fins de visualização.

---

**Etapa anterior:** [Etapa 5 — Preparação de Dados e Refinamento](./05_preparacao_refinamento.md)  
**Próxima etapa:** [Etapa 7 — Avaliação de Acurácia](./07_avaliacao_acuracia.md)
