# TRABALHO 01:  E-Market
Trabalho desenvolvido durante a disciplina de BD1

# Sumário

### 1. COMPONENTES<br>
Integrantes do grupo<br>
Felipe Gante Maia de Sousa : gante.ufes@gmail.com<br>
Diego Rodrigo Perez Pacheco : diegopacheco.ufes@gmail.com<br>
...<br>

### 2.INTRODUÇÃO E MOTIVAÇÃO<br>
A empresa "Brabo's Comporation" visa facilitar a vida de todos que neste tempo não estão tendo como sair de casa devido a pandemia do Novo corona virus. Sabendo-se dos desafios ficamos motivados com o desenvolvimento deste sistema. O Sistema "E-Market" tem como objetivo criar uma interface entre o comprador e os mercados. levando alimentos e produtos essenciais para todos e ajudado os mercados a não fecharem as portas.  

### 3.MINI-MUNDO<br>

Minimundo
E-Market
<br>
<br>
<br>
Estamos produzindo um software com o objetivo de terceirizar as compras nesse período de quarentena, permitindo que pessoas em grau de maior de risco possam efetuar as compras sem precisar se expor diretamente. Cada cliente possui, código identificador, nome, cpf, um telefone, e-mail e endereço. O cliente pode realizar uma compra através do menu de itens onde cada cliente pode fazer de nenhum a até vários pedidos independentes. Ao efetuar o pedido, o vendedor reserva os produtos do pedido. O vendedor possui código de identificação e seu nome. O menu é igual para todos os vendedores. Ao fazer o pedido são enviados a quantidade de itens e o código do pedido. Os pedidos vão ser reservados pelo vendedor, retirados do menu e atribuído para o entregador.
<br>


### 4.PROTOTIPAÇÃO, PERGUNTAS A SEREM RESPONDIDAS E TABELA DE DADOS<br>
#### 4.1 RASCUNHOS BÁSICOS DA INTERFACE (MOCKUPS)<br>
![Arquivo PDF do Protótipo Balsamiq do E-Market](https://github.com/FelipeGante/E-Market/blob/master/arquivos/prototipo.pdf?raw=true "E-market prototipo")
#### 4.2 QUAIS PERGUNTAS PODEM SER RESPONDIDAS COM O SISTEMA PROPOSTO?
    O proprietario precisa inicialmente dos seguintes relatórios:
    - Relatório de produtos mais vendidos:Mostrar qual o nome e numero de vendas dos produtos. Ordenados do mais vendido para o menos vendido. 
    - Relatório de frequêcia de Clientes: Mostrar nome e frenquência de compras dos clientes, ordenados de forma crescente em numero de compras efetuadas.
    - Relátorio de Faturamento do mes: mostrar o valor do faturamento do mes. 
    - Relatório de consumo total por cliente: Mostra o nome do cliente e o quanto ele ja gastou no estabelecimento.
    - Relatorio de média de gastos por cliente: mostrar a media de gasto por cliente.


 
#### 4.3 TABELA DE DADOS DO SISTEMA:
    
![Exemplo de Tabela de dados do E-Market](https://github.com/FelipeGante/E-Market/blob/master/arquivos/tabela_pedidos.csv "Tabela - E-Market")
    
    
### 5.MODELO CONCEITUAL<br>
    Modelo feito utilizando o software "Br Modelo 3"    
        
![Alt text](https://github.com/FelipeGante/E-Market/blob/master/images/modelo_conceitual.png?raw=true "Modelo Conceitual")
    
    

    
#### 5.1 Validação do Modelo Conceitual
    [Grupo01]: [Nomes dos que participaram na avaliação]
    [Grupo02]: [Nomes dos que participaram na avaliação]

#### 5.2 Descrição dos dados 
    [Tabela]: [Produto]
    Codigo do produto - Identificador unico para controle dos itens no sistema.
    preço - Preço unitario de um dado produto
    nome do produto - Nome do item cadastrado para identificação por pessoas.

    [Tabela]: [Pedidos]
    Quantidade - Informa no momento do pedido a quantidade associada ao item solicitado.
    Codigo do pedido - Identificador unico para gerênciar cada pedido de forma singular.

    [Tabela]: [Entregador]
    nome - Nome do funcionario ao qual um pedido foi atribuído.
    codigo_entregador - Identificador unico do vendedor para ter um controle sistematico permitindo responsabilização de tarefas.

    [Tabela]: [Cliente]
    cpf - Identificador unico para o cliente baseado em um documento comum e de facil acesso.
    ddd - Código referente a localização do numero do cliente.
    telefone - Numero de contato do cliente.
    nome - Nome do cliente ao qual estará vinculado a solicitação.
    Endereço - Dividido em 4 campos que são rua,bairro,cidade e complemento. Com isso é possivel ter uma melhor precisão das informações obtidas para melhor atender o cliente. 
    


### 6	MODELO LÓGICO<br>
        Modelo Lógico gerado a partir do "Br Modelo 3"
![Alt text](https://github.com/FelipeGante/E-Market/blob/master/images/modelo_logico.png?raw=true "Modelo Lógico")

### 7	MODELO FÍSICO<br>
        Drop das tabelas.
        
        DROP TABLE trabalho_bd."PEDIDOS";
        DROP TABLE trabalho_bd."CLIENTE";
        DROP TABLE trabalho_bd."PRODUTO";
        DROP TABLE trabalho_bd."ENTREGADOR";

        CREATE TABLE trabalho_bd.cliente (
        cpf varchar(11) NOT NULL,
        telefone int4 NOT NULL,
        nome varchar(80) NOT NULL,
        ddd int4 NOT NULL,
        logradouro varchar(20) NULL,
        bairro varchar(20) NULL,
        cidade varchar(20) NULL,
        complemento varchar(20) NULL,
        tipo_logradouro varchar(10) NULL,
        cep int4 NULL,
        numero int4 NULL,
        CONSTRAINT cliente_pkey_1 PRIMARY KEY (cpf)
        );

        CREATE TABLE trabalho_bd.entregador (
        nome_entregador varchar(80) NOT NULL,
        codigo_entregador int4 NOT NULL,
        CONSTRAINT codigo_vendedor_pk_1 PRIMARY KEY (codigo_entregador)
        );

        CREATE TABLE trabalho_bd.pedidos (
        quantidade int4 NULL,
        codigo_pedido int4 NOT NULL,
        cpf_cliente varchar(11) NOT NULL,
        codigo_menu int4 NOT NULL,
        codigo_entregador int4 NOT NULL,
        momento_entrega timestamp NULL,
        data_pedido timestamp NULL,
        CONSTRAINT codigo_pedido_pk_1 PRIMARY KEY (codigo_pedido)
        );

        CREATE TABLE trabalho_bd.produto (
        nome_produto varchar(40) NULL,
        menu int4 NOT NULL,
        preco float8 NULL,
        CONSTRAINT codigo_produto_pk_1 PRIMARY KEY (menu)
        );
        
       
### 8	INSERT APLICADO NAS TABELAS DO BANCO DE DADOS<br>
        Inserção da tabela Cliente

        INSERT INTO trabalho_bd."CLIENTE"
        (cpf, telefone, nome, ddd, rua, bairro, cidade, complemento)
        VALUES(27384539423,995949699,'diego',27,'Arco iris','Nova palestina','vitoria','100'),
        (19547362409,999938469,'joao',27,'Evania','Tabuazeiro','vitoria','apt 400'),
        (22138540328,999992699,'Maria',11,'horacio','Sao joao','vitoria','300'),
        (93452374381,999945999,'Robson',27,'amadeu','consolacao','vitoria','354'),
        (11174503843,999909899,'Rogerio',27,'Prof Adao','Centro','vitoria','bl 4 apt 200'),
        (17439228345,999994899,'Julia',28,'Da luta','Peteleco','Serra','frente a praca'),
        (12853820019,991539999,'pablo',28,'Nossa Senhora','Praia do sua','vitoria','35'),
        (28346837456,992837459,'felipe',27,'Dr Arthur','Ilha do boi','vitoria','252');


        Inserção da tabela MENU

        INSERT INTO trabalho_bd."MENU"
        (codigo_produto,nome_produto,preco)
        VALUES(734,'pizza','30.9'),
        (376,'acerola','5.0'),
        (572,'cafe','4.5'),
        (212,'batata','1.5'),
        (438,'fruta pao','12.0'),
        (883,'bolinho de queijo','11.0'),
        (13,'alvejante','2.5'),
        (616,'repolho','2.3');


        Inserção da tabela VENDEDORES

        INSERT INTO trabalho_bd."VENDEDOR"
        (nome_vendedor ,codigo_vendedor )
        VALUES('Ludovino',23),
        ('Ramilton',65),
        ('Judislayne',12),
        ('Jaraspion',86);

        Inserção DE PEDIDOS

        INSERT INTO trabalho_bd."PEDIDOS"
        (quantidade ,codigo_pedido,clf_cliente ,cod_menu ,cod_vendedor )
        VALUES(6,1,'17439228345',438,12),
        (2,2,'27384539423',883,86),
        (3,3,'12853820019',376,65),
        (6,4,'11174503843',734,65),
        (5,5,'93452374381',13,65),
        (9,6,'93452374381',616,65),
        (3,7,'28346837456',572,65),
        (6,8,'27384539423',438,65),
        (5,9,'12853820019',13,23),
        (3,10,'27384539423',376,86),
        (6,11,'11174503843',438,12),
        (6,12,'19547362409',438,12);

![colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")
        
### 9	TABELAS E PRINCIPAIS CONSULTAS<br>
    OBS: Incluir para cada tópico as instruções SQL + imagens (print da tela) mostrando os resultados.<br>
#### 9.1	CONSULTAS DAS TABELAS COM TODOS OS DADOS INSERIDOS (Todas) <br>
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")
![Consulta clientet](https://github.com/FelipeGante/E-Market/blob/master/images/Consulta_Clientes.png?raw=true "E-market prototipo")
![Consuto Vendedor](https://github.com/FelipeGante/E-Market/blob/master/images/Consulta_vendedor.png?raw=true "E-market prototipo")
![Consulta menu](https://github.com/FelipeGante/E-Market/blob/master/images/Consulta_menu.png?raw=true "E-market prototipo")
![Consulta pedido](https://github.com/FelipeGante/E-Market/blob/master/images/Consulta_pedidos.png?raw=true "E-market prototipo")
#### 9.2	CONSULTAS DAS TABELAS COM FILTROS WHERE (Mínimo 4)<br>
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")
#### 9.3	CONSULTAS QUE USAM OPERADORES LÓGICOS, ARITMÉTICOS E TABELAS OU CAMPOS RENOMEADOS (Mínimo 11)
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

#### 9.4	CONSULTAS QUE USAM OPERADORES LIKE E DATAS (Mínimo 12) <br>
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

#### 9.5	INSTRUÇÕES APLICANDO ATUALIZAÇÃO E EXCLUSÃO DE DADOS (Mínimo 6)<br>
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

#### 9.6	CONSULTAS COM INNER JOIN E ORDER BY (Mínimo 6)<br>
    a) Uma junção que envolva todas as tabelas possuindo no mínimo 2 registros no resultado
    b) Outras junções que o grupo considere como sendo as de principal importância para o trabalho

#### 9.7	CONSULTAS COM GROUP BY E FUNÇÕES DE AGRUPAMENTO (Mínimo 6)<br>
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

#### 9.8	CONSULTAS COM LEFT, RIGHT E FULL JOIN (Mínimo 4)<br>
  !(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

#### 9.9	CONSULTAS COM SELF JOIN E VIEW (Mínimo 6)<br>
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

#### 9.10	SUBCONSULTAS (Mínimo 4)<br>
!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

># Marco de Entrega 02: Do item 9.2 até o ítem 9.10<br>

### 10 RELATÓRIOS E GRÁFICOS

!(colab](https://colab.research.google.com/drive/1kamgOybZT-nBwm08_GRMIv6PSlL4oI_n?usp=sharing "Codigo Colab")

    

### 11	AJUSTES DA DOCUMENTAÇÃO, CRIAÇÃO DOS SLIDES E VÍDEO PARA APRESENTAÇAO FINAL <br>
https://youtu.be/0n5wq25g3_w


### 12 FORMATACAO NO GIT:<br> 
https://help.github.com/articles/basic-writing-and-formatting-syntax/
<comentario no git>
    
##### About Formatting
    https://help.github.com/articles/about-writing-and-formatting-on-github/
    
##### Basic Formatting in Git
    
    https://help.github.com/articles/basic-writing-and-formatting-syntax/#referencing-issues-and-pull-requests
    
    
##### Working with advanced formatting
    https://help.github.com/articles/working-with-advanced-formatting/
#### Mastering Markdown
    https://guides.github.com/features/mastering-markdown/

    
### OBSERVAÇÕES IMPORTANTES

#### Todos os arquivos que fazem parte do projeto (Imagens, pdfs, arquivos fonte, etc..), devem estar presentes no GIT. Os arquivos do projeto vigente não devem ser armazenados em quaisquer outras plataformas.
1. <strong>Caso existam arquivos com conteúdos sigilosos<strong>, comunicar o professor que definirá em conjunto com o grupo a melhor forma de armazenamento do arquivo.

#### Todos os grupos deverão fazer Fork deste repositório e dar permissões administrativas ao usuário do git "profmoisesomena", para acompanhamento do trabalho.

#### Os usuários criados no GIT devem possuir o nome de identificação do aluno (não serão aceitos nomes como Eu123, meuprojeto, pro456, etc). Em caso de dúvida comunicar o professor.


Link para BrModelo:<br>
http://www.sis4.com/brModelo/download.html
<br>


Link para curso de GIT<br>
![https://www.youtube.com/curso_git](https://www.youtube.com/playlist?list=PLo7sFyCeiGUdIyEmHdfbuD2eR4XPDqnN2?raw=true "Title")


