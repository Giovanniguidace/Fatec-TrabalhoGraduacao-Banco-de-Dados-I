# Portfólio TG - API's - Trabalho de Graduação em BD I

#
<h2>Participações em API's: 5
</h2> 

<h3>1º Semestre:</h3>

* <B>Projeto Web BOT:</b>

<b>Objetivo do API:</b>
		<p>O objetivo do API do primeiro semestre, consiste em criar um WEBBOT para automatizar qualquer tipo de operação que será escolhida de forma livre entre as equipes. </p>


<b>Objetivo do Projeto:</b>

Criar um WebBOT capaz de realizar a leitura de CNPJ's de todas as empresas de São José dos Campos e realizar a leitura de qual o tipo de ramo cada empresa. Será possível também, validar qual o capital a empresa possui e se ela está inativa ou ativa.

Com este valores coletados e os pontos inseridos no mapa, será possível visualizar em regiões de São José dos Campos quais delas possuem uma maior quantia de empresa de determinado ramo e capital. 

É possível selecionar no mapa qual ramo e capital deverá ser filtrado. Esta opção é disponibilizada aos usuários para que possam saber se determinada região compensa um possível investimento em determinado ramo.

<b>Tecnologias Adotadas na Solução:</b>

* Slack - Motivo: Utilizado como meio principal de contato entre a equipe;
* Visual Studio Code - Motivo: De acordo com votação em equipe, foi decidido a utilização desta ferramenta para desenvolvimento do código;
* MongoDB - Motivo: De acordo com votação em equipe, foi utilizado este banco não relacional para armazenar dados de CNPJ, Ramo da empresa, Latitude e Longitude, Capital;
* Django/Python: Motivo: De acordo com votação em equipe, foi decidido pelo Django Framework devido a sua linguagem ser em python e pela possibilidade de utilizar bibliotecas de geolocalização, organização de dados, entre outros...

	<b>Bibliotecas Python Utilizadas:</b>
	*   Selenium - Utilizado para coletar informações de empresa e geolocalização em sites;
	*   OS - Biblioteca Python;
	*   Math - Biblioteca Python;
	*   Pymongo - Utilizado para conectar no servidor do BD NoSQL Mongo;
	*   Folium - Utilizado para apontar Latitude e Longitude no mapa geográfico;
	*   Pandas - Utilizado para organizar dados de empresa e posteriormente enviar para a biblioteca Folium;

<b>Contribuições individuais/pessoais</b>

* Levantamento de tecnologias a serem utilizadas;
* Auxilio no levantamento dos objetivos do projeto;
* Coletar Latitude e Longitude de cada empresa e apontar em um mapa os pontos utilizando a biblioteca Folium e Pandas;
* Apresentação do projeto;

<b>Aprendizados Efetivos</b>

* Trabalho em equipe utilizando a metodologia ágil SCRUM;
* Aprofundamento na linguagem Python e as bibliotecas Folium e Pandas;
* Organização de projeto e documentação;
* Inicialização no framework Django;
* Funcionamento de web scraping;

#
#
<h3>2º Semestre:</h3>

* <B>Projeto GANTT PLANNER - Grupo PHPYTHON:</b>


<b>Objetivo do API:</b>

O desenvolvimento desse projeto partiu de uma demanda da empresa Necto, a partir de seu CEO Carlos Eduardo, que era de uma ferramenta que fosse fácil de mexer, que fosse portátil e ao mesmo tempo flexível para auxiliar no planejamento de seus projetos. Manipular um gráfico de Gantt afim de conquistar esses objetivos será o cerne do projeto. Outro fator decisivo para o desenvolvimento é a limitação que outras ferramentas semelhantes à do nosso projeto que impossibilitam ou dificultam muito a visualização da empresa como um todo, afim de conseguir conciliar o desenvolvimento de vários projetos simultaneamente com a distribuição da equipe da melhor forma possível, além de ter uma melhor distribuição dos recursos financeiros.

Para equipes que trabalham em múltiplos projetos e tarefas, que estão insatisfeitas com a dificuldade de fazer um planejamento com as ferramentas de planejamento disponíveis, o Gantt Planner é uma ferramenta visual de planejamento que auxilia o desenvolvimento do seu planejamento, minimizando os riscos de má distribuição de mão de obra, perder prazos e compreensão da evolução das tarefas. Ao contrário de outras ferramentas de planejamento conhecidas, nosso projeto oferece gráficos e relatórios completos e agradáveis com a possibilidade de compartilhamento do gráfico do planejamento como imagem para o time.

<b>Objetivo do Projeto:</b>

Para que seja criada uma aplicação que atenda os requisitos solicitados pelo cliente, foram levantadas as seguintes necessidades:

* Cadastro de Pessoa:
	* Foi realizada a implementação do cadastro de pessoa para que o cliente pudesse inclui-lo nas tarefas e projetos, que posteriormente seriam visualizados no gráfico de GANTT. O cadastro de pessoas consiste em informações básicas de um funcionário e também com a possibilidade de classificá-lo com uma função do projeto ou o cargo que ele possui.
	
* Cadastro de Tarefa:
	* Foi realizada a implementação do cadastro de tarefa com a finalidade de inserir pessoas que serão contribuintes desta tarefa que pertencerá a um projeto. A tarefa possui as informações como descrição da tarefa, data de conclusão, pessoas que farão parte e qual o projeto que ela pertence.

* Cadastro de projeto:
	* Foi realizada a implementação do cadastro de projeto, onde ele terá as tarefas vinculadas a ele e nessas tarefas quem serão os executores. Desta forma, é possível jogar todas as informações necessárias para gerar o gráfico do GANTT.

* Cadastro de distribuição de tarefas:
	* Foi realizada a implementação do cadastro de distribuição de tarefas as pessoas, onde torna possível vincular uma tarefa a uma pessoa que fará parte do projeto.

* Relatórios:
	* Foi realizada a implementação de relatórios que torna possível a visualização do andamento do projeto, as tarefas que estão vinculadas a ele e as pessoas que estão vinculadas a esta tarefa. Também é possível visualizar datas de conclusão de cada tarefa.

Com a implementação destas funcionalidades em nosso projeto, foi possível disponibilizar ao cliente uma aplicação capaz de organizar projetos de desenvolvimento, dividido em tarefas e pessoas, com data de conclusão e uma prévia de conclusão de projeto.

<b>Tecnologias Adotadas na Solução:</b>
-   Python - Motivo: Foi realizada uma votação para a utilização da linguagem Python, pois pensamos em utilizar o framework Django;
-   PostgreSQL - Motivo: Foi realizada uma votação em que a escolha do banco de dados foi o PostgreSQL devido à todos do grupo já terem uma familiaridade com este SGBD;
-   HTML - Motivo: Utilização de Front-End na aplicação;
-   JavaScript e CSS - Motivo: Foi realizado o uso das linguagens Javascript e CSS para a criação do layout e requisições GET, POST, DELETE E PUT para o manuseio de dados vindo do BackEnd. Também foi utilizada a linguagem Javascript para se comunicar com a API do Frappe e utilizar o gráfico de Gantt;
-   Django (Framework Python) - Motivo: Foi escolhido framework Django devido a sua utilização no projeto anterior e por ter uma maior facilidade na criação de API's;
-   Maquina Virtual - Motivo: Foram realizadas implementações de código dentro de máquinas virtuais, onde era possível transportar para utilização em computadores da Fatec;
-   GitLab - Motivo: Foi realizada a escolha opr votação do repositório do Gitlab, pois foi este o reposit´roio escolhido no projeto anterior;
-   Whats App - Motivo: Foi escolhido por votação a utilização da ferramenta de mensagem do Whatsapp para comunicação do grupo;
- Heroku - Motivo: Foi escolhido o Heroku como provedor de hospedagem da aplicação, onde foi possível apresentar a aplicação em servidor público;

<b>Contribuições individuais/pessoais</b>

* Criação de todo o Front-End da aplicação; 
* Conexão com API criada com Django Rest Framework;
* GET, PUT, DELETE E POST com Javascript;
* Criação de gráfico GANTT com requisições GET e POST para a Lib do Frappe;
* Auxilio na escolha das tecnologias do projeto;
* Auxilio na criação de ideias do projeto;
* Auxilio na criação na documentação do projeto;


<b>Aprendizados Efetivos</b>

* Aprendizado no que se trata uma API;
* Aprendizado em trabalhar com requisições GET, PUT, POST e DELETE utilizando a linguagem Javascript;
* Aprendizado em HTML e CSS;
* Aprendizado em Django Rest Framework;
* Aprendizado em Models, Views e Templates do Django;
* Aprendizado em implementação de dados do Django conectando ao banco de dados PostgreSQL;
* Aprendizado no sistema operacional Linux com base Debian;
* Aprendizado em trabalhar em equipe utilizando a metodologia ágil SCRUM;
* Aprendizado em utilização de repositórios de código utilizando comandos do GIT;
* Aprendizado no que seria Front-End, Back-End;
* Aprendizado no que é deploy e a realizar deploy da aplicação em servidor do Heroku;

#
#
<h3>3º Semestre:</h3>

* <B>Projeto GANTT PLANNER - Grupo PHPYTHON:</b>

<b>Objetivo do API:</b>

O SPC, em parceria com os alunos do 3º semestre do curso de Banco de Dados da Fatec de SJC, necessita de um software para obter uma análise estatística da evolução do consumidor em relação ao histórico de pagamentos e também da evolução da nota de score. Esse software é usado por qualquer pessoa física ou jurídica, que possua cadastro positivo e que, ao utilizá-lo, espera melhorar seu score de uma forma melhor do que as outras alternativas existentes no mercado. Espera também, obter dados de sua evolução financeira, afim de contribuir para uma melhora de seu score, e, possivelmente, efetuar novas solicitações de crédito para as instituições financeiras.

<b>Objetivo do Projeto:</b>

Foram levantadas ideias de calcular de uma forma mais exata possível o score de cada pessoa cadastrada na aplicação, onde ela possui um banco de dados com todos os dados de transação, empréstimo, financiamento e cartão de crédito de uma pessoa física.

Com estes dados e cálculo em mãos, foi levantada uma ideia de uma espécie de jogo, onde o usuário teria metas para cumprir, e, com as 8metas concluídas, teria um saldo de XP de experiência. Desta forma, há um incentivo para que as pessoas acessem a aplicação e cumpram as metas de melhoras no score.

A aplicação consiste de um Back-End criado com Spring Boot(Java) e o banco de dados postgreSQL. O Front-End criado com HTML, CSS e Javascript. O cálculo do score, análise de dados, metas e XP são criados  no Back-End. 

A aplicação possui um cadastro de pessoa física e jurídica, e, com o cpf ou cnpj cadastrado, a aplicação consegue analisar em uma massa de dados quais seriam seus dados de transações bancárias. 

<b>Tecnologias Adotadas na Solução:</b>

-   MySql Community - Motivo: Foi realizada a utilização desta ferramenta para a modelagem do modelo EER de nossa base de dados;
-   Java 1.8 - Motivo: Versão válida e segura para a utilização em projetos em Java;
-   Spring 2.3.0 - Motivo: Foi realizada uma votação em grupo para a utilização deste framework para a criação da aplicação;
-   Maven - - Motivo: Foi realizada uma votação em grupo para a utilização deste framework para a criação da aplicação;
-   Bootstrap 4 - Motivo: Foi realizada a escolha de implementar no projeto o Bootstrap 4 para realizar a criação do layout do Front-End;
-   Html5 - Motivo: Foi utilizado para a criação de templates;
-   JavaScript - Motivo: Foi escolhido a linguagem Javascript para implementar funcionalidades do Front-End;
-   CSS - Motivo: Foi realizado o uso de CSS para criar o layout do Front-End;

<b>Contribuições individuais/pessoais</b>

* Organização e documentação do projeto;
* SCRUM Master;
* Criação do layout e funcionalidades do Front-End;
* Auxilio na formulação do cálculo de score;
* Auxilio nas ideias do projeto, como o de ganho de XP e metas a cumprir;
* Vídeos e apresentações do grupo;

<b>Aprendizados Efetivos</b>

* Metodologia ágil como SCRUM;
* Aprendizado de como funciona o cálculo do score;
* Aprendizado a trabalhar com dados "mockados";
* Aprendizado em trabalhar com layout do Front-End, utilizando Bootstrap 4, CSS e HTML;
* Aprendizado de como liderar a equipe;
* Aprendizado em apresentar um projeto de software;
* Aprendizado em User Story;
* Aprendizado em Burndown e prazos de entrega na metodologia ágil;


#
#
<h3>4º Semestre:</h3>

* <B>Projeto NEMO API - Grupo NEMO:</b>

<b>Objetivo do API:</b>

A necessidade do cliente para esta API é a criação de um sistema escalável e rápido para o envio de currículos já filtrados de forma inteligente e de acordo com parâmetros que sejam passados por outras aplicações. Não é necessária a criação de uma interface de contato com usuário, apenas será trabalhado com um back-end, onde receberá dados de parâmetros de filtros de pessoas e retornará os currículos filtrados e no formato JSON. Deverá ser criada uma API para que as aplicações dos clientes possam realizar as requisições.

<b>Objetivo do Projeto:</b>

O projeto Nemo visa ser uma solução simples, versátil, escalável e open source para pessoas e empresas que precisam de um sistema escalável, simples e versátil para fazer a gestão dos currículos de candidatos relacionando eles às vagas disponíveis pela empresa.

Sem possuir uma interface(Front-End) o NEMO API possui a responsabilidade de receber dados, realizar a inserção em banco e retornar dados solicitados com os parâmetros no formato JSON.

Com o intuito de gastar um menor tempo na seleção de currículos, a aplicação do cliente envia parâmetros de filtro para a NEMO API, onde a mesma tem a finalidade de retornar currículos de acordo com o parâmetro passado.

<b>Tecnologias Adotadas na Solução:</b>

* Java - Motivo: De acordo com a votação realizada em grupo, foi realizada a escolha da linguagem Java;
* Spring Boot - Motivo: De acordo com a escolha da linguagem Java, que foi escolhida em grupo, foi escolhida também o framework Spring Boot para a criação da API e filtragem dos resultados;
* PostgreSQL - Motivo: Foi escolhido através de votação o banco de dados postgreSQL;
* Gitlab - Motivo: De acordo com votação em grupo, foi escolhido o repositório de código o Gitlab, pois os projetos anteriores já estavam sendo armazenados lá e o processo de CI/CD já estava mais avançado com este repositório;

<b>Contribuições individuais/pessoais</b>

* Auxilio na criação de métodos GET e POST para o envio e recebimento de dados vindo do Front-End;
* Auxilio na modelagem do modelo EER;
* Auxilio na criação de tabelas no banco de dados através do framework chamado Liquibase;
* Auxilio na idealização do projeto;
* Criação de servidor na AWS;
* Liberação de porta do postgresql, ssh, https, http no servidor hospedado na AWS;
* Criação de serviços para o proxy reverso NGINX;
* Deploy de projeto em ambiente Linux e apontamento do NGINX para o projeto do Java, utilizando o Maven;
* Criação de serviço para subir a conexão com o Maven e o projeto Java;
* Criação de servidor de banco de dados em servidor Linux hospedado na AWS;

<b>Aprendizados Efetivos</b>

* Aprendizado na utilização de framework Spring Boot para criação de projetos Java;
* Aprendizado na criação de tabelas de banco de dados utilizando o Liquibase;
* Aprendizado para subir servidor com comando do Maven e arquivo pom.xml;
* Criação de serviços no Linux;
* Criação de serviço para proxy reverso NGINX;
* Aprendizado na liberação de portas no firewall;
* Criação de deploy do projeto em ambiente Linux;
* Aprendizado em testes e deploys utilizando CI/CD;
