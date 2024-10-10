# Criar uma Estratégia de envio

A comunicação entre o estoque, a doca e a política de envio definem a combinação de estrutura para entrega dos pedidos da loja VTEX.

Essa relação é chamada de **estratégia de envio**.

![estrategiadeenvio](https://images.ctfassets.net/alneenqid6w5/1LdEuL3gjF12uwFj4ya6OL/c60984b010b96980383798cffad3527f/shipping_strategy_PT.png)

Para acessar a página de estratéia de envio, é necessário acessar, no Admin, **Envio > Estratégia de envio** ou pesquisar por **Estratégia de Envio** na barra de busca.

O módulo Envio é responsável pelas configurações logísticas da sua loja VTEX. É nele que a loja gerencia o inventário, as tarifas de envio, a disponibilidade de itens e as entregas.

Na aba Estratégia de envio, você pode configurar e visualizar as informações já configuradas do estoque, doca e política de envio, além de relacionar cada uma dessas etapas da estratégia de envio.

![estrategiadeenvioadmin](https://i.ibb.co/rfX4cph/Captura-de-tela-2024-10-09-192335.png)

>Importante: antes de configurar a logística da sua loja, você precisa configurar:
>
> 1. [Política comercial](https://help.vtex.com/pt/tutorial/criar-uma-politica-comercial--563tbcL0TYKEKeOY4IAgAE)
>
> 2. [Catálogo](https://help.vtex.com/pt/tracks/catalogo-101--5AF0XfnjfWeopIFBgs3LIQ/3rA2tTpIoEXdv2nzC27zxR)
>
> 3. [Preços](https://help.vtex.com/pt/tracks/precos-101--6f8pwCns3PJHqMvQSugNfP/3N9xYhnampRQOrfaTAOxNu)

## Definições e configurações logísticas

As configurações podem ser realizadas pelo Admin VTEX ou por API. Se você está iniciando as configurações de estratégia de envio da loja, a ordem de cadastro sugerida é a seguinte:

### **[1. Política de Envio](https://help.vtex.com/pt/tutorial/politica-de-envio--tutorials_140)**

A política de envo é um conjunto de regras acordadas entre lojas e [transportadoras](https://help.vtex.com/pt/tutorial/o-que-e-uma-transportadora--7u9duMD5UQa2QQwukAWMcE) que definem as opções e condições de frete que serão apresentadas ao consumidor no momento da finalização da compra. A partir dessas regras, a plataforma filtra e calcula quais transportadoras satisfazem as condições do pedido. A política de envio também é utilizada para selecionar o envio por [pontos de retirada](https://help.vtex.com/pt/tutorial/pontos-de-retirada--2fljn6wLjn8M4lJHA6HP3R).

Para criar uma política de envio, após acessar a página de **Estratégia de Envio** no Admin:

Clique no botão ``Criar política de envio``.

Preencha os campos da tela descritos e em seguida clique em ``Salvar aterações``.

Para conferir mais detalhes de como realizar essa configuração através do Admin, acesse:
[Criar uma política de envio](https://help.vtex.com/pt/tutorial/criar-uma-politica-de-envio--66rJO4LKBdyMJOH6Z3dsaT).

> Para realizar essa configuração via API:
> [Create shipping policy](https://developers.vtex.com/docs/api-reference/logistics-api#post-/api/logistics/pvt/shipping-policies)

### **[2. Planilha de frete](https://help.vtex.com/pt/tutorial/planilha-de-frete--tutorials_127)**

A planilha de fretes é a planilha de cadastro dos preços de envio que serão oferecidos aos seus clientes. Ela contém informações como os intervalos de código postal, o peso aceito e o valor do serviço cobrado pela empresa que realizará a entrega.

Para cadastrar preços de envio pela planilha de frete:

[Preencha os campos da planilha](https://help.vtex.com/pt/tutorial/planilha-de-frete--tutorials_127#preencher-os-campos-da-planilha)

[Envie o arquivo pelo Admin VTEX](https://help.vtex.com/pt/tutorial/planilha-de-frete--tutorials_127#enviar-o-arquivo-pelo-admin-vtex) dentro das configurações da política de envio desejada.

Para conferir mais detalhes de como realizar essa configuração através do Admin, acesse:
[Planilha de frete](https://help.vtex.com/pt/tutorial/planilha-de-frete--tutorials_127).

### **[3. Doca](https://help.vtex.com/pt/tutorial/doca--5DY8xHEjOLYDVL41Urd5qj)**.

A doca é parte do sistema logístico e geralmente funciona como ponto intermediário entre estoques e transportadoras. Na doca, as transportadoras recolhem os itens para entregá-los para seus destinatários.

Para cadastrar uma nova doca, após acessar a página de **Estratégia de Envio** no Admin:

Vá na aba Docas e clique no botão ``Criar Doca``.

Preencha os campos de cadastro e clique em ``Salvar``.

Para conferir mais detalhes de como realizar essa configuração através do Admin, acesse:
[Gerenciar Doca](https://help.vtex.com/pt/tutorial/gerenciar-doca--7K3FultD8I2cuuA6iyGEiW).

> Para realizar essa configuração via API:
> [Create/update dock](https://developers.vtex.com/docs/api-reference/logistics-api#post-/api/logistics/pvt/configuration/docks)

### **[4. Estoque](https://help.vtex.com/pt/tutorial/estoque--6oIxvsVDTtGpO7y6zwhGpb)**

O estoque é a quantidade de mercadorias armazenadas num depósito ou numa loja. Funciona como ferramenta de controle de disponibilidade de produtos.

Para cadastrar um novo estoque, após acessar a página de **Estratégia de Envio** no Admin:

Clique na aba ``Estoques``.

Clique no botão ``Criar estoque``.

Confira se o botão  está como Ativo no canto superior direito. Caso não esteja mude-o para Ativo.

Preencha os [campos de cadastro](https://help.vtex.com/pt/tutorial/gerenciar-estoque--tutorials_137#campos-de-cadastro).

Clique no botão ``Salvar alterações``.

Para conferir mais detalhes de como realizar essa configuração através do Admin, acesse:
[Gerenciar Estoque](https://help.vtex.com/pt/tutorial/gerenciar-estoque--tutorials_137).


> Para realizar essa configuração via API:
> [Create/update warehouse](https://developers.vtex.com/docs/api-reference/logistics-api#post-/api/logistics/pvt/configuration/warehouses)

#### Observação: Pontos de Retirada

Para algumas estratégias de negócio, as lojas oferecem [pontos de retirada](https://help.vtex.com/pt/tutorial/como-funcionam-pontos-de-retirada--2fljn6wLjn8M4lJHA6HP3R), locais onde o cliente pode retirar seu pedido. Para realizar essa configuração é necessário, primeiramente, cadastrar o ponto de retirada para depois realizar as configurações de uma estratégia de envio que atenda esse ponto de retirada. Isso ocorre porque a plataforma também calcula os pontos de retirada disponíveis a partir da localização do cliente, conferindo o estoque, a doca e o transporte para que o produto fique disponível para retirada.

> Para realizar essa configuração via API:
> [Create or update pickup point
](https://developers.vtex.com/docs/api-reference/logistics-api#put-/api/logistics/pvt/configuration/pickuppoints/-pickupPointId-)

O ponto de retirada fica disponível no checkout como uma opção de envio, e o cliente escolhe entre Entrega (transportadora) e Retirada (ponto de retirada).

## Validando configurações: Simulador de Envio
Após configurar as estratégias de envio e adicionar estoque para os SKUs através do [inventário](https://help.vtex.com/pt/tutorial/gerenciar-itens-em-estoque--tutorials_139), é importante validar se essas configurações estão refletindo de acordo com o esperado, ou seja, se realmente os produtos cadastrados no inventário fornecem opções de envio para os clientes, possibilitando a criação de carrinhos e pedidos.

O [simulador de envio](https://help.vtex.com/pt/tutorial/simulador-de-envio--tutorials_144) permite que os lojistas verifiquem os cenários de entrega disponíveis para o produto em uma localidade específica.

Através da ferramenta, é possível conferir:

* A disponibilidade de entrega do produto em determinada região.

* As formas de envio para o produto.

* As transportadoras que podem realizar a entrega.

* Os motivos pelos quais algumas transportadoras foram desconsideradas para o envio.

* O prazo de entrega do produto.

* As tarifas de envio existentes.

* O seller white label que realizará a entrega do produto.

> Realize simulações também através das APIs:
>
> [API de cálculo de SLA ](https://developers.vtex.com/docs/api-reference/logistics-api#post-/api/logistics/pvt/shipping/calculate)
>
> [API de simulação de carrinho](https://developers.vtex.com/docs/api-reference/checkout-api#post-/api/checkout/pub/orderForms/simulation)
