# Processamento e Algoritmo de Classificação

---

## Processamento de Imagens

O fluxo de trabalho é implementado via **Google Earth Engine (GEE)**, onde são analisados grandes volumes de dados satelitários em tempo real. A metodologia utiliza imagens Sentinel-2A e 2B, *Top of Atmosphere* (TOA), processadas nativamente com o algoritmo estatístico **Random Forest**.

O processamento das áreas de pastagem é amparado por **164 métricas espectro-temporais e geográficas**, resumidas abaixo:

| Categoria de Dado | Métricas Utilizadas no Treinamento Preditivo |
| :--- | :--- |
| **Série Temporal (24 meses)** | Análise entre Julho de 2023 e Junho de 2025 (p/ mapa de 2024) |
| **Espectrais Reduzidas** | Mínimo, Mediana, Máximo, Desvio Padrão e Amplitude |
| **Percentis Estatísticos** | Percentis de 10%, 25%, 75% e 90% |
| **Geolocalização / Terreno** | Elevação e Declividade |

Após o processamento via *Random Forest*, os mapas brutos são convertidos de naturezas probabilísticas para discretas, fincando o "ponto de corte" paramétrico para pastagem em probabilidades \> 51%.

> **Figura 5:** Fluxo da metodologia da classificação das pastagens em Santa Catarina.

---

## Classificação Regionalizada

A classificação de máquina não age no estado todo de uma vez; é processada de forma estritamente regionalizada e subdividida. São **12 modelos globais**, parametrizados segundo as correspondentes Cartas de Articulação do IBGE:

| Malha de Processamento | Cartas do IBGE Referenciadas |
| :---: | :--- |
| **Cartas "SG-22" (10 Modelos)** | SG-22-X-D, SG-22-Z-B, SG-22-Z-D, SG-22-Z-A, SG-22-Z-C, SG-22-Y-D, SG-22-Y-B, SG-22-Y-C, SG-22-Y-A |
| **Cartas "SH-22" (2 Modelos)** | SH-22-X-A, SH-22-X-B, SH-22-X-D | *Nota: O ajuste exato resulta em 12 zonas poligonais.* |

Para cada carta, os modelos utilizam as respectivas amostras locais, absorvendo ainda uma **zona de amortecimento (buffer) de 100 km**, garantindo com sucesso uma transição impecável para mitigar os temidos *efeitos de borda*.

---

## Abordagens de Classificação

A metodologia de classificação da pastagem apresentada, fundamenta-se em dois eixos principais de processamento: a abordagem por multi probabilidade e a abordagem binária.

Inicialmente foram realizados testes em que o processamento permitiu a distinção simultânea entre a pastagem natural, a pastagem cultivada e as demais classes de uso e cobertura da terra.

A abordagem binária desdobra-se em três fluxos distintos de discriminação para maior refinamento dos dados:

1. O primeiro fluxo binário consiste na separação inicial entre o conjunto total de pastagens e as demais classes, seguida por uma etapa de classificação dentro das áreas mapeadas como pastagem para diferenciar as tipologias natural e cultivada.
2. As outras duas variações da abordagem binária focam na diferenciação individualizada, onde se isola a pastagem natural em relação às demais classes — incluindo a pastagem cultivada no grupo de controle — ou isola-se a pastagem cultivada frente às outras coberturas, mantendo a pastagem natural inserida no grupo de demais classes.

Essa estrutura permite uma análise hierárquica e comparativa, garantindo que a detecção das áreas de gramíneas ocorra com maior precisão frente à complexidade do solo. Diante dos testes práticos, o cenário "isolado" sagrou os melhores caminhos, consolidando em apenas **duas etapas computacionais (Scripts)**:

1. **Ação do `Classificacao.js`**: Conduz uma Classificação Binária dura, englobando todas as pastagens num único grupo versus as demais sub-classes ("Outros"). Ele gera os pixels em base bruta em cada um dos 12 blocos e amarra tudo.
2. **Ação do `Filtro_moda_mediana.js`**: Aplica pós-processamento utilizando um *filtro de moda com kernel dinâmico de raio 5x5* para remover ruído-pixel (ex: árvores solitárias na pastagem) e "limpar" a mancha poligonal resultante.

---

## Scripts Relacionados

- [Classificacao.js](https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/Classificacao.js) — JavaScript (GEE) — Classificação utilizando o algoritmo random forest com 500 árvores realizando a classificação por cartas do IBGE e unindo os dados após término de classificações
- [Filtro_moda_mediana.js](https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/Filtro_moda_mediana.js) — JavaScript (GEE) — Aplicação do filtro de moda, contém também filtro de mediana caso desejado

---

**Etapa anterior:** [Desenho Amostral e Inspeção Visual](./desenho_amostral.md)  
**Próxima etapa:** [Preparação de Dados e Refinamento](./preparacao_refinamento.md)
