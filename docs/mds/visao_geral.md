# Visão Geral e Introdução

> Relatório Técnico: Mapeamento da Pastagem em Santa Catarina para o ano de 2024 (ATBD) — Março de 2026

---

[//]:#(imagem_splitpanel)
<br>
<div align="center">
    <img src="base_dados/images/campo_DSC_0630_25_11_2025_15_23.jpg" width="100%" alt="split_panel">
    <p><i>Figura 1: Lapig(11/2025).</i></p>
</div>

## Introdução

As áreas de pastagem no Brasil têm sido viabilizadas principalmente pelo aumento da produtividade da pecuária como um todo, especialmente nas áreas de pastagens que permaneceram ativas (Filho, 2014). As pastagens naturais de Santa Catarina vêm sendo, há várias décadas, substituídas por outras atividades econômicas, especialmente grãos (milho, soja, trigo), florestas cultivadas e horticultura (Córdova, et al, 2024). Tradicionalmente, os campos foram usados para pecuária extensiva, principalmente de gado de corte, com manejo baseado no pastejo direto.

### Objetivo do Projeto

O objetivo deste projeto é mapear as pastagens em Santa Catarina para o ano de 2024, utilizando imagens Sentinel-2A com 10 m de resolução e a plataforma Google Earth Engine (GEE), construir uma máscara de referência para áreas de pastagem, produzir amostras de treinamento, treinar um classificador, classificar a totalidade de áreas de pastagem do estado de Santa Catarina, refinar as áreas mapeadas como pastagem e vetorizar os dados finais.

---

## Plataforma de Processamento

A plataforma Google Earth Engine é uma plataforma para análise científica e visualização de conjuntos de dados geoespaciais, destinada a usuários acadêmicos, sem fins lucrativos, empresariais e governamentais. O Google Earth Engine hospeda imagens de satélite e as armazena em um arquivo de dados público que inclui imagens históricas da Terra com mais de quarenta anos. As imagens, processadas diariamente, são então disponibilizadas para mineração de dados em escala global. O Earth Engine também fornece APIs e outras ferramentas para permitir a análise de grandes conjuntos de dados.

---

## Apresentação Metodológica

A apresentação metodológica utiliza imagens do satélite Sentinel-2A e 2B (TOA), filtragem de nuvem, extração de métricas, inspeção visual das amostras, treinamento com aproximadamente 12,4 mil amostras, classificação Random Forest (500 árvores) e pós-processamento com filtros espaciais, culminando em análise de consistência para seleção do melhor filtro e geração do mapeamento final.

---

## Principais Resultados 

O mapeamento resultou em uma área total aproximada de **1.439.037 hectares de pastagens** identificadas em Santa Catarina, valor altamente coeso com a base de referência do Mapbiomas (diferença absoluta de apenas -0,37%).

Todo este fluxo metodológico está devidamente organizado e fragmentado em códigos e tarefas computacionais. Para replicar ou entender em nível técnico as execuções, acessando a etapa de [Passo a Passo e Processos Metodológicos](./passo_a_passo.md).

---


**Próxima etapa:** [Integração de Dados de Referência](./integracao_dados.md)
