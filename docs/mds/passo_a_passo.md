# Passo a Passo e Processos Metodológicos (Scripts)
---

## Definição de metodologia
A metodologia de classificação utilizando o algoritmo Random Forest descrita no <a href="https://amazonia.mapbiomas.org/wp-content/uploads/sites/10/2024/09/Apendice-12-Pastos-Coleccion-6.0.pdf"> Documento Base Teórico de Algoritmos (ATBD) </a>, realizada pelo Mapbiomas foi base para projeto. Usar cartas do Instituto Brasileiro de Geografia e Estatística (IBGE) para delimitar regiões de classificação. Para cada carta, é utilizado as amostras da carta central e um buffer de 100 km da vizinhança para o treinamento do classificador. São 12 modelos no total.




---

## Desenho amostral
Foi realizado o Sorteio aleatório estratificado proporcionalmente pelos estratos secundários e uniforme para as 3 classes resultantes das máscaras de referência (Mapbiomas uso e cobertura e Global Pasture Watch) ambas contendo as classes de pastagem natural, cultivada e outros. especificamente a máscara do mapbiomas resumiu todas as classes que não fossem vegetação campestre, pastagem e mosaico de usos foram classificadas com "outros" para evitar confusão com todas as outras classes que não são o foco da pesquisa.
<br>



---

## Inspeção visual de pontos
Utilizando as 12440 amostras de treinamento geradas para o estado de Santa Catarina, sendo elas 4146 amostras para cada classe, foi feita a inspeção dessas por meio da ferramenta <a href="https://tvi.lapig.iesa.ufg.br/#/login"> Temporal Visual Inspection (TVI) </a> com 8 interpretes realizando a tarefa, sendo 3 para cada ponto. Para guiar os interpretes e manter um padrão, os treinamentos foram feitos com base na chave de interpretação costruída para o projeto.
<br>

---

## Classificação
A metodologia realizada pelo mapbiomas de classificação de áreas de pastagem foi adaptanda pois a possibilidade de classificar áreas de pastagem naturais e pastagens cultivadas foi explorada em testes. A classificação binária que separava as classes de todas as pastagens por outros foi a mais correspondente com a realidade, sendo essa feita em 2 etapas, apontadas nos scripts abaixo:
    <ul>
        <li><a href="https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/Classificacao.js"> Classificação binária </a> (GEE JavaScript)</li>
        <li><a href="https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/Filtro_moda_mediana.js"> Filtro de moda com kernel 5x5 </a> (GEE JavaScript)</li>
    </ul>
<br>

---

## Preparação de dados para análise
Após a classificação ser finalizada foram realizados uma série de procedimentos para a etapa de refinamento. Sendo eles a separação dos tiles de acordo com as regiões separadas para cada interprete. Conferir os dados separados e organizar uma planilha de controle e preparação dos demais processos, como o de união dos dados ao finalizar as etapas de refinamento e auditoria. Os processos realizados nessa etapa são os mesmos tanto em fase de refinamento quanto de auditoria. Scripts referentes a estes processos:
    <ul>
        <li><a href="https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/recorte_automatizado.sh"> Scripts Automatizados de Recorte </a> (.sh)</li>
        <li><a href="https://github.com/guilhermeramosvaz/Classificacao-Pastagem-SC/blob/main/docs/base_dados/aplicacao/Scripts/uniao_de_dados.sh"> Scripts de União de Dados </a> (.sh)</li>
    </ul>
<br>

---

## Refinamento e Auditoria
Utilizando o software <a href="https://qgis.org/"> Qgis </a> juntamente com o plug-in <a href="https://github.com/SMByC/ThRasE"> thRasE </a> e imagens sentinel, possibilitaram a atividade de refinamento e auditoria dos dados recortados por regiões.
