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
