# Avaliação de Acurácia da Classificação de Pastagem

---

## Acurácia Global e Estatísticas Gerais

A classificação binária da pastagem para o estado de Santa Catarina, apresentou desempenho geral satisfatório. A avaliação foi conduzida com base em 405 amostras, após a remoção de 82 amostras de bordas de um total original de 487 pontos sorteados. Os pontos sorteados foram inspecionados por 3 intérpretes independentes. A avaliação dos indicadores de erro de alocação e de quantidade foram, respectivamente, 3,28% e 0,23%.

---

## Tabela de Métricas de Validação e Erros Individuais

A consolidação de erro cruza duas ópticas. A **Acurácia do Produtor (PA)** mensura a capacidade do classificador de fato encontrar os locais que eram pastagens confirmadas na superfície, sendo seu reverso o Erro de Omissão (quando o modelo não detectou e omitiu a área). A **Acurácia do Usuário (UA)** mede o grau de pureza do desenho, ou seja, quantas áreas geradas são realmente do alvo, sendo seu reverso o Erro de Comissão (quando o modelo excede e desenha grama onde não há).

| Parâmetro Preditivo | Classe 0 (Outros/Não-Pastagem) | Classe 1 (Pastagem) |
| :--- | :---: | :---: |
| **Acurácia do Produtor (PA)** | 98,12% | **85,25%** |
| **Erro associado (Omissão)** | 1,88% | **14,75%** |
| | | |
| **Acurácia do Usuário (UA)** | 97,86% | **86,84%** |
| **Erro associado (Comissão)** | 2,14% | **13,16%** |

Esses resultados indicam que cerca de 15% das áreas de pastagens reais escorregaram nas malhas e foram subestimadas na classe *Outros*. Ao mesmo tempo, dentre tudo que se desenhou como pastagem, há "gorduras" estatísticas de 13% de detecções alheias de uso e cobertura do solo. 

Esse padrão é comum em classificações florestais, dadas as altas complexidades heterogêneas do solo (ex: pastagens degradadas, relevos ou capoeiras em transição), onde a resposta de infravermelho de *Outros* emula o tapete de *Gramíneas*.

---

## Link do Mapeamento

🔗 [Mapeamento Pastagem SC](https://polianavi.github.io/pastagem_remap/)

---

**Etapa anterior:** [Análise do Mapeamento](./analise_mapeamento.md)  
**Voltar ao índice:** [Home](../index.md)
