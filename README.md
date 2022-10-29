# Projeto de Segmentação de Clientes - Departamento de Marketing

<h2> O que é a Segmentação de Cliente ? </h2>

A segmentação de clientes é, basicamente, separá-los em grupos menores, usando aspectos comuns entre eles. Logo, o objetivo disso é oferecer uma comunicação mais assertiva e personalizada aos clientes, melhorando sua experiência e entregando valor relevante para eles.

A segmentação oferece uma maneira simples de organizar e gerenciar os relacionamentos da sua empresa com os clientes.  Esse processo também facilita adaptar e personalizar seus esforços de marketing, vendas e pós-vendas para as necessidades de grupos específicos. 

Portanto, um dos pontos cruciais de marketing é conhecer os clientes e identificar suas necessidades. Logo, entendendo os consumidores podemos enviar campanhas para necessidades específicas. Se dados sobre os clientes estão disponíveis, podemos aplicar Ciência de Dados para segmentar o mercado.


<h2> 4 Razões para Segmentar Clientes </h2>

- Os consumidores são mais propensos a comprar de fornecedores
- Eficiência na comunicação de e-mails
- Evoluir o relacionamento com o cliente 
- Clareza nas características do público que geram maior faturamento

<h2> Desafio </h2>

Fomos contratados por um banco de Nova York para desenvolver um modelo que ajude na segmentação do cliente para definir a estratégia de marketing a ser tomada.
O conjunto de dados é uma amostra que resume o comportamento de uso do cartão de crédito de 9000 clientes ativos durante os últimos 6 meses.

<h2> Objetivo </h2>

- Analisar dados

- Construir um modelo de clusterização

<h2> Dicionário de Dados </h2>

- `CUSTID` : Identificador do cliente.
- `BALANCE`: Saldo para fazer compras.
- `BALANCE_FREQUENCY`: Frequência que o saldo é atualizado (1 = frequente, 0 = não frequente).
- `PURCHASES`: Quantidade de compras realizadas.
- `ONEOFFPURCHASES`: Quantidade de compras feitas "de uma vez só" (sem parcelar).
- `INSTALLMENTS_PURCHASES`: Quantidade de compras parceladas.
- `CASH_ADVANCE`: Dinheiro adiantado.
- `PURCHASES_FREQUENCY`: Frequência das compras (entre 1 e 0).
- `ONEOFF_PURCHASES_FREQUENCY`: Frequência de compras à vista (entre 1 e 0).
- `PURCHASES_INSTALLMENTS_FREQUENCY`: Frequência de compras parceladas (entre 1 e 0).
- `CASH_ADVANCE_FREQUENCY`: Frequência de saques de dinheiro adiantado.
- `CASH_ADVANVE_TRX`: Número de transações feitas como "Cash in Advance".
- `PURCHASES_TRX`: Número de compras.
- `CREDIT_LIMIT`: Limite do cartão de crédito.
- `PAYMENTS`: Valor pago.
- `MINIMUM_PAYMENTS`: Valor mínimo pago.
- `PRC_FULL_PAYMENT`: Percentual de pagamentos da fatura completa.
- `TENURE`: Posse do titular do cartão.


O desenvolvimento do projeto encontra-se no [notebook](https://github.com/nickolasdias/marketing/blob/main/notebooks/m01.ipynb)

## 3.1 Principais Passos

### 3.1.1 Descrição dos Dados - Estatística Descritiva


### 3.1.2 Análise de Dados - Análise Univariada

![01](https://github.com/nickolasdias/marketing/blob/main/Imagens/01.png)

**Observações:**

- Mais de 4000 clientes tem saldo baixo para fazer compras.
- Cerca de 6000 clientes mantém sua o saldo atualizado.
- 2778 compras de até 100 dólares foram realizadas.
- 4553 compras à vista de até 50 dólares foram realizadas.
- 3994 compras parceladas de até 25 dólares foram realizadas.
- 2043 clientes não realizam compras e 2178 clientes fizeram compras com frequência nos últimos 6 meses.
- 4302 clientes não realizaram compras à vista com frequência nos últimos 6 meses.
- 3915 clientes não realizaram compras parceladas com frequência nos últimos 6 meses.
- 4628 clientes não realizaram saque de dinheiro do cartão de crédito nos últimos 6 meses.
- A maioria dos clientes possuem limite de crédito entre 0 e 6200 dólares.
- 5903 clientes não pagaram a fatura total nos últimos 6 meses.
- Mais de 7000 mil clientes estão no banco há 12 anos.


### 3.1.3 Análise de Dados - Validação de Hipótese



- Qual o perfil do cliente que realizou a compra a vista mais cara ?
- Qual o perfil do cliente que realizou a compra parcelada mais cara ?
- Qual o perfil do cliente que sacou dinheiro do crédito mais alto ?
- Qual o perfil do cliente que faz o pagamento total da fatura ?
- Qual o perfil do cliente que não faz o pagamento da fatura ?
- Qual o perfil do cliente que tem o limite de crédito abaixo da média ?
- Qual o perfil do cliente que tem o limite de crédito acima da média - 


![02](https://github.com/nickolasdias/marketing/blob/main/Imagens/2.png)


![03](https://github.com/nickolasdias/marketing/blob/main/Imagens/3.png)

![04](https://github.com/nickolasdias/marketing/blob/main/Imagens/4.png)

![05](https://github.com/nickolasdias/marketing/blob/main/Imagens/5.png)

![06](https://github.com/nickolasdias/marketing/blob/main/Imagens/6.png)

![07](https://github.com/nickolasdias/marketing/blob/main/Imagens/7.png)


### 3.1.4 Análise Multivariada

![08](https://github.com/nickolasdias/marketing/blob/main/Imagens/corr.png)

**Algumas Correlações:**

- PURCHASES x ONEOFF_PURCHASES: 0.92
- PURCHASES x INSTALLMENTS_PURCHASES: 0.68
- PURCHASES x PURCHASES_TRX: 0.69
- PAYMENTS x PURCHASES: 0.60
- CASH_ADVANCED x CASH_ADVANCED_FREQUENCY: 0.63
- CASH_ADVANCED_FREQUENCY x CASH_ADVANCED_TRX: 0.80

### 3.1.5 Machine Learning - Definição do Número de Clusters

![09](https://github.com/nickolasdias/marketing/blob/main/Imagens/elbow.png)

**Observação:**

- Número de clusters a ser utilizado: 5


### 3.1.6 Machine Learning - K-Means

O K-means é um algoritmo do tipo não supervisionado, ou seja, que não trabalha com dados rotulados.O objetivo desse algoritmo é encontrar similaridades entre os dados e agrupá-los conforme o número de cluster passado pelo argumento k. O algoritimo calcula a distancia entre dois ponto, utilizando a distancia euclidiana. A distância Euclidiana é a distância mais conhecidas dentre as métricas. Essa distância é a menor distância entre dois pontos no Rn, que pode ser representada pela hipotenusa, observada no Teorema de Pitágoras.

**Clusterização dos Centros**



**Observações:**

- **Grupo 0:** Clientes que realizam compras com forte frequência, tem o terceiro limite do cartão mais alto (4295) e o primeiro mais alto percentual da fatura completa (0.2910).

- **Grupo 1:** Clientes que realizam compras com pouca frequência, porém tem um limite do cartão moderado e o terceiro mais alto percentual de pagamento da fatura completa (0.2257).

- **Grupo 2:** Clientes que realizam compras com baixissima frequência, porém tem um limite do cartão moderado e sacam dinheiro do cartão de crédito com frequência em relação aos outros grupos. Tem um percentual baixissimo de pagamento da fatura completa (0.0249).

- **Grupo 3:** Clientes que realizam compras com forte frequência (0.95), tem limite do cartão mais alto (10131) e o segundo mais alto percentual de pagamento da fatura completa (0.2379).

- **Grupo 4:** Clientes que realizam compras com frequência moderada (0.37), tem o segundo limite de cartão mais alto (8770), sacam dinheiro do cartão de crédito com frequência moderada. Tem o percentual mais baixo de pagamento da fatura completa, porém o pagamento mínimo é o mais alto, em média, de 2990.73 dólares.



### 3.1.6 Conclusão 

Foi realizada a segmentação de clientes do banco de Nova York em que o modelo de clusterização, K-Means, realizou agrupou os clientes em 5 clusters, utilizando como principais características similares: frequência de compras, limite do cartão do de crédito, percentual de pagamento total da fatura, saque de dinheiro do cartão de crédito.

- **Grupo 0:** 3103 clientes
- **Grupo 1:** 1364 clientes
- **Grupo 2:** 3121 clientes
- **Grupo 3:** 318 clientes
- **Grupo 4:** 1044 clientes
