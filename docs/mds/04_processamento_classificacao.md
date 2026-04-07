# Etapa 4 — Processamento de Imagens e Algoritmo de Classificação

> Classificação supervisionada via Google Earth Engine com Random Forest

---

## 4.1. Processamento de Imagens

O fluxo de trabalho é implementado via **Google Earth Engine (GEE)**, onde se analisa grandes volumes de dados satelitários em tempo real.

### Dados de Entrada

| Componente | Especificação |
|:-----------|:-------------|
| **Satélite** | Sentinel 2A e 2B |
| **Processamento** | Top of Atmosphere (TOA) |
| **Janela temporal** | Julho/2023 – Junho/2025 (24 meses) |
| **Ano de referência** | 2024 |
| **Total de métricas** | 164 métricas espectro-temporais e geográficas |

### Métricas Espectrais Utilizadas

As métricas são geradas a partir de reduções temporais aplicadas às bandas espectrais:

| Tipo de Redução | Descrição |
|:----------------|:----------|
| Mínimo | Valor mínimo da série temporal |
| Mediana | Valor mediano |
| Máximo | Valor máximo |
| Desvio Padrão | Dispersão dos valores |
| Amplitude | Diferença entre máximo e mínimo |
| Percentil 10% | Valor do percentil 10 |
| Percentil 25% | Valor do percentil 25 |
| Percentil 75% | Valor do percentil 75 |
| Percentil 90% | Valor do percentil 90 |

### Informações Geográficas Complementares

- **Elevação** (modelo digital de elevação)
- **Declividade** (slope)

---

## 4.2. Algoritmo de Classificação — Random Forest

O treinamento com classificadores de florestas considerou as amostras interpretadas visualmente pelos intérpretes.

### Parâmetros do Classificador

| Parâmetro | Valor |
|:----------|:------|
| Algoritmo | Random Forest |
| Número de árvores | 500 |
| Tipo de classificação | Binária (Pastagem × Outros) |
| Limiar de probabilidade | > 51% |

### Conversão Probabilidade → Mapa Discreto

Após o processo de classificação, os mapas são transformados de mapas probabilísticos para mapas discretos, estabelecendo o ponto de corte para áreas de pastagem para probabilidades **maiores que 51%**.

---

## 4.3. Classificação Regionalizada

A classificação é processada de forma **regionalizada por Cartas do IBGE**:

```
SG-22-X-D, SG-22-Z-B, SG-22-Z-D, SG-22-Z-A, SG-22-Z-C,
SH-22-X-A, SG-22-Y-D, SG-22-Y-B, SG-22-Y-C, SG-22-Y-A,
SH-22-X-B, SH-22-X-D
```

> **Total: 12 modelos** regionais

Cada carta utiliza amostras de treinamento locais e de uma **zona de amortecimento (buffer) de 100 km** para reduzir efeitos de borda e capturar variações regionais do estado.

---

## 4.4. Abordagens de Classificação Testadas

A metodologia fundamenta-se em dois eixos principais de processamento:

### Abordagem Multi-Probabilidade
Processamento que permitiu a distinção simultânea entre pastagem natural, pastagem cultivada e demais classes de uso e cobertura da terra.

### Abordagem Binária (selecionada)
Desdobra-se em três fluxos distintos de discriminação:

1. **Fluxo 1:** Separação inicial entre o conjunto total de pastagens e as demais classes, seguida por classificação interna para diferenciar as tipologias natural e cultivada.
2. **Fluxo 2:** Isolamento da pastagem natural em relação às demais classes (incluindo pastagem cultivada no grupo de controle).
3. **Fluxo 3:** Isolamento da pastagem cultivada frente às outras coberturas (mantendo pastagem natural no grupo de demais classes).

> A **classificação binária** (Pastagem × Outros) foi a mais correspondente com a realidade, sendo a abordagem final adotada.

### Pós-processamento

Após a classificação binária, é aplicado um **filtro de moda com kernel 5×5** para suavizar ruídos espaciais.

---

## Scripts Relacionados

| Script | Linguagem | Ambiente | Descrição |
|:-------|:----------|:---------|:----------|
| [`Classificacao.js`](../metodologia/Scripts/Classificacao.js) | JavaScript | GEE | Classificação binária com Random Forest por cartas do IBGE |
| [`Filtro_moda_mediana.js`](../metodologia/Scripts/Filtro_moda_mediana.js) | JavaScript | GEE | Aplicação do filtro de moda 5×5 (e mediana opcional) |

---

**Etapa anterior:** [Etapa 3 — Desenho Amostral e Inspeção Visual](./03_desenho_amostral.md)  
**Próxima etapa:** [Etapa 5 — Estratégias de Refinamento](./05_refinamento.md)
