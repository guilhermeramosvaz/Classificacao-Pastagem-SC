# Análise do Mapeamento

---
![split_panel_gif](../base_dados/images/splt_pnl.gif)

---

## Estimativas de Área

As estimativas de área de pastagem obtidas pelas diferentes fontes apresentaram resultados distintos para o estado de Santa Catarina. Enquanto o produto MapBiomas (que inclui a 'Classe Pastagem-15' e 'Classe Campestre-12') foi usado como *baseline*, o mapeamento final do LAPIG produziu as seguintes consolidações:

| Produto Cartográfico | Área Final Mapeada (Hectares) | Diferença (%) |
| :--- | :---: | :---: |
| **Mapeamento LAPIG (Total Final)** | **1.439.037 ha** | Base |
| **Padrão MapBiomas (Classes 12 + 15)** | **1.433.668 ha** | **- 0,37% (- 5.369 ha)** |

Como a diferença absoluta foi de margem muito estreita (menos de 0,5%), isso valida estatisticamente o volume territorial de pastagens descoberto. Ambos os dados são espacializados nas frentes comparativas do [script de visualização GEE no rodapé da página.](#scripts-relacionados)

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

- [split_panel.js](https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/split_panel.js) — JavaScript (GEE) — Visualização de comparativo em paralelo de dados
- [mascara_estrato_amostral_Mapbiomas_GPW.js](https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/mascara_estrato_amostral_Mapbiomas_GPW.js) — JavaScript (GEE) — Visualização de comparação entre resultado e bases

Ao final dos processamentos os dados gerados são novamente inseridos no GEE para fins de visualização.

---

**Etapa anterior:** [Preparação de Dados e Refinamento](./preparacao_refinamento.md)  
**Próxima etapa:** [Avaliação de Acurácia](./avaliacao_acuracia.md)
