# Mock Database

A sales database **simulating the sales of an NPC** within Baldur's Gate.

## Topics:
* [Motivation](#motivation)
* [Planning](#planning)
* [Stages](#stages)
* [Researching outside my expertise/domain](#researching-outside-my-expertise/domain)
* [Data Dictionary](#data-dictionary)
* [Sources](#sources)


## Motivation
I wanted a database to **practice Data Analysis**, but I wasn't finding an interesting one, so I decided to create one. I chose this theme because of my interest in the game Baldur's Gate 3, and also because it is currently in the spotlight.

## Planning
![fluxo do projeto](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/04e8c08f-eafa-4e0d-b1b6-1383114b1f23)

[↑](#topics)

## Stages:
* Generate and Transform the data with [Excel](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/usando_excel.md)
* Create the [main Database](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/database_creation.ipynb)
* Create the [random encounters data](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/encounters_dataset_creation.ipynb)

[↑](#tópicos)
 
## Researching outside my expertise/domain
To generate random encounters, I needed to research **the animal behavior of the three animals** I chose to inspire the appearances of the monsters I decided to use, which were: 

| monsters | animals/source |
|----------|----------------|
| Owlbear  | [Jacurutu Owl](https://www.wikiaves.com.br/wiki/jacurutu)|
| dragon   | [Komodo Dragon](https://pt.wikipedia.org/wiki/Drag%C3%A3o-de-komodo#:~:text=Apesar%20dos%20drag%C3%B5es%2Dde%2Dkomodo,incluindo%20invertebrados%2C%20aves%20e%20mam%C3%ADferos.&text=A%20%C3%A9poca%20de%20reprodu%C3%A7%C3%A3o%20come%C3%A7a,ovos%20s%C3%A3o%20postos%20em%20setembro.)|
| Griffon  | [Harpy Eagle](https://pt.wikipedia.org/wiki/Gavi%C3%A3o-real)|

<div style="display: inline_block" align="left"><br>
 <img width="200" height="200" src="https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/d3b964fb-cf1e-4b08-a93f-99c32a1ceb97" alt="Jacurutu"/>
 <img width="200" height="200" src="https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/fc58faa8-d1e8-42c6-bf7d-ac1653cb73d0" alt="harpia"/>
 <img width="200" height="200" src="https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/564147cc-705a-4bf2-a27a-4b920b1e6d67" alt="dragao de komodo"/>
</div>

Image Source:
* [Jacurutu](https://pt.wikipedia.org/wiki/Ficheiro:Talons,_Great_Horned_Owl.jpg)
* [Harpy](https://pt.wikipedia.org/wiki/Ficheiro:Harpia_harpyja_001_800.jpg)
* [komodo Dragon](https://pt.wikipedia.org/wiki/Ficheiro:Varanus_komodoensis6.jpg)

[↑](#topics)

## Data Dictionary:

**Relationships between tables**:
![relacionamento_tabelas](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/assets/64172146/7c11e79f-aad8-4cad-bcd9-7b77dbe81fb2)
***

**Currency**:
Coin|	CP|	SP|EP|GP|	PP
--- |---|---|--|--|--
Copper (cp)|	1|	10	|50	|100|	1,000
Silver (sp)	|1/10|	1|	5|	10|	100
Electrum (ep)|	1/50|	1/5|	1|	2|	20
Gold (gp)	|1/100|	1/10|	1/2|	1	|10
Platinum (pp)|1/1,000|	1/100|	1/20|	1/10|	1

***sales*** table:
attributes | meaning 
---------- |-------------
sale_id  | sale ID
date     | sale date
customer_id | customer ID 
product_id | product ID
price    | product price 
product_name | produt name

***customers*** table:

attributes | meaning 
---------- |-------------
customer_id| customer ID
name| customer name
sex| customer gender
race| customer race
age| customer age
class| customer class

* Note 1: The age range varies according to the race, with some being able to live for centuries.

***all_products*** table:
attributes | meaning 
-----------|-------------
product_id| product ID
product_name| product name
price| product price
type| product type
* Note 2: ***type*** references the table that contains the product details, so '*type* = weapon' means that the product belongs to the 'details_weapons' table

The other ***details_*** tables:
attributes | meaning 
-----------|-------------
item_id | Item ID; corresponds to the *product_id* attribute in the other tables
name| product name
price| product price
damage| weapon damage
ac| *armor class*, represents defences againts monster attacks
weight| item weight
requirements| item requeriments
stealth| if the item affects the customer's *stealth*
dc| *Difficulty Class*, means the number that needs to be achieved to succeed in a dice roll
properties| item properties
rarity| item rarity
category| item category
type| item type

* Note 3: I decided to exclude from the database items with rarities ***Very Rare*** and ***Legendary***

[Encounters table](https://github.com/PatrickLeal/projeto_baldursgate_vendor_sales/blob/main/data/encounters.csv):
attributes | meaning 
---------|-------------
enc_id| encounter ID
date| encounter date
monster| monster type 
encounter_type| encounter type

[↑](#topics)

## **Sources**
**Items**:
* https://docs.google.com/spreadsheets/d/1YPjicBYONAtoduyoamiwlVpsV_k1Ki2XzNCAnar5d4Y/edit#gid=0
* https://bg3.wiki/wiki/Items
* https://baldursgate3.wiki.fextralife.com/Weapons
* https://www.thievesguild.cc/shops/
  
**Fantasy names:**
* https://www.tumblr.com/tabletop-rpgs/183572141838/chris-perkins-npc-name-list

**Currency:**
* https://dnd5e.info/equipment/currency/

**Races and lifespans:** 
* https://www.reddit.com/r/DnD/comments/97a8to/oc_ive_finally_made_an_expanded_version_of_the/
* https://lairofsentinel.tumblr.com/post/632336501467906048
* https://people.wku.edu/charles.plemons/ad&d/races/age.html
* https://life-of-the-party-dnd.fandom.com/wiki/Races#Dragonborn

**Classes:**
* https://www.dndbeyond.com/sources/basic-rules/classes#ClassesSummary
 
[↑](#topics)
