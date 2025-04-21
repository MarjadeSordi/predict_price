# predict_price
Trabalho final para a cadeira MFlow
Para rodar esse projeto é necessário utilizar o Google Colab;
Cadastrar um usuário no https://dashboard.ngrok.com/;
É necessário adicionar a cédula que simula a API:
'!ngrok authtoken <SEU TOKEN>' para simular o servidor da api. 
Para realizar esse colab eu utilizei os dados disponíveis no Kagle por esse link: **https://www.kaggle.com/code/kerneler/starter-sao-paulo-real-estate-sale-07ca8a78-2**;
Nesse repositório vou disponibilizar os dados em formato de csv. 
Os dados foram treinados para prever o preço dos apartamentos da cidade de São Paulo. 
Para simular a Api local, é necessário rodar o projeto. 
O endereço de hospedagem é gerado local com auxílio do negrok. 
Para fazer um post que retorna a previsão de valor dos apartamentos é possível utilizar o Postmam.
A requisição é feita com o endereço gerado no projeto + '/predict' , por exemplo: 'https://f324-34-169-62-239.ngrok-free.app/predict';
No body da requisição é necessário colocar as informações do apartamentos no seguinte formato:
{
  "input_data": {
    "Price": 7000000.0,
    "Condo": 3000.0,
    "Size": 440.0,
    "Rooms": 4,
    "Toilets": 4,
    "Suites": 4,
    "Parking": 8,
    "Elevator": 0,
    "Furnished": 0,
    "Swimming Pool": 0,
    "New": 0,
    "Latitude": -23.5431,
    "Longitude": -46.6362,
    "Negotiation Type": "sale",
    "Property Type": "apartment"
  }
}
Editando de acordo com as suas preferencias.
Após fazer a requisição a api deve retornar 200 com um JSON mostrando a previsão:
{
    "prediction": 2200000.0
}
A última etapa do código carrega dados, os pré-processa, treina modelos de aprendizado de máquina e os avalia. Ele usa o MLflow para registrar os experimentos e modelos. O retreinamento é agendado para ocorrer periodicamente, garantindo que o modelo se adapte a possíveis mudanças nos dados ao longo do tempo. Ele também inclui uma funcionalidade para detecção de drift (mudança na distribuição dos dados), utilizando a biblioteca NannyML. Esse monitoramento de drift ajuda a identificar quando o modelo pode estar se tornando menos preciso devido a mudanças nos dados de entrada, sinalizando a necessidade de um novo retreinamento.
