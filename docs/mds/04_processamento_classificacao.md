# Etapa 4 — Descrição do Processamento e Algoritmo de Classificação

---

## 4.1. Processamento de Imagens

O fluxo de trabalho é implementado via Google Earth Engine (GEE), onde analisa grandes volumes de dados satelitários em tempo real. A metodologia utiliza imagens Sentinel 2A e 2B, Top of Atmosphere (TOA), processadas com o algoritmo Random Forest, que identifica áreas de pastagem com base em 164 métricas espectro-temporais e geográficas, como dados espectrais temporalmente reduzidos (Mínimo, Mediana, Máximo, Desvio Padrão, Amplitude e Percentis 10%, 25%, 75% e 90%) e informações de geolocalização (Elevação e Declividade). É utilizada uma série temporal de 24 meses de imagens. A janela temporal utilizada é entre julho de 2023 e junho de 2025 para a geração do mapa de 2024. O treinamento com classificadores de florestas considerou as amostras interpretadas visualmente pelos intérpretes.

Após o processo de classificação, os mapas são transformados de mapas probabilísticos para mapas discretos, estabelecendo o ponto de corte para áreas de pastagem para probabilidades maiores que 51%.

> **Figura 5:** Fluxo da metodologia da classificação das pastagens em Santa Catarina.

---

## 4.2. Classificação Regionalizada

A classificação é processada de forma regionalizada por Cartas do IBGE ('SG-22-X-D', 'SG-22-Z-B', 'SG-22-Z-D', 'SG-22-Z-A', 'SG-22-Z-C', 'SH-22-X-A', 'SG-22-Y-D', 'SG-22-Y-B', 'SG-22-Y-C', 'SG-22-Y-A', 'SH-22-X-B', 'SH-22-X-D'). Cada carta utiliza amostras de treinamento locais e de uma zona de amortecimento (buffer) de 100 km para reduzir efeitos de borda e capturar variações regionais do estado. São 12 modelos no total.

---

## 4.3. Abordagens de Classificação

A metodologia de classificação da pastagem apresentada, fundamenta-se em dois eixos principais de processamento: a abordagem por multi probabilidade e a abordagem binária.

Inicialmente foram realizados testes em que o processamento permitiu a distinção simultânea entre a pastagem natural, a pastagem cultivada e as demais classes de uso e cobertura da terra.

A abordagem binária desdobra-se em três fluxos distintos de discriminação para maior refinamento dos dados:

1. O primeiro fluxo binário consiste na separação inicial entre o conjunto total de pastagens e as demais classes, seguida por uma etapa de classificação dentro das áreas mapeadas como pastagem para diferenciar as tipologias natural e cultivada.
2. As outras duas variações da abordagem binária focam na diferenciação individualizada, onde se isola a pastagem natural em relação às demais classes — incluindo a pastagem cultivada no grupo de controle — ou isola-se a pastagem cultivada frente às outras coberturas, mantendo a pastagem natural inserida no grupo de demais classes.

Essa estrutura permite uma análise hierárquica e comparativa, garantindo que a detecção das áreas de gramíneas, sejam elas naturais ou antrópicas, ocorra com maior precisão metodológica frente à complexidade das demais classes de uso do solo.

A classificação binária que separava as classes de todas as pastagens por outros foi a mais correspondente com a realidade, sendo essa feita em 2 etapas:

1. Classificação binária
2. Filtro de moda com kernel 5x5

---

## Scripts Relacionados

- [Classificacao.js](../metodologia/Scripts/Classificacao.js) — JavaScript (GEE) — Classificação utilizando o algoritmo random forest com 500 árvores realizando a classificação por cartas do IBGE e unindo os dados após término de classificações
- [Filtro_moda_mediana.js](../metodologia/Scripts/Filtro_moda_mediana.js) — JavaScript (GEE) — Aplicação do filtro de moda, contém também filtro de mediana caso desejado

---

**Etapa anterior:** [Etapa 3 — Desenho Amostral e Inspeção Visual](./03_desenho_amostral.md)  
**Próxima etapa:** [Etapa 5 — Preparação de Dados e Refinamento](./05_preparacao_refinamento.md)
