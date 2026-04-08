# Etapa 3 — Desenho Amostral e Inspeção Visual

---

## 3.1. Desenho Amostral

O método utiliza amostragem probabilística estratificada, em que cada classe da máscara é tratada como um estrato, garantindo representatividade e controle do erro. As proporções das classes são estimadas a partir da contagem de pixels, servindo de base para o cálculo do tamanho amostral, considerando nível de confiança de 95%, erro de 8% e p = 0,5. As amostras são então sorteadas aleatoriamente dentro de cada estrato, assegurando independência espacial e ausência de viés. Após a seleção, os pontos são organizados, georreferenciados e identificados, sendo preparados para as etapas de interpretação, treinamento e validação. Foram geradas 12.440 amostras de treinamento, distribuídas de forma probabilística ao longo de todo o território estadual. O delineamento segue uma abordagem estratificada por classes, garantindo representatividade espacial e equilíbrio amostral entre os alvos de classificação. Nesse contexto, cada classe possui aproximadamente 4.146 amostras, o que indica um esforço deliberado de balanceamento para reduzir vieses no processo de modelagem.

> **Figura 3:** Distribuição espacial dos pontos de amostragem utilizados para validação do mapeamento de pastagens no estado de Santa Catarina.

---

## 3.2. Inspeção Visual

As amostras foram inspecionadas visualmente por especialistas através da ferramenta [TVI, Temporal Visual Inspection](https://tvi.lapig.iesa.ufg.br/#/login), que possibilita a interpretação de séries históricas de imagens de satélite de forma independente (MATOS, et al). Cada ponto recebeu 3 inspeções de especialistas diferentes para garantir a confiabilidade do dado de treinamento. Os intérpretes analisaram séries históricas de imagens de satélite de forma independente. A série temporal utilizada nas inspeções compreendeu imagens dos anos 2020, 2021, 2022, 2023 e 2024, permitindo avaliar a estabilidade temporal da classe atribuída ao ponto e identificar eventuais mudanças de uso do solo ao longo do período.

Utilizando as 12440 amostras de treinamento geradas para o estado de Santa Catarina, sendo elas 4146 amostras para cada classe, foi feita a inspeção dessas por meio da ferramenta Temporal Visual Inspection (TVI) com 8 intérpretes realizando a tarefa, sendo 3 para cada ponto. Para guiar os intérpretes e manter um padrão, os treinamentos foram feitos com base na [chave de interpretação](../Resultados/Chave%20de%20Interpretação%20das%20Pastagens%20para%20o%20Estado%20de%20Santa%20Catarina.pdf) construída para o projeto.

> **Figura 4:** Visual Temporal Inspection (TVI). Visualização da ferramenta de inspeção visual para as amostras de treinamento.

---

## Scripts Relacionados

- [amostras_treinamento_sc_remap.R](../metodologia/Scripts/amostras_treinamento_sc_remap.R) — R — Sorteio aleatório estratificado dos pontos de treinamento a partir da relação MapBiomas × GPW

## Dados de Saída

- [train_samples.geojson](../Resultados/train_samples.geojson) — Pontos de treinamento gerados

---

**Etapa anterior:** [Etapa 2 — Integração de Dados](./02_integracao_dados.md)  
**Próxima etapa:** [Etapa 4 — Processamento e Classificação](./04_processamento_classificacao.md)
