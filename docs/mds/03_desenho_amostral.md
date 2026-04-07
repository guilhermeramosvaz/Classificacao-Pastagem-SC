# Etapa 3 — Desenho Amostral e Inspeção Visual

> Amostragem probabilística estratificada e inspeção visual via TVI

---

## 3.1. Método de Amostragem

O método utiliza **amostragem probabilística estratificada**, em que cada classe da máscara é tratada como um estrato, garantindo representatividade e controle do erro.

### Parâmetros do Desenho Amostral

| Parâmetro | Valor |
|:----------|:------|
| Nível de confiança | 95% |
| Erro amostral | 8% |
| Proporção (p) | 0,5 |
| Total de amostras geradas | **12.440** |
| Amostras por classe | ~4.146 |
| Número de classes | 3 (Pastagem Natural, Pastagem Cultivada, Outros) |

As proporções das classes são estimadas a partir da contagem de pixels, servindo de base para o cálculo do tamanho amostral.

### Distribuição das Amostras

As amostras são sorteadas aleatoriamente dentro de cada estrato, assegurando:
- **Independência espacial**
- **Ausência de viés**
- **Representatividade** de todo o território estadual

O delineamento segue uma abordagem estratificada por classes, garantindo equilíbrio amostral entre os alvos de classificação. Cada classe possui aproximadamente **4.146 amostras**, indicando um esforço deliberado de balanceamento para reduzir vieses no processo de modelagem.

Após a seleção, os pontos são organizados, georreferenciados e identificados, sendo preparados para as etapas de interpretação, treinamento e validação.

---

## 3.2. Inspeção Visual (TVI)

As amostras foram inspecionadas visualmente por especialistas através da ferramenta **TVI (Temporal Visual Inspection)**, que possibilita a interpretação de séries históricas de imagens de satélite de forma independente (MATOS, et al).

### Protocolo de Inspeção

| Parâmetro | Valor |
|:----------|:------|
| Total de amostras inspecionadas | 12.440 |
| Intérpretes totais | 8 |
| Inspeções por ponto | 3 (intérpretes diferentes) |
| Série temporal utilizada | 2020, 2021, 2022, 2023, 2024 |

Cada ponto recebeu **3 inspeções de especialistas diferentes** para garantir a confiabilidade do dado de treinamento. Os intérpretes analisaram séries históricas de imagens de satélite de forma independente.

A série temporal utilizada nas inspeções compreendeu imagens dos anos **2020 a 2024**, permitindo:
- Avaliar a **estabilidade temporal** da classe atribuída ao ponto
- Identificar eventuais **mudanças de uso do solo** ao longo do período

### Chave de Interpretação

Para guiar os intérpretes e manter um padrão, os treinamentos foram feitos com base na [Chave de Interpretação das Pastagens para o Estado de Santa Catarina](../Resultados/Chave%20de%20Interpretação%20das%20Pastagens%20para%20o%20Estado%20de%20Santa%20Catarina.pdf), construída especificamente para o projeto.

---

## Scripts Relacionados

| Script | Linguagem | Descrição |
|:-------|:----------|:----------|
| [`amostras_treinamento_sc_remap.R`](../metodologia/Scripts/amostras_treinamento_sc_remap.R) | R | Sorteio aleatório estratificado dos pontos de treinamento a partir da relação MapBiomas × GPW |

---

## Dados Gerados

| Dado | Formato | Localização |
|:-----|:--------|:------------|
| Pontos de treinamento | GeoJSON | [`train_samples.geojson`](../Resultados/train_samples.geojson) |

---

**Etapa anterior:** [Etapa 2 — Integração de Dados](./02_integracao_dados.md)  
**Próxima etapa:** [Etapa 4 — Processamento e Classificação](./04_processamento_classificacao.md)
