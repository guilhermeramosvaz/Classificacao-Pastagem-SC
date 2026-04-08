# Etapa 1 — Visão Geral e Introdução

> Relatório Técnico: Mapeamento da Pastagem em Santa Catarina para o ano de 2024 (ATBD) — Março de 2026

---

## 1.1. Introdução

As áreas de pastagem no Brasil têm sido viabilizadas principalmente pelo aumento da produtividade da pecuária como um todo, especialmente nas áreas de pastagens que permaneceram ativas (Filho, 2014). As pastagens naturais de Santa Catarina vêm sendo, há várias décadas, substituídas por outras atividades econômicas, especialmente grãos (milho, soja, trigo), florestas cultivadas e horticultura (Córdova, et al, 2024). Tradicionalmente, os campos foram usados para pecuária extensiva, principalmente de gado de corte, com manejo baseado no pastejo direto.

### Objetivo do Projeto

O objetivo deste projeto é mapear as pastagens em Santa Catarina para o ano de 2024, utilizando imagens Sentinel-2A com 10 m de resolução e a plataforma Google Earth Engine (GEE), construir uma máscara de referência para áreas de pastagem, produzir amostras de treinamento, treinar um classificador, classificar a totalidade de áreas de pastagem do estado de Santa Catarina, refinar as áreas mapeadas como pastagem e vetorizar os dados finais.

---

## 1.2. Plataforma de Processamento

A plataforma Google Earth Engine é uma plataforma para análise científica e visualização de conjuntos de dados geoespaciais, destinada a usuários acadêmicos, sem fins lucrativos, empresariais e governamentais. O Google Earth Engine hospeda imagens de satélite e as armazena em um arquivo de dados público que inclui imagens históricas da Terra com mais de quarenta anos. As imagens, processadas diariamente, são então disponibilizadas para mineração de dados em escala global. O Earth Engine também fornece APIs e outras ferramentas para permitir a análise de grandes conjuntos de dados.

---

## 1.3. Apresentação Metodológica

A apresentação metodológica utiliza imagens do satélite Sentinel-2A e 2B (TOA), filtragem de nuvem, extração de métricas, inspeção visual das amostras, treinamento com aproximadamente 12,4 mil amostras, classificação Random Forest (500 árvores) e pós-processamento com filtros espaciais, culminando em análise de consistência para seleção do melhor filtro e geração do mapeamento final.

---

## Equipe

**Coordenador geral:** Laerte Guimarães Ferreira Jr.

**Coordenadores técnicos:** Poliana Vieira dos Prazeres, Vinicius Vieira Mesquita, Ana Paula Mattos e Silva

**Equipe:** Ana Paula Carlos Assunção, Felipe Souza de Jesus, Guilherme Vaz

---

## Instituições Parceiras

- [LAPIG/UFG](https://www.lapig.iesa.ufg.br/) — Laboratório de Processamento de Imagens e Geoprocessamento
- [Remapgeo](https://www.remapgeo.com/)
- [Epagri](https://www.epagri.sc.gov.br/) — Empresa de Pesquisa Agropecuária e Extensão Rural de Santa Catarina

---

**Próxima etapa:** [Etapa 2 — Integração de Dados de Referência](./02_integracao_dados.md)
