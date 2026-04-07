# Etapa 1 — Visão Geral e Introdução

> **Relatório Técnico:** Mapeamento da Pastagem em Santa Catarina para o ano de 2024 (ATBD)

---

## 1.1. Introdução

As áreas de pastagem no Brasil têm sido viabilizadas principalmente pelo aumento da produtividade da pecuária como um todo, especialmente nas áreas de pastagens que permaneceram ativas (Filho, 2014). As pastagens naturais de Santa Catarina vêm sendo, há várias décadas, substituídas por outras atividades econômicas, especialmente grãos (milho, soja, trigo), florestas cultivadas e horticultura (Córdova, et al, 2024). Tradicionalmente, os campos foram usados para pecuária extensiva, principalmente de gado de corte, com manejo baseado no pastejo direto.

### Objetivo do Projeto

O objetivo deste projeto é:

1. **Mapear as pastagens** em Santa Catarina para o ano de 2024, utilizando imagens Sentinel-2A com 10 m de resolução e a plataforma Google Earth Engine (GEE);
2. **Construir uma máscara de referência** para áreas de pastagem;
3. **Produzir amostras de treinamento**;
4. **Treinar um classificador** (Random Forest);
5. **Classificar** a totalidade de áreas de pastagem do estado;
6. **Refinar** as áreas mapeadas como pastagem;
7. **Vetorizar** os dados finais.

---

## 1.2. Plataforma de Processamento

A plataforma **Google Earth Engine** é uma plataforma para análise científica e visualização de conjuntos de dados geoespaciais, destinada a usuários acadêmicos, sem fins lucrativos, empresariais e governamentais. O Google Earth Engine hospeda imagens de satélite e as armazena em um arquivo de dados público que inclui imagens históricas da Terra com mais de quarenta anos. As imagens, processadas diariamente, são então disponibilizadas para mineração de dados em escala global. O Earth Engine também fornece APIs e outras ferramentas para permitir a análise de grandes conjuntos de dados.

---

## 1.3. Apresentação Metodológica

A apresentação metodológica utiliza:

| Componente | Detalhe |
|:-----------|:--------|
| **Satélite** | Sentinel-2A e 2B (TOA) |
| **Pré-processamento** | Filtragem de nuvem |
| **Features** | Extração de métricas espectro-temporais |
| **Amostras** | ~12.400 amostras inspecionadas visualmente |
| **Classificador** | Random Forest (500 árvores) |
| **Pós-processamento** | Filtros espaciais (moda 5×5) |
| **Validação** | Análise de consistência para seleção do melhor filtro |

---

## Equipe

| Função | Nome |
|:-------|:-----|
| Coordenador Geral | Laerte Guimarães Ferreira Jr. |
| Coordenadores Técnicos | Poliana Vieira dos Prazeres, Vinicius Vieira Mesquita, Ana Paula Mattos e Silva |
| Equipe | Ana Paula Carlos Assunção, Felipe Souza de Jesus, Guilherme Vaz |

---

## Instituições Parceiras

- **LAPIG/UFG** — Laboratório de Processamento de Imagens e Geoprocessamento
- **Remapgeo**
- **Epagri** — Empresa de Pesquisa Agropecuária e Extensão Rural de Santa Catarina

---

**Próxima etapa:** [Etapa 2 — Integração de Dados de Referência](./02_integracao_dados.md)
