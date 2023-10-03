# Dicionário de Dados (DD)

O dicionário de dados oferece uma visão geral das principais entidades, atributos e terminologia utilizados neste projeto.

## Entidade: Dimensão

#### Descrição: Armazena informações relacionada as dimensões
#### Observações: Esta tabela não possui chave estrangeira
<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idDimensão|Identificador da dimensão|Int||PK|
|nome|Nome da dimensão|VarChar|20|Not Null|
|tamanho|Tamanho da dimensão|Int||Not Null|

<br><br>

## Viagem

#### Descrição: Armazena informações de viagem entre dimensões
#### Observações: Essa tabela possui chaves estrangeiras da tabela Dimensão
<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|origem|	Dimensão de origem da viagem|	VarChar|	20|	FK|
|destino|	Dimensão de destino da viagem|	VarChar|	20|	FK|

<br><br>

## Entidade: Local

#### Descrição: Armazena informações relacionada ao local
#### Observações: Essa tabela possui chave estrangeira da tabela Dimensão			
<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idLocal|Identificador do local|Int||PK|
|idDimensao|Chave estrangeira referenciando o identidicador de Dimensão|Int|20|FK|
|tamanho|Tamanho do local|Int||Not Null|
|bioma|Bioma do local|VarChar||Not Null|

<br><br>

## Entidade: Efeito de Ambiente

#### Descrição: Armazena informações dos efeitos de ambiente
#### Observações: Essa tabela possui chave estrangeira da tabela Local

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idEfeitoAmbiente|Identificador do efeito de ambiente|Int||PK|
|idLocal|Chave estrangeira referenciando identificador do local|Int||FK|			
|duracao|	Duração do efeito de ambiente|	Float|		|Check|
|intensidade	|Intensidade do efeito de ambiente	|VarChar	|20	|Not Null|
|tipo	|Tipo do efeito de ambiente|	VarChar|	20|	Not Null|


<br><br>

## Entidade: Estrutura

#### Descrição: Armazena informações de estruturas
#### Observações: Essa tabela possui chave estrangeira da tabela Local

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idEstrutura|	Identificador da estrutura|	Int||		PK|
|idLocal	|Chave estrangeira referenciando identificador do local|Int|		|FK|			
|tamanho|	Tamanho da estrutura|	Int|		|Not Null|

<br><br>

## Entidade: Personagem

#### Descrição: Armazena informações de Personagem
#### Observações: Essa tabela não possui chave estrangeira

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idPersonagem|	Identificador do personagem|	Int|		|PK|
|nome	|Nome do personagem	|VarChar	|20	|Not Null|
|tipo	|Tipo do personagem	|VarChar|	20|	Not Null|
|vida	|Vida do personagem	|Int|		|Check|


<br><br>

## Entidade: PC

#### Descrição: Armazena informações do Player Character (Personagem jogável)
#### Observações: Essa tabela possui chave estrangeira da tabela Personagem

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idPC|	Identificador do personagem jogável|	Int||		PK|
|idPersonagem|	Chave estrangeira referenciando identificador do personagem |Int|		|FK|			
|nivel|	Nível do personagem jogável|	Int||		Check|
|localNascimento|	Local de nascimento do personagem jogável|	VarChar|	20|	Not Null|


<br><br>

## Entidade: NPC

#### Descrição: Armazena informações do Not Player Character (Personagem não jogável)
#### Observações: Essa tabela possui chave estrangeira da tabela Personagem

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idNPC|	Identificador do npc|	Int||		PK|
|idPersonagem|	Chave estrangeira referenciando	identificador do personagem|	 	Int||		FK|
|hostilidade|	Hostilidade do npc|	VarChar|	20|	Not Null|
|danoCausado|	Dano causado pelo npc|	Int|		| Check|

<br><br>

## Entidade: Instância

#### Descrição: Armazena informações de vida e morte de NPCs específicos
#### Observações: Essa tabela possui chave estrangeira das tabelas NPC e Local

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idNPC|	Chave estrangeira referenciando identificador do npc|	Int||		FK|		
|idLocal|	Chave estrangeira referenciando identificador do local|	Int||		FK|

<br><br>


## Entidade: Missão		
			
#### Descrição: Armazena informações das Missões
#### Observações: Essa tabela possui chave estrangeira da tabela NPC		

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idMissao|	identificador de missão|	Int|	|	PK|
idNPC|	chave estrangeira referenciando identificador de NPC|	Int| |		FK|			
|descrição|	descrição da missão|	VarChar|	100|	NotNull|
|objetivo|	objetivo da missão|	VarChar|	30|	NotNull|
|recompensa|	recompensa da missão (item e/ou conquista)|||			NotNull|

<br><br>


## Entidade: Conquista

#### Descrição: Armazena informações de conquistas
#### Observações: Essa tabela possui chave estrangeira da tabela PC	

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idConquista|	Identificador da conquista|	Int||		PK|
|idMissao| Identificador de missão | Int || FK |
|idPC|	Chave estrangeira referenciando identificador do personagem jogável|	Int||		FK|
|titulo|	Nome identificador da conquista|	VarChar|	50|	Not Null|
|descricao|	Descrição da conquista|	VarChar|	50|	Not Null|


<br><br>


## Entidade: Inventário

#### Descrição: Armazena informações do inventário
#### Observações: Essa tabela possui chave estrangeira da tabela PC

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idInventario|	Identificador do inventário|	Int||		PK|
|personagem	|Chave estrangeira referenciando o identificador do personagem jogável|	Int||		FK|
|tamanho|	Tamanho do inventário|	Int||		Not Null|

<br><br>


## Entidade: Item

#### Descrição: Armazena informações dos itens
#### Observações: Essa tabela possui chave estrangeira da tabela Inventário

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idItem|	Identificador do item|	Int||		PK|
|idInventario|	Chave estrangeira referenciando identificador do inventário| 	Int||		FK|
|tipo|	Tipo do item|	VarChar|	20|	Not Null|
|durabilidade|	Durabilidade do item|	Int||		Default|


<br><br>


## Entidade: Consumível

#### Descrição: Armazena informações dos itens consumíveis
#### Observações: Essa tabela possui chave estrangeira da tabela Item

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idItemConsumivel|	Identificador do item consumível|	Int||		PK|
|idItem|	Chave estrangeira referenciando identificador do item|	Int||		FK|		
|quatidadeUso|	Quantidade de uso do item consumível|	Int||		Check|


<br><br>

## Entidade: Não-consumível	

#### Descrição: Armazena informações dos itens não consumíveis
#### Observações: Essa tabela possui chave estrangeira da tabela Item

<!-- Tabela-->
| Nome     | Descrição | Tipo de Dado | Tamanho | Restrições de Domínio |
|:--------:|:---------:|:------------:|:-------:|:---------------------:|
|idItemNC|	Identificador do item não consumível|	Int||		PK|
|idItem|	Chave estrangeira referenciando identificador do item|	Int||		FK|	
|resistencia|	Resistência do item não consumível|	Int||		Check|
|dano|	Dano do item não consumível|	Int||		Check|
|efeito|	Efeito do item não consumível|	VarChar|	20|	Not Null|	

| Versão |  Data | Descrição | Autor |
| :----: | :---: | --------- | ----- |
| 1.0    | 24/09/2023 | Criação do Dicionario de Dados | [Nicolas](https://github.com/NickGehjk) |
| 1.1 | 25/09/2023 | Adição do Dicionário no ReadMe | [Victor Hugo](https://github.com/ViictorHugoo) |
| 1.2 | 01/10/2023 | Alterações no Dicionário de Dados | [Maria Alice](https://github.com/Maliz30) <br> [Victor Hugo](https://github.com/ViictorHugoo) 
