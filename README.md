# predict_price
Trabalho final para a cadeira MFlow </br>
Para rodar esse projeto é necessário utilizar o Google Colab; </br>
Cadastrar um usuário no https://dashboard.ngrok.com/; </br>
É necessário adicionar a cédula que simula a API: </br>
'!ngrok authtoken <SEU TOKEN>' para simular o servidor da api.  </br>
Para realizar esse colab eu utilizei os dados disponíveis no Kagle por esse link: **https://www.kaggle.com/code/kerneler/starter-sao-paulo-real-estate-sale-07ca8a78-2**; </br>
Nesse repositório vou disponibilizar os dados em formato de csv. </br>
Os dados foram treinados para prever o preço dos apartamentos da cidade de São Paulo.  </br>
Para simular a Api local, é necessário rodar o projeto. </br>
O endereço de hospedagem é gerado local com auxílio do negrok. </br>
Para fazer um post que retorna a previsão de valor dos apartamentos é possível utilizar o Postmam.</br>
A requisição é feita com o endereço gerado no projeto + '/predict' , por exemplo: 'https://f324-34-169-62-239.ngrok-free.app/predict';</br>
No body da requisição é necessário colocar as informações do apartamentos no seguinte formato:</br>
{</br>
  "input_data": {</br>
    "Price": 7000000.0,</br>
    "Condo": 3000.0,</br>
    "Size": 440.0,</br>
    "Rooms": 4,</br>
    "Toilets": 4,</br>
    "Suites": 4,</br>
    "Parking": 8,</br>
    "Elevator": 0,</br>
    "Furnished": 0,</br>
    "Swimming Pool": 0,</br>
    "New": 0,</br>
    "Latitude": -23.5431,</br>
    "Longitude": -46.6362,</br>
    "Negotiation Type": "sale",</br>
    "Property Type": "apartment"</br>
  }</br>
}</br>
Editando de acordo com as suas preferencias.</br>
Após fazer a requisição a api deve retornar 200 com um JSON mostrando a previsão:</br>
{</br>
    "prediction": 2200000.0</br>
}</br>
A última etapa do código carrega dados, os pré-processa, treina modelos de aprendizado de máquina e os avalia. Ele usa o MLflow para registrar os experimentos e modelos. O retreinamento é agendado para ocorrer </br> periodicamente, garantindo que o modelo se adapte a possíveis mudanças nos dados ao longo do tempo. Ele também inclui uma funcionalidade para detecção de drift (mudança na distribuição dos dados), utilizando a biblioteca </br>NannyML. Esse monitoramento de drift ajuda a identificar quando o modelo pode estar se tornando menos preciso devido a mudanças nos dados de entrada, sinalizando a necessidade de um novo retreinamento.</br>
