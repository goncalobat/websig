# README

O presente código HTML foi usado para a respetiva criação de um mapa relativo aos casos de COVID-19 para o dia 23 de Janeiro.

## Estruturação do Código

Relativamente à sua estrutura, este encontra-se estruturado da seguinte maneira:

- Na parte denominada como `<head>`, encontram-se todas as bibliotecas que foram usadas e também os estilos utilizados para a criação do mapa em questão;

- Na secção `<body>` é onde se encontra a estrutura da página, incluindo a div onde por sua vez, o mapa será apresentado;

- Por último, no fim do arquivo, existe um `<script>`, contendo o código JavaScript, sendo este o responsável pela configuração do mapa a exibir.

## Configurações

- `L.map('map').setView([38.749, -9.155], 10)` -> Faz com que o mapa inicie, definindo a sua localização e ainda o nível de zoom pretendido;

- `L.tileLayer` -> Faz com que se adicione uma layer do `OpenStreetMap` ao mapa a exibir;

- `L.tileLayer.wms` -> Faz com que se adicione uma layer WMS do GeoServer ao mapa, sendo que foi necessário a utilização de uma shapefile relativa aos concelhos de Portugal continental, tendo sido esta previamente criada.

## Cores e Estilos do Mapa

- Utilização da função `getcor10k(d)` para a atribuição de cores, tendo por base o número de casos de COVID-19 por 10.000 habitantes;

- Para a definição do estilo dos polígonos presentes no mapa, com base mais uma vez, nos dados de COVID-19 por 10.000 habitantes, recorreu-se ao uso da função `estilo10k(feature)`.

## Criação de Layers

- `L.geoJSON(casos10kData)` permite a criação de uma layer (polígonos) no mapa, usando os dados geoJSON relativos aos casos COVID-19 por 10.000 habitantes;

- `L.markerClusterGroup()` permite a criação de clusters, de modo a permitir a visualização dos marcadores referentes aos casos de COVID-19, criando assim clusters (pontos) com o número de casos ao se agruparem ao longo do mapa.

## Controlos e Legenda

- `L.control.scale()` -> Permite adicionar uma escala ao mapa criado;

- `L.control.layers` -> Permite selecionar a camada a visualizar;

- `L.control({position: 'bottomright')}` -> Permite que a legenda esteja disposta na parte inferior direita do mapa ao ser exibido.

## Funcionalidades do Mapa

- A iniciação do mapa em questão é feita através do uso do Leaflet;
- A layer do OpenStreetMap é considerada como sendo uma layer base, tendo esta de ser carregada e adicionada ao mapa;
- O mesmo acontece com a layer referente aos concelhos (denominada como CONCELHOS), dado que também tem de ser carregada, porém a partir de um servido WMS, servidor este que recolhe informação ao GeoServer;
- O mapa apresenta também funções de estilo e de interação com uma layer em questão, sendo esta a dos casos por 10 mil habitantes. Estas mesmas funções são então orientadas para se criar um determinado estilo e ainda um conjunto de ações, para desta forma, definir a cor dos polígonos a formar, tendo estes a base relativa ao número de casos COVID-19. Apresentam ainda ações como por exemplo o evidenciar dos polígonos ao se mover o rato por cima dos mesmos;
- Relativamente à layer dos casos por 10 mil habitantes, esta é por sua vez, criada com base em dados geoJSON, sendo também definido um dado estilo e conjunto de ações para a mesma, sendo posteriormente adicionada ao mapa a exibir;
- Os marcadores (markers) também são outro ponto fundamental para ser adicionado e apresentado no mapa, dado que dizem respeito aos casos de COVID-19, sendo estes criados mais uma vez, com base em dados geoJSON. Posteriormente estes são agregados usando-se uma extensão específica: Leaflet.MarkerCluster;
- Há a criação de uma legenda, estando esta localizada no canto inferior direito do mapa. Esta irá possibilitar uma melhor clareza e interpretação na análise dos dados (casos COVID-19) apresentados no mapa;
- O mapa apresenta também funções de  zoom e de destacamento, ou seja, são criadas funções de maneira que seja possível o destacar de dados polígonos ao se mover o rato por cima, e ainda, caso necessário, o seu ajustamento;
- Os controlos de layer são criados para ser possível a alternação entre a layer base e a de sobreposição;
- Para uma fácil interpretação dos dados ao nível do concelho, foi necessário a criação de um controlo de informações, sendo este exibido de forma a apresentar informações sobre um determinado concelho.
