# Mock Database

Um database de vendas simulando as vendas de um NPC dentro de Baldur's Gate. 
## Motivação
Eu queria uma base de dados para praticar Data Analysis, mas não estava encontrando uma BD interessante então decidi criar uma, escolhi esse tema por causa do meu interesse no jogo Baldur's Gate 3 e porquê o mesmo está em bastante evidência atualmente.
## Planejamento
![fluxo do projeto](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/04e8c08f-eafa-4e0d-b1b6-1383114b1f23)
## Etapas:
* Gerar e Traformar dados com [Excel](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/usando_excel.md)
* Criar a [Base de Dados](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/database_creation.ipynb) principal
* Criar os Dados com [Encontros Aleatórios](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/encounters_dataset_creation.ipynb)
## Pesquisando fora do meu domínio
Para gerar os encontros aleatórios, eu precisei pesquisar sobre o comportamento animal dos três animais que eu escolhi para inspirar as aparições dos montros que eu decidi utilizar, e foram: 
| monstros | animais/fontes |
|----------|----------------|
| Owlbear  | [Coruja Jacurutu](https://www.wikiaves.com.br/wiki/jacurutu)|
| Dragão   | [Dragão de Komodo](https://pt.wikipedia.org/wiki/Drag%C3%A3o-de-komodo#:~:text=Apesar%20dos%20drag%C3%B5es%2Dde%2Dkomodo,incluindo%20invertebrados%2C%20aves%20e%20mam%C3%ADferos.&text=A%20%C3%A9poca%20de%20reprodu%C3%A7%C3%A3o%20come%C3%A7a,ovos%20s%C3%A3o%20postos%20em%20setembro.)|
| Griffon  | [Harpia Brasileira](https://pt.wikipedia.org/wiki/Gavi%C3%A3o-real)|

## Dicionário dos Dados:
Moedas:
Coin|	CP|	SP|EP|GP|	PP
--- |---|---|--|--|--
Copper (cp)|	1|	10	|50	|100|	1,000
Silver (sp)	|1/10|	1|	5|	10|	100
Electrum (ep)|	1/50|	1/5|	1|	2|	20
Gold (gp)	|1/100|	1/10|	1/2|	1	|10
Platinum (pp)|1/1,000|	1/100|	1/20|	1/10|	1

Tabela ***sales***:
atributo | significado 
---------|-------------
sale_id  | ID da venda 
date     | data da venda 
customer_id | ID do cliente 
product_id | ID do produto 
price    | preço do produto 
product_name | nome do produto 

Tabela ***customers***:

atributo | significado 
---------|-------------
customer-id| ID do cliente
name| nome do cliente
sex| sexo do cliente
race| raça do cliente
age| idade do cliente
class| classe do cliente
* Nota1: O range de idade varia de acordo com a raça, com algumas podendo chegar a viver por séculos.

Tabela ***all_products***:
atributo | significado 
---------|-------------
product_id| Id do produto
product_name| nome do produto
price| preço do produto
type| tipo do produto
* Nota2: ***type*** faz referência à tabela que contém os detalhes do produto, logo '*type* = weapon' significa que o produto pertence a tabela *details_weapons*


