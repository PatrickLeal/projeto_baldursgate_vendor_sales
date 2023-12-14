# Mock Database

Um database de vendas **simulando as vendas de um NPC** dentro de Baldur's Gate. 

## Tópicos:
* [Motivação](#motivação)
* [Planejamento](#planejamento)
* [Etapas](#etapas)
* [Pesquisando Fora do meu Domínio](#pesquisando-fora-do-meu-domínio)
* [Dicionário dos Dados](#dicionário-dos-dados)
* [Fontes](#fontes)


## Motivação
Eu queria uma base de dados para praticar Data Analysis, mas não estava encontrando uma BD interessante então decidi criar uma, escolhi esse tema por causa do meu interesse no jogo Baldur's Gate 3 e porquê o mesmo está em bastante evidência atualmente.
## Planejamento
![fluxo do projeto](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/04e8c08f-eafa-4e0d-b1b6-1383114b1f23)

[↑](#tópicos)

## Etapas:
* Gerar e Traformar dados com [Excel](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/usando_excel.md)
* Criar a [Base de Dados](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/database_creation.ipynb) principal
* Criar os Dados com [Encontros Aleatórios](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/encounters_dataset_creation.ipynb)

[↑](#tópicos)
 
## Pesquisando fora do meu domínio
Para gerar os encontros aleatórios, eu precisei pesquisar sobre o comportamento animal dos três animais que eu escolhi para inspirar as aparições dos monstros que eu decidi utilizar, e foram: 
| monstros | animais/fontes |
|----------|----------------|
| Owlbear  | [Coruja Jacurutu](https://www.wikiaves.com.br/wiki/jacurutu)|
| Dragão   | [Dragão de Komodo](https://pt.wikipedia.org/wiki/Drag%C3%A3o-de-komodo#:~:text=Apesar%20dos%20drag%C3%B5es%2Dde%2Dkomodo,incluindo%20invertebrados%2C%20aves%20e%20mam%C3%ADferos.&text=A%20%C3%A9poca%20de%20reprodu%C3%A7%C3%A3o%20come%C3%A7a,ovos%20s%C3%A3o%20postos%20em%20setembro.)|
| Griffon  | [Harpia Brasileira](https://pt.wikipedia.org/wiki/Gavi%C3%A3o-real)|

<div style="display: inline_block" align="left"><br>
 <img width="200" height="200" src="https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/d3b964fb-cf1e-4b08-a93f-99c32a1ceb97" alt="Jacurutu"/>
 <img width="200" height="200" src="https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/fc58faa8-d1e8-42c6-bf7d-ac1653cb73d0" alt="harpia"/>
 <img width="200" height="200" src="https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/564147cc-705a-4bf2-a27a-4b920b1e6d67" alt="dragao de komodo"/>
</div>

Fonte imagens:
* [Coruja jacurutu](https://pt.wikipedia.org/wiki/Ficheiro:Talons,_Great_Horned_Owl.jpg)
* [Harpia](https://pt.wikipedia.org/wiki/Ficheiro:Harpia_harpyja_001_800.jpg)
* [Dragão de komodo](https://pt.wikipedia.org/wiki/Ficheiro:Varanus_komodoensis6.jpg)

[↑](#tópicos)

## Dicionário dos Dados:

**Relacionamento das tabelta**:
![relacionamento_tabelas](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/7c11e79f-aad8-4cad-bcd9-7b77dbe81fb2)
***

**Moedas**:
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
customer_id| ID do cliente
name| nome do cliente
sex| sexo do cliente
race| raça do cliente
age| idade do cliente
class| classe do cliente
* Nota 1: O range de idade varia de acordo com a raça, com algumas podendo chegar a viver por séculos.

Tabela ***all_products***:
atributo | significado 
---------|-------------
product_id| Id do produto
product_name| nome do produto
price| preço do produto
type| tipo do produto
* Nota 2: ***type*** faz referência à tabela que contém os detalhes do produto, logo '*type* = weapon' significa que o produto pertence a tabela *details_weapons*

As demais tabelas ***details_***:
atributo | significado 
---------|-------------
item_id | ID do item; corresponde ao atributo *product_id* nas outras tabelas
name| nome do produto
price| preço do produto
damage| dano da arma
ac| *armor class*, representa a defesa contra ataque dos monstros
weight| peso do item
requirements| requerimentos do item
stealth| se o item afeta o *stealth* do cliente
dc| *Difficulty Class*, significa o número que é preciso atingir para ser bem sucedido em uma rolagem de dados
properties| propriedade do item
rarity| raridade do item
category| categoria do item
type| tipo do item

* Nota 3: Eu decidi excluir da BD os items de raridades iguais a ***Very Rare*** e ***Legendary***

Tabela [encounters](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/data/encounters.csv):
atributo | significado 
---------|-------------
enc_id| ID do encontro
date| data do encontro
monster| tipo de monstro 
encounter_type| tipo de encontro

[↑](#tópicos)

## **Fontes**
**Itens**:
* https://docs.google.com/spreadsheets/d/1YPjicBYONAtoduyoamiwlVpsV_k1Ki2XzNCAnar5d4Y/edit#gid=0
* https://bg3.wiki/wiki/Items
* https://baldursgate3.wiki.fextralife.com/Weapons
* https://www.thievesguild.cc/shops/
  
**Nomes de Fantasia:**
* https://www.tumblr.com/tabletop-rpgs/183572141838/chris-perkins-npc-name-list

**Moedas:**
* https://dnd5e.info/equipment/currency/

**Raças e Idades:** 
* https://www.reddit.com/r/DnD/comments/97a8to/oc_ive_finally_made_an_expanded_version_of_the/
* https://lairofsentinel.tumblr.com/post/632336501467906048
* https://people.wku.edu/charles.plemons/ad&d/races/age.html
* https://life-of-the-party-dnd.fandom.com/wiki/Races#Dragonborn

**Classes:**
* https://www.dndbeyond.com/sources/basic-rules/classes#ClassesSummary
 
[↑](#tópicos)
