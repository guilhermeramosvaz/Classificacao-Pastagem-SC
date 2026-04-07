# Etapa 7 — Avaliação de Acurácia da Classificação de Pastagem

> Métricas de acurácia do produtor, do usuário, e erros de omissão e comissão

---

## 7.1. Acurácia Global e Estatísticas Gerais

A classificação binária da pastagem para o estado de Santa Catarina apresentou **desempenho geral satisfatório**.

### Dados da Validação

| Parâmetro | Valor |
|:----------|:------|
| Total de pontos sorteados | 487 |
| Amostras de borda removidas | 82 |
| **Amostras de validação utilizadas** | **405** |
| Intérpretes independentes por ponto | 3 |

### Indicadores de Erro

| Indicador | Valor |
|:----------|:------|
| **Erro de alocação** | 3,28% |
| **Erro de quantidade** | 0,23% |

---

## 7.2. Acurácia do Produtor e Erros de Omissão

A acurácia do produtor (PA) mensura a capacidade do classificador em identificar corretamente as áreas de referência de cada classe.

| Classe | Acurácia do Produtor | Erro de Omissão |
|:-------|:---------------------|:----------------|
| **Classe 0** (Não-Pastagem/Outros) | **98,12%** | 1,88% |
| **Classe 1** (Pastagem) | **85,25%** | 14,75% |

> Aproximadamente **15%** das áreas de pastagem reais não foram detectadas pelo classificador, sendo alocadas na classe Outros. Esse padrão é comum em classificações de pastagem em regiões com alta heterogeneidade de cobertura do solo, onde áreas de pastagem degradada ou em transição podem apresentar resposta espectral similar a outras classes de vegetação.

---

## 7.3. Acurácia do Usuário e Erros de Comissão

A acurácia do usuário mede a probabilidade de que uma área mapeada como pertencente a uma determinada classe represente de fato essa classe no campo.

| Classe | Acurácia do Usuário | Erro de Comissão |
|:-------|:--------------------|:-----------------|
| **Classe 0** (Outros) | **97,86%** | 2,14% |
| **Classe 1** (Pastagem) | **86,84%** | 13,16% |

> Cerca de **13%** das áreas mapeadas como pastagem correspondem, na verdade, a outras classes de uso e cobertura do solo.

---

## 7.4. Resumo das Métricas de Acurácia

| Métrica | Classe 0 (Outros) | Classe 1 (Pastagem) |
|:--------|:-------------------|:--------------------|
| Acurácia do Produtor | 98,12% | 85,25% |
| Acurácia do Usuário | 97,86% | 86,84% |
| Erro de Omissão | 1,88% | 14,75% |
| Erro de Comissão | 2,14% | 13,16% |
| Erro de Alocação | 3,28% | — |
| Erro de Quantidade | 0,23% | — |

---

## Considerações sobre a Acurácia

- A **Classe 0 (Outros)** apresenta desempenho excelente tanto na acurácia do produtor quanto do usuário (>97%)
- A **Classe 1 (Pastagem)** apresenta acurácia satisfatória (~85-87%), com os erros concentrados em:
  - **Omissão (14,75%):** Áreas de pastagem não detectadas — geralmente pastagens degradadas ou em transição com resposta espectral ambígua
  - **Comissão (13,16%):** Áreas incorretamente mapeadas como pastagem — confusão com outras coberturas vegetais
- Os erros de **alocação (3,28%)** predominam sobre os erros de **quantidade (0,23%)**, indicando que o classificador acerta bem a proporção total de pastagem, mas comete erros pontuais de posicionamento espacial

---

## Link do Mapeamento

🔗 **[Mapeamento Final — Pastagem SC](https://polianavi.github.io/pastagem_remap/)**

---

**Etapa anterior:** [Etapa 6 — Análise do Mapeamento](./06_analise_mapeamento.md)  
**Voltar ao índice:** [README](./README.md)
