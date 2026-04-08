# Etapa 5 — Estratégias de Refinamento

---

## 5.1. Divisão em Tiles

Para melhorar a qualidade do mapa, dividimos o limite do estado de Santa Catarina em 1.373 tiles de 10 km x 10 km. Isso permitiu analisar e corrigir os detalhes de cada região de forma mais precisa e organizada. O mapa de pastagem classificado foi recortado por cada tile de 10x10 km e organizado em blocos de aproximadamente 25 tiles, para garantir que o intérprete visualizasse uma região com características de pastagens semelhantes. Essa divisão permitiu distribuir as tarefas de correção manual no plugin ThRasE de forma organizada, garantindo que cada parte das áreas de pastagem fossem revisadas detalhadamente por um especialista do projeto.

---

## 5.2. Preparação de Dados

Após a classificação ser finalizada foram realizados uma série de procedimentos para a etapa de refinamento. Sendo eles a separação dos tiles de acordo com as regiões separadas para cada intérprete. Os dados são recortados e reprojetados para uma projeção que permita utilizar o tamanho do pixel em metros sem necessidade de conversão e separados em pastas para cada intérprete. Conferir os dados separados e organizar uma planilha de controle e preparação dos demais processos, como o de união dos dados ao finalizar as etapas de refinamento e auditoria. Os processos realizados nessa etapa, são os mesmos tanto em fase de refinamento quanto de auditoria.

> **Figura 5 (metodologia):** Início de divisões de regiões para refinamento e auditoria.

---

## 5.3. Plugin ThRasE

O plugin ThRasE (thematic raster editor) é uma ferramenta voltada para o processamento de imagens raster que utiliza a técnica de classificação e refinamento de dados espaciais. No contexto do refinamento da classe de pastagem em Santa Catarina, o seu uso foi da seguinte forma:

- Inclusão ou exclusão de pixel da classe de Pastagem e da classe Outros.

O plugin permite "limpar" ruídos da classificação da pastagem, para aumentar a precisão do mapeamento em Santa Catarina. Ele automatiza a criação de máscaras, pixel a pixel, onde o intérprete analisa se uma área pertence ou não à classe de pastagem.

Utilizando o software [QGIS](https://qgis.org/) juntamente com o plug-in [ThRasE](https://github.com/SMByC/ThRasE) e imagens Sentinel, possibilitaram a atividade de refinamento e auditoria dos dados recortados por regiões.

---

## 5.4. Controle de Qualidade

Após os refinamentos e auditorias realizados no ThRasE, os analistas mandavam uma pasta contendo os arquivos raster usados e o dado de extensão ".yaml" que continha as alterações. Para que o dado seja salvo é necessário fixar essa alteração, então usando o dado original dentro da pasta criar uma nova versão do arquivo.

Para controle de dados, foi necessário que os dados salvos fossem listados visando entender as informações de cada dado gerado, desde extensão até mesmo valor sem dados. Essa é a etapa de checagem de dados.

Posterior ao processo de checagem, após verificar compatibilidade dos dados, os processos de união e alinhamento e reprojeção foram aplicados.

> **Figura 6 (metodologia):** Fluxograma de processamento de dados.

---

## Scripts Relacionados

- [recorte_automatizado.sh](../metodologia/Scripts/recorte_automatizado.sh) — Shell (WSL/Linux) — Recorte e reprojeção dos tiles para distribuição por intérprete
- [salvar_em_pastas_yamlTIF.sh](../metodologia/Scripts/salvar_em_pastas_yamlTIF.sh) — Shell (WSL/Linux) — Salvamento das alterações do ThRasE (YAML → TIF)
- [listar.py](../metodologia/Scripts/listar.py) — Python — Listagem de metadados dos arquivos raster
- [listar_nodata_tipo_p_lista_RASTER_v2.sh](../metodologia/Scripts/listar_nodata_tipo_p_lista_RASTER_v2.sh) — Shell (WSL/Linux) — Listagem de NoData, tipo e propriedades dos rasters
- [gdal_calc_nodata.sh](../metodologia/Scripts/gdal_calc_nodata.sh) — Shell (WSL/Linux) — Cálculo e tratamento de valores NoData
- [reclassificar_raster_yaml.sh](../metodologia/Scripts/reclassificar_raster_yaml.sh) — Shell (WSL/Linux) — Reclassificação de raster com base em YAML
- [uniao_de_dados.sh](../metodologia/Scripts/uniao_de_dados.sh) — Shell (WSL/Linux) — União e alinhamento dos dados refinados/auditados

## Requisitos

- Python 3.12 ou superior
- Numpy 2.2.4 python package
- GDAL Binaries 3.10.3
- QGIS com plugin ThRasE instalado

---

**Etapa anterior:** [Etapa 4 — Processamento e Classificação](./04_processamento_classificacao.md)  
**Próxima etapa:** [Etapa 6 — Análise do Mapeamento](./06_analise_mapeamento.md)
