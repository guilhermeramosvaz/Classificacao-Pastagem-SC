# Etapa 2 — Descrição Metodológica: Integração MapBiomas e Global Pasture Watch (GPW) para o Estado de Santa Catarina

---

## 2.1. Integração de Dados

Para a geração do estrato amostral, aplicou-se uma técnica de combinação categórica entre os dados do MapBiomas e do Global Pasture Watch (GPW) para a criação de uma máscara amostral. Este procedimento visa identificar a concordância e divergência entre as bases, permitindo uma análise espacial das áreas de gramíneas e pastagens no estado de Santa Catarina.

---

## 2.2. Fontes de Dados e Pré-processamento

### 2.2.1. Máscara de referência

A metodologia utiliza como base de dados primária o mapeamento de uso e cobertura da terra da Coleção 9.0 do MapBiomas para o ano de 2022. O processamento inicial consiste na filtragem e reclassificação das classes de interesse do MapBiomas (Campestre e Pastagem), focando nas tipologias que apresentam maior potencial ou transição com áreas de pastagem. Todas as demais classes do mapa de uso e cobertura do MapBiomas são atribuídos valor 0. São integrados os dados de mapeamento da pastagem do Global Pasture Watch (GPW), especificamente o produto das classes de gramíneas Cultivated grassland e natural/semi-natural grassland, também referente ao ano de 2022. Todas as demais classes do mapa de pastagem do GPW, são atribuídos valor 0.

O resultado foi recortado espacialmente para os limites do estado de Santa Catarina. A integração foi realizada através de uma operação aritmética de "transição", onde os valores das classes do MapBiomas foram multiplicados por 100 e somados aos valores das classes do GPW.

> [!TIP] 
> **Lógica do algoritmo no GEE:**
> A fórmula executada via JavaScript para mesclar os mapas gerou uma matriz de reclassificação única:
> `Valor_Integrado = (Classe_MapBiomas x 100) + Classe_GPW`

Esta abordagem gera códigos compostos que representam cada sobreposição de cenários, originando um total de **12 combinações**. Exemplos ilustrativos:

| Código Final | Classe Base: MapBiomas (Base 100) | Classe Integrada: Global Pasture Watch |
| :---: | :--- | :--- |
| **1501** | Classe **15** (Pastagem) | Classe **1** (Cultivated Grassland) |
| **1502** | Classe **15** (Pastagem) | Classe **2** (Natural/Semi-natural Grassland) |
| **1201** | Classe **12** (Formação Campestre) | Classe **1** (Cultivated Grassland) |
| **...** | *Demais permutações (12 totais)* | *Demais categorizações combinadas* |

---

> **Figura 2:** Matriz de reclassificação das classes de pastagem a partir da combinação MapBiomas (2022) Global Pasture Watch (2022).

O produto desta etapa (operado através do [script citado no rodapé](#scripts-relacionados)), é uma máscara de estrato amostral, exportada como um ativo de imagem no GEE. Este mapa transversal serve como mapa-base para o sorteio de pontos, garantindo a variabilidade de transições na área de estudo. Por fim, a máscara resultante das 12 combinações foi simplificada em apenas **três macroclasses**:

- **Pastagem Natural:** Áreas de vegetação herbácea/gramínea original (como os Campos e topos de Serras), incluindo áreas úmidas (banhados) e áreas com diferentes graus de conservação.
- **Pastagem Cultivada:** Áreas onde a vegetação nativa (geralmente florestal) foi substituída por gramíneas plantadas, envolvendo manejo antrópico intensivo.
- **Outros:** Classes de uso e cobertura que não se enquadram em pastagens (agricultura, silvicultura, áreas urbanas, corpos d'água, etc.).

---

## Scripts Relacionados

- [mascara_estrato_amostral_Mapbiomas_GPW.js](../base_dados/aplicacao/Scripts/mascara_estrato_amostral_Mapbiomas_GPW.js) — JavaScript (GEE) — Geração da máscara de estrato amostral a partir da combinação MapBiomas e GPW

---

**Etapa anterior:** [Etapa 1 — Visão Geral](./01_visao_geral.md)  
**Próxima etapa:** [Etapa 3 — Desenho Amostral e Inspeção Visual](./03_desenho_amostral.md)
