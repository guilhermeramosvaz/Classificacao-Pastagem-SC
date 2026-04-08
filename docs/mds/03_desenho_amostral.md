# Etapa 3 — Desenho Amostral e Inspeção Visual

---

## 3.1. Desenho Amostral

O método utiliza amostragem probabilística estratificada, em que cada classe da máscara é tratada como um estrato, garantindo representatividade e controle do erro. As proporções das classes são estimadas a partir da contagem de pixels, servindo de base para o cálculo do tamanho amostral, considerando nível de confiança de 95%, erro de 8% e p = 0,5. 

As amostras são sorteadas aleatoriamente e, após a seleção, organizadas, georreferenciadas e identificadas para as opções de interpretação. Esse delineamento, orquestrado automatizadamente via **Linguagem R** ([ver script no final da página](#scripts-relacionados)), segue uma abordagem estratificada por classes.

### Resumo do Esforço Amostral Balanceado

| Total de Amostras Geradas | Distribuídas nas 3 Classes (Aprox.) | Intérpretes Via TVI | Revisões Exigidas |
| :---: | :---: | :---: | :---: |
| **12.440 pontos** | **4.146 amostras** *(por classe)* | **8 especialistas** | **3 checagens** *(por ponto)* |

O alto número amostral e as triplas inspeções cegas por ponto demonstram um esforço deliberado para reduzir viés no processo metodológico.

> **Figura 3:** Distribuição espacial dos pontos de amostragem utilizados para validação do mapeamento de pastagens no estado de Santa Catarina.

---

## 3.2. Inspeção Visual

As amostras foram inspecionadas visualmente através da ferramenta [TVI, Temporal Visual Inspection](https://tvi.lapig.iesa.ufg.br/#/login), que possibilita a interpretação de séries históricas de imagens de satélite de forma independente. 

A série temporal assistida na tela do TVI compreendeu as janelas completas dos anos **2020, 2021, 2022, 2023 e 2024**, permitindo avaliar a integridade estável da classe e identificar mutações temporais. Para guiar os 8 intérpretes em um direcionamento visual rigoroso de padrão, toda a etapa foi alimentada pela respectiva [chave de interpretação](../Resultados/Chave%20de%20Interpretação%20das%20Pastagens%20para%20o%20Estado%20de%20Santa%20Catarina.pdf) construída para o projeto.

> **Figura 4:** Visual Temporal Inspection (TVI). Visualização da ferramenta de inspeção visual para as amostras de treinamento.

---

## Scripts Relacionados

- [amostras_treinamento_sc_remap.R](../base_dados/aplicacao/Scripts/amostras_treinamento_sc_remap.R) — R — Sorteio aleatório estratificado dos pontos de treinamento a partir da relação MapBiomas × GPW

## Dados de Saída

- [train_samples.geojson](../Resultados/train_samples.geojson) — Pontos de treinamento gerados

---

**Etapa anterior:** [Etapa 2 — Integração de Dados](./02_integracao_dados.md)  
**Próxima etapa:** [Etapa 4 — Processamento e Classificação](./04_processamento_classificacao.md)
