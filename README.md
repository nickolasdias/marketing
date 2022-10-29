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

![20](https://github.com/nickolasdias/marketing/blob/main/Imagens/11.png)

**Algumas Observações:**

- O saldo para fazer compras em média é 1564.47 dólares
- Em média a atualização de saldo dos clientes é de 88%.
- Em média, os clientes gastam 1003.20 dólares com compras.
- Em média, os clientes gastam 592.44 dólares com compras a vista.
- Em média, os clientes gastam 411.07 dólares com compras parceladas.
- Em média, 36.44% dos clientes preferem fazer compras parceladas com frequência do que compras a vista (20.25%).
- Em média, 13.51% dos clientes sacam dinheiro do crédito com frequência.
- Em média, o limite do cartão dos clientes é de 4494.45 dólares.
- Em média, 15.37% dos clientes pagam a fatura completa.
- Em média, os clientes estão há 12 anos ativos no banco.


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


### 3.1.3 Análise de Dados - Validação de Hipóteses


#### 3.1.3.1 Qual o perfil do cliente que realizou a compra a vista mais cara ?

![02](https://github.com/nickolasdias/marketing/blob/main/Imagens/1.png)

**Observações:**

- Cliente que atualiza o saldo com frequência.
- Cliente que compra com frequencia, porém prefere fazer mais compras a vista do que parceladas.
- Cliente que saca pouco do dinheiro disponível do cartão de crédito
- Paga somente 25% da fatura total, ou seja, prefere pagar somente o minimo da fatura do cartão, por não usar tanto o cartão de crédi

#### 3.1.3.2 Qual o perfil do cliente que realizou a compra parcelada mais cara ?

![03](https://github.com/nickolasdias/marketing/blob/main/Imagens/2.png)

**Observações:**

- Cliente que mantém seu saldo atualizado moderadamente
- Cliente que não realiza compras a vista, só compras parceladas.
- Cliente que não costuma comprar com tanta frequência e nem sacar dinheiro do crédito.
- Cliente que não paga a fatura total.


#### 3.1.3.3 Qual o perfil do cliente que sacou dinheiro do crédito mais alto ?

![04](https://github.com/nickolasdias/marketing/blob/main/Imagens/3.png)

**Observações**

- Cliente que mantém seu saldo atualizado com frequência.
- Cliente que não realiza compras a vista e nem compras parceladas.
- Cliente que realiza saques de dinheiro do crédito com frequência.
- Cliente que não paga a fatura total somente o pagamento mínimo.


#### 3.1.3.4 Qual o perfil do cliente que faz o pagamento total da fatura ?

![05](https://github.com/nickolasdias/marketing/blob/main/Imagens/4.png)

**Observações:**

- 5.45% dos clientes fazem o pagamento total da fatura
- 50% dos clientes tem limite de crédito, em média, de 4000 dólares.
- Clientes tem uma frequencia de compra, em média, de 70%.
- Clientes praticamente não realizam saque de dinheiro do cartão de crédito.
- Clientes realizaram 23 compras em média.


#### 3.1.3.5 Qual o perfil do cliente que não faz o pagamento da fatura ?

![06](https://github.com/nickolasdias/marketing/blob/main/Imagens/5.png)

**Observações:**

- 65.95% dos clientes não pagam a fatura
- 50% dos clientes tem limite de crédito, em média, de 3000 dólares.
- Clientes tem uma frequência de compra, em média, de 41.27%.
- Clientes sacam dinheiro do cartão de crédito com frequência de 16.20%. em média.
- Clientes realizaram em média de 12 compras.


#### 3.1.3.6 Qual o perfil do cliente que tem o limite de crédito abaixo da média ?

![07](https://github.com/nickolasdias/marketing/blob/main/Imagens/6.png)

**Observações:**

- 60.32% dos clientes tem limite de crédito abaixo da média.
- Clientes tem saldo para compra. em média, de 840 dólares.
- Clientes tem uma frequencia de compra, em média, de 45%, sendo com realizações maiores de compras parceladas.
- Clientes pagam a fatura total, em média, de 14.46%.
- Clientes realizaram 10 compras em média.


#### 3.1.3.7 Qual o perfil do cliente que tem o limite de crédito acima da média ?

![20](https://github.com/nickolasdias/marketing/blob/main/Imagens/7.png)

**Observações:**

- 39.66% dos clientes tem limite de crédito acima da média.
- Clientes tem saldo para compra, em média, de 2667.29 dólares.
- Clientes tem uma frequencia de compra, em média, de 40%.
- Clientes pagam a fatura total, em média, de 30.96%.
- Clientes realizaram 22 compras em média.


### 3.1.4 Análise Multivariada

![08](https://github.com/nickolasdias/marketing/blob/main/Imagens/corr.png)

**Algumas Correlações:**

- PURCHASES x ONEOFF_PURCHASES: 0.92
- PURCHASES x INSTALLMENTS_PURCHASES: 0.68
- PURCHASES x PURCHASES_TRX: 0.69
- PAYMENTS x PURCHASES: 0.60
- CASH_ADVANCED x CASH_ADVANCED_FREQUENCY: 0.63
- CASH_ADVANCED_FREQUENCY x CASH_ADVANCED_TRX: 0.80


### 3.1.5 Filtro de Variáveis - Seleção de Variáveis

O critério para a seleção de variáveis é eliminar aqueles atributos que possuem o conceito multicolinearidade, ou seja, variáveis que explicam o mesmo fenômeno conforme as correlações.

Exclusão das variáveis: 'CUST_ID', 'ONEOFF_PURCHASES', 'INSTALLMENTS_PURCHASES', 'ONEOFF_PURCHASES_FREQUENCY', 'PURCHASES_INSTALLMENTS_FREQUENCY', e 'CASH_ADVANCE'.

### 3.1.6 Machine Learning - Definição do Número de Clusters

- https://en.wikipedia.org/wiki/Elbow_method_(clustering)
- https://www.geeksforgeeks.org/elbow-method-for-optimal-value-of-k-in-kmeans/

O Método Elbow é conhecido como método do cotovelo. Basicamente o que o método faz é testar a variância dos dados em relação ao número de clusters. A partir do valor indicado pelo “cotovelo” no gráfico significa que não existe ganho em relação ao aumento de clusters.

![09](https://github.com/nickolasdias/marketing/blob/main/Imagens/elbow.png)

**Observação:**

- Número de clusters a ser utilizado: 5


### 3.1.7 Machine Learning - K-Means

O K-means é um algoritmo do tipo não supervisionado, ou seja, que não trabalha com dados rotulados.O objetivo desse algoritmo é encontrar similaridades entre os dados e agrupá-los conforme o número de cluster passado pelo argumento k. O algoritimo calcula a distancia entre dois ponto, utilizando a distancia euclidiana. A distância Euclidiana é a distância mais conhecidas dentre as métricas. Essa distância é a menor distância entre dois pontos no Rn, que pode ser representada pela hipotenusa, observada no Teorema de Pitágoras.

**Clusterização dos Centros**

![32](https://github.com/nickolasdias/marketing/blob/main/Imagens/22.png)

**Observações:**

- **Grupo 0:** Clientes que realizam compras com forte frequência, tem o terceiro limite do cartão mais alto (4295) e o primeiro mais alto percentual da fatura completa (0.2910).

- **Grupo 1:** Clientes que realizam compras com pouca frequência, porém tem um limite do cartão moderado e o terceiro mais alto percentual de pagamento da fatura completa (0.2257).

- **Grupo 2:** Clientes que realizam compras com baixissima frequência, porém tem um limite do cartão moderado e sacam dinheiro do cartão de crédito com frequência em relação aos outros grupos. Tem um percentual baixissimo de pagamento da fatura completa (0.0249).

- **Grupo 3:** Clientes que realizam compras com forte frequência (0.95), tem limite do cartão mais alto (10131) e o segundo mais alto percentual de pagamento da fatura completa (0.2379).

- **Grupo 4:** Clientes que realizam compras com frequência moderada (0.37), tem o segundo limite de cartão mais alto (8770), sacam dinheiro do cartão de crédito com frequência moderada. Tem o percentual mais baixo de pagamento da fatura completa, porém o pagamento mínimo é o mais alto, em média, de 2990.73 dólares.



### 3.1.8 Conclusão 

Foi realizada a segmentação de clientes do banco de Nova York em que o modelo de clusterização, K-Means, realizou agrupou os clientes em 5 clusters, utilizando como principais características similares: frequência de compras, limite do cartão do de crédito, percentual de pagamento total da fatura, saque de dinheiro do cartão de crédito.

- **Grupo 0:** 3103 clientes
- **Grupo 1:** 1364 clientes
- **Grupo 2:** 3121 clientes
- **Grupo 3:** 318 clientes
- **Grupo 4:** 1044 clientes
