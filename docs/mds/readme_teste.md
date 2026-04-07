# Mapeamento da Pastagem no estado de Santa Catarina

![Foto_pastagem_Vieira_Mesquita(11/2025)](imgs/campo_DSC_0630_25_11_2025_15_23.jpg)
*Figura 1: Lapig(11/2025).*

## Introdução

Trabalho de mapeamento das pastagens do estado de Santa Catarina para o ano de 2024 realizado pela parceria entre Lapig e Remapgeo. Utilizando imagens do satélite Sentinel 2A/B com 10 metros de resolução espacial, dados de referência do Mapbiomas e Global Pasture Watch, foi possível gerar uma classificação supervisionada para todo o estado, realizada com o Algorítmo Random Forest, descrita em [metodologia](./metodologia/).

No presente repositório serão encontrados os seguintes dados:

- Processos metodológicos realizados no decorrer do projeto:
    1. [Definição de metodologia](metodologia/README.md#desenho)
    2. [Geração de amostras]()
    3. [Classificação](metodologia/README.md#classificacao)
    4. [Chave de interpretação](./Resultados/Chave%20de%20Interpretação%20das%20Pastagens%20para%20o%20Estado%20de%20Santa%20Catarina.pdf)
    5. [Refinamento e auditoria](metodologia/README.md#refinamento_e_auditoria)
- [Scripts](metodologia/Scripts/) utilizados em shell script, javascript (utilizado dentro do ambiente Google Earth engine, GEE) e python;
- [Resultados gerados](Resultados/) no processo;

## Bases de dados

Foram utilizados como dados de referência os dados de pastagem [Mapbiomas](https://brasil.mapbiomas.org/) e global pasture watch do [Land & Carbon Lab](https://landcarbonlab.org/about-global-pasture-watch/) para gerar os pontos utilizados.

## Requisitos

- Python 3.12 ou superior
- Numpy 2.2.4 python package
- Gdal Binaries 3.10.3 

## Acknowledgements

| | |
|:---:|:---:|
|This research was supported by Epagri| ![epagri](imgs/epagri.png) |
|This research was supported by LAPIG/UFG| ![LAPIG Logo](imgs/LAPIG%20Logo.png) |
|This research was supported by Remapgeo| ![REMAPgeo](imgs/REMAPgeo.png) |

