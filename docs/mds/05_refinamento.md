# Etapa 5 — Estratégias de Refinamento

> Refinamento e auditoria manual do mapa classificado utilizando ThRasE/QGIS

---

## 5.1. Divisão em Tiles

Para melhorar a qualidade do mapa, o limite do estado de Santa Catarina foi dividido em **1.373 tiles de 10 km × 10 km**. Isso permitiu analisar e corrigir os detalhes de cada região de forma mais precisa e organizada.

### Organização dos Tiles

| Parâmetro | Valor |
|:----------|:------|
| Total de tiles | 1.373 |
| Dimensão de cada tile | 10 km × 10 km |
| Tiles por bloco de trabalho | ~25 |
| Critério de agrupamento | Características de pastagens semelhantes |

O mapa de pastagem classificado foi recortado por cada tile de 10×10 km e organizado em blocos de aproximadamente **25 tiles**, para garantir que o intérprete visualizasse uma região com características de pastagens semelhantes.

Essa divisão permitiu distribuir as tarefas de correção manual de forma organizada, garantindo que cada parte das áreas de pastagem fossem revisadas detalhadamente por um especialista do projeto.

---

## 5.2. Preparação de Dados para Refinamento

Após a classificação ser finalizada, foram realizados uma série de procedimentos preparatórios:

1. **Separação dos tiles** de acordo com as regiões separadas para cada intérprete
2. **Reprojeção** para uma projeção que permita utilizar o tamanho do pixel em metros sem necessidade de conversão
3. **Conferência** dos dados separados e organização de uma planilha de controle
4. **Preparação** dos processos de união dos dados ao finalizar as etapas

> Os processos realizados nessa etapa são os mesmos tanto em fase de refinamento quanto de auditoria.

---

## 5.3. Ferramenta de Refinamento — Plugin ThRasE

O plugin **ThRasE** (Thematic Raster Editor) é uma ferramenta voltada para o processamento de imagens raster que utiliza a técnica de classificação e refinamento de dados espaciais, integrada ao software **QGIS**.

### Ambiente de Trabalho

| Componente | Ferramenta |
|:-----------|:-----------|
| Software GIS | [QGIS](https://qgis.org/) |
| Plugin de edição | [ThRasE](https://github.com/SMByC/ThRasE) |
| Imagens de apoio | Sentinel-2 |

### Processo de Refinamento

No contexto do refinamento da classe de pastagem em Santa Catarina, a ferramenta foi utilizada da seguinte forma:

- **Inclusão** ou **exclusão** de pixels da classe de Pastagem e da classe Outros
- O plugin permite "limpar" ruídos da classificação da pastagem, para aumentar a precisão do mapeamento
- Ele automatiza a criação de máscaras, pixel a pixel, onde o intérprete analisa se uma área pertence ou não à classe de pastagem

### Fluxo de Trabalho do Refinamento

```
        Classificação        Recorte por         Distribuição        Refinamento         Checagem
        com filtro    →      tiles 10×10km   →   por intérprete  →  via ThRasE      →   de dados
        de moda                                                                          |
                                                                                         v
        União dos      ←    Alinhamento e    ←   Salvar            Listagem de
        dados                reprojeção          alterações ←      metadados
```

---

## 5.4. Auditoria

Após o refinamento, o processo de auditoria segue o mesmo fluxo, com os dados já refinados sendo novamente distribuídos para revisão por especialistas, garantindo uma segunda camada de controle de qualidade.

---

## Scripts Relacionados

| Script | Linguagem | Ambiente | Descrição |
|:-------|:----------|:---------|:----------|
| [`recorte_automatizado.sh`](../metodologia/Scripts/recorte_automatizado.sh) | Shell (Bash) | WSL/Linux | Recorte e reprojeção dos tiles para distribuição |
| [`salvar_em_pastas_yamlTIF.sh`](../metodologia/Scripts/salvar_em_pastas_yamlTIF.sh) | Shell (Bash) | WSL/Linux | Salvamento das alterações do ThRasE (YAML → TIF) |
| [`listar.py`](../metodologia/Scripts/listar.py) | Python | Local | Listagem de metadados dos arquivos raster |
| [`listar_nodata_tipo_p_lista_RASTER_v2.sh`](../metodologia/Scripts/listar_nodata_tipo_p_lista_RASTER_v2.sh) | Shell (Bash) | WSL/Linux | Listagem de NoData, tipo e propriedades dos rasters |
| [`gdal_calc_nodata.sh`](../metodologia/Scripts/gdal_calc_nodata.sh) | Shell (Bash) | WSL/Linux | Cálculo e tratamento de valores NoData |
| [`reclassificar_raster_yaml.sh`](../metodologia/Scripts/reclassificar_raster_yaml.sh) | Shell (Bash) | WSL/Linux | Reclassificação de raster com base em YAML |
| [`uniao_de_dados.sh`](../metodologia/Scripts/uniao_de_dados.sh) | Shell (Bash) | WSL/Linux | União e alinhamento dos dados refinados/auditados |

---

## Requisitos

- **Python** 3.12 ou superior
- **NumPy** 2.2.4
- **GDAL Binaries** 3.10.3
- **QGIS** com plugin ThRasE instalado

---

**Etapa anterior:** [Etapa 4 — Processamento e Classificação](./04_processamento_classificacao.md)  
**Próxima etapa:** [Etapa 6 — Análise do Mapeamento](./06_analise_mapeamento.md)
