# Etapa 2 — Integração de Dados de Referência (MapBiomas e Global Pasture Watch)

> Descrição Metodológica: Integração MapBiomas e Global Pasture Watch (GPW) para o Estado de Santa Catarina

---

## 2.1. Integração de Dados

Para a geração do estrato amostral, aplicou-se uma técnica de combinação categórica entre os dados do **MapBiomas** e do **Global Pasture Watch (GPW)** para a criação de uma máscara amostral. Este procedimento visa identificar a concordância e divergência entre as bases, permitindo uma análise espacial das áreas de gramíneas e pastagens no estado de Santa Catarina.

---

## 2.2. Fontes de Dados e Pré-processamento

### 2.2.1. Máscara de Referência

A metodologia utiliza como base de dados primária o mapeamento de uso e cobertura da terra da **Coleção 9.0 do MapBiomas** para o ano de **2022**.

O processamento inicial consiste na filtragem e reclassificação das classes de interesse do MapBiomas:
- **Campestre** (classe 12)
- **Pastagem** (classe 15)

Focando nas tipologias que apresentam maior potencial ou transição com áreas de pastagem. Todas as demais classes do mapa de uso e cobertura do MapBiomas são atribuídos **valor 0**.

### 2.2.2. Global Pasture Watch (GPW)

São integrados os dados de mapeamento da pastagem do GPW, especificamente o produto das classes de gramíneas:
- **Cultivated grassland** (classe 1)
- **Natural/semi-natural grassland** (classe 2)

Também referente ao ano de **2022**. Todas as demais classes do mapa de pastagem do GPW são atribuídos **valor 0**.

---

## 2.3. Operação de Integração

O resultado foi recortado espacialmente para os limites do estado de Santa Catarina. A integração foi realizada através de uma operação aritmética de "transição":

```
Valor_Integrado = (Classe_MapBiomas × 100) + Classe_GPW
```

Esta abordagem gera **códigos únicos** que representam cada combinação possível entre as duas fontes de dados, gerando no total **12 combinações**.

> **Exemplo:** O código `1501` representaria a Classe 15 (*Pastagem*) do MapBiomas integrada à Classe 1 (*Cultivated grassland*) do Global Pasture Watch.

---

## 2.4. Produto: Máscara de Estrato Amostral

O produto desta etapa é uma **máscara de estrato amostral**, exportada como um asset de imagem no GEE. Este mapa de "transição" serve como base para o sorteio de pontos de treinamento, garantindo que a variabilidade das diferentes bases de dados seja representada no processo de inspeção visual para amostras de classificação.

### Classes da Máscara Resultante

| Classe | Descrição |
|:-------|:----------|
| **Pastagem Natural** | Áreas de vegetação herbácea/gramínea original (como os Campos e topos de Serras), incluindo áreas úmidas (banhados) e áreas com diferentes graus de conservação. |
| **Pastagem Cultivada** | Áreas onde a vegetação nativa (geralmente florestal) foi substituída por gramíneas plantadas, envolvendo manejo antrópico intensivo. |
| **Outros** | Classes de uso e cobertura que não se enquadram em pastagens (agricultura, silvicultura, áreas urbanas, corpos d'água, etc.). |

---

## Scripts Relacionados

| Script | Linguagem | Descrição |
|:-------|:----------|:----------|
| [`mascara_estrato_amostral_Mapbiomas_GPW.js`](../metodologia/Scripts/mascara_estrato_amostral_Mapbiomas_GPW.js) | JavaScript (GEE) | Geração da máscara de estrato amostral a partir da combinação MapBiomas e GPW |

---

**Etapa anterior:** [Etapa 1 — Visão Geral](./01_visao_geral.md)  
**Próxima etapa:** [Etapa 3 — Desenho Amostral e Inspeção Visual](./03_desenho_amostral.md)
