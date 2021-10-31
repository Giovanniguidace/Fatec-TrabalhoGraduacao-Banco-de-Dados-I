

# Portfólio TG - API's - Trabalho de Graduação em BD I

#
<h2>Participações em API's: 5
</h2> 

<h3>1º Semestre:</h3>

* <B>Projeto Web BOT:</b>

<b>Objetivo do API:</b>
		<p>O objetivo do API do primeiro semestre, consiste em criar um WEBBOT para automatizar qualquer tipo de operação que será escolhida de forma livre entre as equipes. </p>



<b>Objetivo do Projeto:</b>

![logo.jpg](https://gitlab.com/cesaraugusto98/webbot/-/raw/master/class/logo.jpg)

Criar um WebBOT capaz de realizar a leitura de CNPJ's de todas as empresas de São José dos Campos e realizar a leitura de qual o tipo de ramo cada empresa. Será possível também, validar qual o capital a empresa possui e se ela está inativa ou ativa.

Com este valores coletados e os pontos inseridos no mapa, será possível visualizar em regiões de São José dos Campos quais delas possuem uma maior quantia de empresa de determinado ramo e capital. 

É possível selecionar no mapa qual ramo e capital deverá ser filtrado. Esta opção é disponibilizada aos usuários para que possam saber se determinada região compensa um possível investimento em determinado ramo.

Caso de Uso do Projeto:

![IMG-20190827-WA0037.jpg](https://gitlab.com/cesaraugusto98/webbot/-/raw/Mapas_geolocaliza%C3%A7ao/Imagens/IMG-20190827-WA0037.jpg)


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

Utilização da biblioteca Folium - Na prática:

Primeiramente, foi realizada a conexão com a base de dados NoSQL MongoDB, no qual as informações de Latitude e Longitude estavam armazenadas. Com isso, foi possível utilizar a Lib do Folium para criar um mapa de calor e um mapa de pontos em uma determinada região, que no projeto foi escolhida São José dos Campos.

Mapa de calor:
```python
import pymongo
import folium

from folium import plugins
from pymongo import MongoClient

#REALIZA A CONEXÃO COM O BANCO NO MONGO DB
db = MongoClient('mongodb+srv://admin:admin@cluster0-vuh1j.azure.mongodb.net/test?retryWrites=true&w=majority')

db = db.get_database('BD_EMPRESAS')


collection = db.empresas
latitude = []
longitude = []
qtd_range = []
coordenadas = []

#GET DE TODAS AS LATITUDES NA COLLECTION EMPRESAS
latitude = db.get_collection('empresas').distinct("latitude")

qtd_range = len(latitude)

#GET DE TODAS AS LONGITUDES NA COLLECTION EMPRESAS
longitude = db.get_collection('empresas').distinct("longitude")

#DELIMITA A REGIÃO DE INTERESSE NA BIBLIOTECA FOLIUM
mapa = folium.Map(location=[-23.4795233,-46.2698754],zoom_start=9)

#É ADICIONADO NO MAPA OS PONTOS COM AS LOCALIZAÇÕES DE LATITUDE E LONGITUDE
for i in range(qtd_range):
 coordenadas.append([latitude[i],longitude[i]])
 mapa.add_child(plugins.HeatMap(coordenadas))
 
#OS PONTOS SÃO ENVIADOS PARA O TEMPLATE MAPA_CALOR.HTML E SÃO TRANSFORMADOS COMO MAPA DE CALOR
mapa.save("mapa_calor.html")

```

Mapa de pontos:
```python
import pymongo
import folium

from pymongo import MongoClient

#REALIZA A CONEXÃO COM O BANCO NO MONGO DB
db = MongoClient('mongodb+srv://admin:admin@cluster0-vuh1j.azure.mongodb.net/test?retryWrites=true&w=majority')

db = db.get_database('BD_EMPRESAS')

collection = db.empresas
cnpj = []
latitude = []
longitude = []
qtd_range = []
endereco = []

#REALIZA A COLETA DE DADOS DA EMPRESA NA COLLECTION EMPRESAS
cnpj = db.get_collection('empresas').distinct("cnpj")
latitude = db.get_collection('empresas').distinct("latitude")
qtd_range = len(latitude)
longitude = db.get_collection('empresas').distinct("longitude")
endereco = db.get_collection('empresas').distinct("endereco")

#DELIMITA A REGIÃO DE INTERESSE NA BIBLIOTECA FOLIUM
mapa = folium.Map(location=[-23.4795233,-46.2698754],zoom_start=9)

for i in range(qtd_range):
 folium.Marker([latitude[i], longitude[i]], popup='CNPJ: '+cnpj[i]+'\n Endereco: '+endereco[i]).add_to(mapa)

#É ADICIONADO NO MAPA OS PONTOS COM AS LOCALIZAÇÕES DE LATITUDE E LONGITUDE
mapa.save("mapa_pontos.html")

```


<b>Aprendizados Efetivos</b>

* Trabalho em equipe utilizando a metodologia ágil SCRUM:
	* Através de Daily's, Sprints, Plannings, Reviews, foi possível entender como funciona de fato a metodologia ágil e qual a proposta de sua implantação em projetos de desenvolvimento.

* Aprofundamento na linguagem Python e as bibliotecas Folium e Pandas:
	* A linguagem Python foi trazida desde o início do curso e foi desenvolvida durante os semestres, com isso, foi possível compreender suas características e qual é a sua finalidade de utilização. As bibliotecas Folium e Pandas foram importadas e utilizadas no projeto e com isso, foi possível compreender que além destas, outras várias Lib's se encontram disponíveis para serem importadas e utilizadas;
	
* Organização de projeto e documentação:
	* A etapa de documentação foi trazida como requisito do projeto, e os itens para compor a documentação são:
		* Caso de Uso;
		* Modelo Entidade Relacionamento de Banco de Dados;
		* Métricas de BurnDown e conclusão de Sprints;
		* Matriz de Habilidade de cada integrante;
		
* Inicialização no framework Django:
	* O Framework Django utiliza da linguagem Python para que possamos, de maneira rápida e ágil, criar aplicações Web. Neste projeto foi aprendido a criar o projeto Django e adicionar Apps para que fossem assim criadas as funcionalidades do projeto. Com a conclusão do projeto, foi possível subir o server do Django e publicar o projeto na Web;
	
* Funcionamento de web scraping;
	* Para a coleta de dados de CNPJ e outros dados de empresa e também Latitude e Longitude de sua localização, foi utilizado o Web Scraping, que é um método de coleta de dados através dos templates em html dos sites visitados. 

Coleta de dados utilizando Web Scraping
```python
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.by import By
from time import sleep

class Driver:

#MAPEAMENTO DO __INIT__ PARA A LOCALIZAÇÃO DE ARQUIVOS
 def __init__(self, cep=False, cnpj=False):
		 directory = 'E:\\FATEC\\PI\\Files'
		 chrome_options = webdriver.ChromeOptions()
		 preferences = {"download.default_directory": directory}
		 chrome_options.add_experimental_option("prefs", preferences)
		 self.driver = webdriver.Chrome(chrome_options=chrome_options, executable_path='C:\\webbot\\chromedriver')
		 self.wait = WebDriverWait(self.driver, 5)
		 self.cep = cep
		 self.cnpj = cnpj
		 self.openSite()
 # self.driver.close()
 
 #FUNÇÃO QUE FARÁ O ACESSO AO SITE DE MAPA CEP E COLETARÁ DADOS DE LATITUDE E LONGITUDE DE ACORDO COM O CEP COLETADO NOS DADOS DA EMPRESA 
 def openSite(self):
		 self.driver.maximize_window()
		 self.driver.get("https://www.mapacep.com.br/index.php")
		 self.wait.until(EC.presence_of_element_located((By.ID, 'keywords')))
		 self.driver.find_element_by_id('keywords').send_keys(self.cep)
		 self.driver.find_element_by_xpath('/html/body/header/div[1]/div/div[2]/div/form/span/button').click()
		 sleep(10)
		 print(self.driver.find_element_by_xpath('/html/body/main/div[3]/div/div[1]/p').text)
		 text = self.driver.find_element_by_xpath('/html/body/main/div[3]/div/div[1]/p').text.split('\n')
		 # print(text)
		 # exit()
		 endereco = text[0]
		 latitude = text[3].split(' ')[1]
		 longitude = text[4].split(' ')[1]
		 print([latitude, longitude, endereco])
		 if self.cnpj:
				 try:
				 self.wait.until(EC.presence_of_element_located((By.ID, 'keywords')))
				 self.driver.find_element_by_id('keywords').clear()
				 self.driver.find_element_by_id('keywords').send_keys(self.cnpj[0:14])
				 self.driver.find_element_by_xpath('/html/body/header/div[1]/div/div[2]/div/form/span/button').click()
				 sleep(10)
				 text_cnpj = self.driver.find_element_by_xpath('/html/body/main/div[5]/div/div[1]/p[1]').text
				 text_cnpj = text_cnpj.split('\n')
				 print(text_cnpj)
				 codigo_atividade = text_cnpj[6].split(' ')[7]
				 nome_empresarial = text_cnpj[4].split(': ')[1]
				 descricao = text_cnpj[6].split(' ')[9:]
				 # self.driver.close()
				 return [latitude, longitude, endereco, codigo_atividade, nome_empresarial]
		 except:
				 # self.driver.close()
				 return [latitude, longitude]
		 # self.driver.quit()
		 # print(endereco, latitude, longitude)

#FUNÇÃO QUE REALIZA O DOWNLOAD DO ARQUIVO CONTENDO DADOS DE EMPRESAS
def getArchives(self):
		 self.driver.get(
		 'http://receita.economia.gov.br/orientacao/tributaria/cadastros/cadastro-nacional-de-pessoas-juridicas-cnpj/dados-publicos-cnpj')
		 links = self.driver.find_elements_by_css_selector('a.external-link')
		 for link in links:
				 link.click()
				 sleep(1)
				 self.waitDownload()

#FUNÇÃO QUE AUXILIA NO DOWNLOAD DE ARQUIVOS CONTENDO DADOS DE EMPRESAS 	 
def waitDownload(self):
		 if not self.driver.current_url.startswith("chrome://downloads"):
				 self.driver.get("chrome://downloads/")
				 # elemento = self.wait.until(EC.visibility_of_element_located((By.XPATH, '//*[@id="leftSpacer"]/h1')))
				 retorno = self.driver.execute_script("""
				 var items = downloads.Manager.get().items_;
				 if (items.every(e => e.state === "COMPLETE"))
				 return items.map(e => e.fileUrl || e.file_url);
				 else
				 return false
				 """)
				 # print(retorno)
				 count = 0
		 while retorno == False and count < 15:
				 sleep(1)
				 retorno = self.driver.execute_script("""
				 var items = downloads.Manager.get().items_;
				 if (items.every(e => e.state === "COMPLETE"))
				 return items.map(e => e.fileUrl || e.file_url);
				 else
				 return false
				 """)
				 count += 1
				 # print(retorno)
				 return
```

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

**Compatibilidade entre o aplicativo e o mundo real**

1.  A preocupação com o uso de ícones para as principais tarefas gera uma aproximação com o mundo real, trazendo um conforto propiciado pelo natural reconhecimento dos símbolos presentes no dia a dia.
2.  O mapa centralizado na tela do usuário em referência as televisões que ficam no centro da sala.

![real-virtual](https://gitlab.com/felipemessibraga/pi-phpython/uploads/3586344651689c3fc8d25e4227eae595/real-virtual.JPG)
**Controle e liberdade para o usuário**

1.  O usuário pode navegar entre as versões do projeto, podendo voltar a uma versão anterior caso a atual não o agrade;
2.  É possível modificar quase todos os atributos dos projetos, tarefas e pessoas;
3.  O sistema é responsivo, para se adaptar aos diversos monitores e dispositivos;

**Consistência e padronização**

1.  Os menus respeitam o mesmo padrão de design;
2.  Os icones apresentam apenas dois tipos, que variam apenas para evidenciar o seu contexto;

**Prevenção de erros**

1.  Existe uma preocupação grande com a prevenção de erros. Todas as decisões que não podem ser desfeitas emitem uma confirmação;
2.  Os botões respeitam um margem mínima para que não haja cliques "sem querer".

![botoes](https://gitlab.com/felipemessibraga/pi-phpython/uploads/c2e675a3dbf8fbcab70ccadc283f9cf2/botoes.JPG)
**Eficiência e flexibilidade de uso**

1.  O aplicativo foi pensado para que qualquer pessoa consiga utiliza-lo, por isso apresenta botões com objetivos claros, drag and drop para facilitar a movimentação das tarefas e contraste visual.
2.  Semelhança na disposição dos menus com ferramentas de uso popular como o Microsoft World;

**Estética e design minimalista**

1.  Deixamos apenas as principais informações em evidência, deixando o maior volume de informações para os relatórios, onde essas informações são idealmente dispostas de forma a não sobrecarregar o visual;
2.  Sem propagandas ou qualquer informação desnecessária.

![wireframe-minimalista](https://gitlab.com/felipemessibraga/pi-phpython/uploads/4de17b52b70036620bf3c0c01800b9a9/wireframe-minimalista.JPG)


**Apresentação Final para o Cliente**

https://www.youtube.com/watch?v=sePaF3FJYkg

#

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

* Criação de cadastros de Projetos, Tarefas, Pessoas, Distribuição de Pessoas em Tarefas

Exemplo de um GET em todos os projetos cadastrados - Javascript

```javascript
function getAllProjects(){  
 xhrGetProjeto = new XMLHttpRequest();
 json = '';
 xhrGetProjeto.open('GET', URLGETPROJETOS, true);
 xhrGetProjeto.onreadystatechange = function(){
 if(xhrGetProjeto.readyState == 4){
		 if(xhrGetProjeto.status == 200){
		 json = (JSON.parse(xhrGetProjeto.responseText));
		 }else if(xhrGetProjeto.status == 404){
		 }
	 } 
	 add_prj_menu_esquerdo(json);
	 }
	 xhrGetProjeto.send();
	}
```

Exemplo de cadastro de Projeto, utilizando o método POST - Javascript

```javascript
/*EXEMPLO DE MÉTODO POST PARA A CRIAÇÃO DE UM NOVO PROJETO*/

//UTILIZANDO O MÉTODO NATIVO DO JAVASCRIPT XMLHttpRequest
 xhrPostProjeto = new XMLHttpRequest();
 xhrPostProjeto.open("POST", URLGETPROJETOS, true);
 xhrPostProjeto.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
 xhrPostProjeto.setRequestHeader("X-CSRFToken", csrftoken);
 xhrPostProjeto.setRequestHeader("withCredentials", 'True');
 xhrPostProjeto.onreadystatechange = function(){
 if(xhrPostProjeto.readyState == 4){
			 if(xhrPostProjeto.status == 201){
			 getProjeto();
			 carregaTabelaProjeto();
			 if((json.length+1) > 1){
			 habilitaRecuoCodProjeto();
			 }  
		 }
	 }  
 }
 xhrPostProjeto.send(JSON.stringify({
					 'prj_id': codProjeto,
					 'prj_nome': nomeProjeto, 
					 'prj_escopo': escopo, 
					 'prj_datainicio': dt_inicio,
					 'prj_prazoentrega': dt_prazo,
					 'prj_color': cor,
					 "prj_cost": custo,
					 "prj_hrs_dev": horas_desen,
					 "prj_progresso": progressoprojeto
					 }));
```
Para a criação deste método foi bastante desafiador obter os conhecimentos necessários de requisições POST, GET, PUT e DELETE e também entender o funcionamento de API's.

* Conexão com API criada com Django Rest Framework;

Exemplo das URL's criadas
```javascript
//**CADASTRO DE PESSOAS*////
URLGETPESSOAS = 'http://localhost:8000/person/';
//**CADASTRO DE PROJETOS*////
URLGETPROJETOS = 'http://localhost:8000/project/';
//**CADASTRO DE TAREFAS*////
URLGETTAREFAS = 'http://localhost:8000/task/';
//**CADASTRO DE DISTRIBUICAO DE PESSOAS EM TAREFAS*////
URLGETDISTRIBUICAO = 'http://localhost:8000/distribute/';
//**CADASTRO DE HABILIDADES*////
URLGETHABILIDADES = 'http://localhost:8000/habilidades/';
//**CADASTRO DE DISTRIBUICAO DE HABILIDADES*////
URLGETDISTRHABILIDADES = 'http://localhost:8000/distributehab/';

```
* Criação de gráfico GANTT com requisições GET e POST para a Lib do Frappe;

Function criada para carregar o Gráfico de Gantt, contendo todas as informações necessárias cadastradas na aplicação e coletadas através do método GET - Javascript

```javascript
recebe_projetoGantt = [];
recebe_tarefaGantt = []

function carregaGantt(jsonProjetosGantt, jsonTarefasGantt){
  
 vetor_gantt = [];
//VALIDA SE O JSON CONTENDO OS DADOS DE PROJETOS ESTÃO VAZIOS
 if(jsonProjetosGantt != null){
 recebe_projetoGantt = jsonProjetosGantt;
 }
 
//VALIDA SE O JSON CONTENDO OS DADOS DE PROJETOS ESTÃO VAZIOS
 if(jsonTarefasGantt != null){
 recebe_tarefaGantt = jsonTarefasGantt;
 }
  
 // FUNÇÃO QUE REALIZARÁ A ANÁLISE DE PROJETOS QUE ESTÃO SELECIONADOS(CHECKED)
 checked_project = [];
 for(i=0;i<recebe_projetoGantt.length;i++){
  
 if(document.getElementById("cb_prj"+recebe_projetoGantt[i]['prj_id']+"").checked){
 checked_project.push(recebe_projetoGantt[i]['prj_id']);
 }
 }
  
 vetor_preparaProjetos = [];
 nomeInterdependencia = '';
 if(recebe_projetoGantt != ''){
	 if(recebe_tarefaGantt != ''){
 
		 for(i=0; i<recebe_projetoGantt.length;i++){
			 for(y=0;y<checked_project.length;y++){
					 if(checked_project[y] == recebe_projetoGantt[i]['prj_id']){
  
  
						 for(x=0;x<recebe_tarefaGantt.length;x++){
								 if(recebe_tarefaGantt[x]['trf_id'] == recebe_tarefaGantt[x]['trf_interdependencia']){
								 nomeInterdependencia = recebe_tarefaGantt[x]['trf_name'];
									 }
							 if(recebe_tarefaGantt[x]['fk_prj_id'] == recebe_projetoGantt[i]['prj_id']){
  
								 linha = [recebe_tarefaGantt[x]['trf_id'], recebe_tarefaGantt[x]['trf_name'],recebe_tarefaGantt[x]['trf_datainicial'], recebe_tarefaGantt[x]['trf_datafinal'], recebe_tarefaGantt[x]['trf_interdependencia'], recebe_tarefaGantt[x]['trf_progresso'], recebe_projetoGantt[i]['prj_color'] ];
								 vetor_preparaProjetos.push(linha);
								 }
						 }
				 }
			 }
		 }
  
 if(vetor_preparaProjetos != ''){
 tasks = []; //CRIA VETOR PARA RECEBER JSON
  
 // REALIZA O ENVIO DOS DADOS DOS PROJETOS PARA A API PARA QUE SEJA RETORNADO OS PARÂMETROS NECESSÁRIOS PARA IMPLEMENTAR NO GRÁFICO
 for(i = 0; i< vetor_preparaProjetos.length;i++){ //FAZ A VARREDURA NO VETOR PARA CRIAR JSON
						 tasks.push({ //CARREGA O JSON COM AS INFORMAÇÕES NECESSÁRIAS PARA CARREGAR O GRÁFICO GANTT
						 'id': 'Task'+vetor_preparaProjetos[i][0],
						 'name': vetor_preparaProjetos[i][1],
						 'start': vetor_preparaProjetos[i][2],
						 'end': vetor_preparaProjetos[i][3],
						 'dependencies': 'Task'+vetor_preparaProjetos[i][4],
						 'progress': vetor_preparaProjetos[i][5], 
						 'custom_class': 'tcolor-'+vetor_preparaProjetos[i][0] 
					 });
  
 }
 //console.log("TASKS: "+tasks+""); //TESTE DE INTEGRIDADE
 gantt = new Gantt('#gantt', tasks, { 
 on_click: function (task) {
 console.log(task);
 document.querySelector('style').innerHTML = '';
  
 cores_tarefas();
 },
 on_date_change: function(task, start, end) {
 console.log(recebe_tarefaGantt)
 console.log(task, start, end);
 const trf_id = parseInt(task.id.replace("Task",""))
 const tarefa = recebe_tarefaGantt.filter(_ => _.trf_id == trf_id)[0]
 tarefa.trf_datainicial = start.toISOString().split("T")[0]
 tarefa.trf_datafinal = end.toISOString().split("T")[0]
 putAtualizaTarefa(tarefa)
  
 },
 on_progress_change: function(task, progress) {
 console.log(task, progress);
 },
 on_view_change: function(mode) {
 console.log(mode);
 },
 custom_popup_html: function(task) {
  
 // the task object will contain the updated
 // dates and progress value
  
 //const end_date = task._end.format('MMM D');
 nome_pessoa_gantt = '';
	 for(i=0;i<recebe_tarefaGantt.length;i++){
					 if(task.name ==  recebe_tarefaGantt[i]['trf_name']){
					 dt_final_tarefa = recebe_tarefaGantt[i]['trf_datafinal'];
					 cod_tarefa_gantt = recebe_tarefaGantt[i]['trf_id'];
					 for(x=0;x<recebe_distribuicaoGantt.length;x++){
							 if(recebe_distribuicaoGantt[x]['fk_trf_id'] == cod_tarefa_gantt){
							 cod_pessoa_gantt = recebe_distribuicaoGantt[x]['fk_pes_id'];
					  
									 for(y=0;y<recebe_pessoasGantt.length;y++){
											 if(cod_pessoa_gantt == recebe_pessoasGantt[y]['pes_id']){
											 nome_pessoa_gantt = recebe_pessoasGantt[y]['pes_nome'];
											 }
									 }
						 }
					 }
					  
 }
 }
 split_dt_final_tarefa = dt_final_tarefa.split('-');
 reverse_dt_final_tarefa = split_dt_final_tarefa.reverse();
 join_dt_final_tarefa = reverse_dt_final_tarefa.join('-');
  
  
 return `
 <div class="details-container">
 <label>${task.name}</label>
 <p>Expected to finish by ${join_dt_final_tarefa}</p>
 <p>${task.progress}% completed!</p>
 <p>Pessoa: ${nome_pessoa_gantt} </p>
 </div>
 `;
 }
 });
  
 cores_tarefas();
  
 }
 }
}
}
```

Para criar esta integração foi bastante dificultoso, pois foi necessário aprender como trabalhar
com envio de parâmetros para a API e entender como os dados eram retornados para assim serem
utilizados e inseridos no gráfico.

Em relação à troca de cores dos projetos também foi bastante dificultoso, pois foi necessário
compreender um pouco mais afundo sobre DOM e assim realizar a troca da cor diretamente na tag
div em HTML.


* Auxilio na escolha das tecnologias do projeto:

	*	Inicialmente, a ideia era a utilização de tecnologias em que já estavam sendo ministradas neste
determinado semestre, para que pudéssemos adquirir conhecimento e concluir o semestre com boas 
notas.
Pensamos também em trabalhar com tecnologias que são muito utilizadas no mercado, como: Criação 
de API's; Front-End moderno; SCRUM como metodologia ágil; Back-End com Django;


* Auxilio na criação de ideias do projeto:

	*	O auxilio na criação das ideias do projeto envolve não só pensar em tecnologias, envolve o plano
de negócio do cliente, envolve o que o cliente deseja em questão de agilidade na utilização, em 
como a aplicação vai favorecê-lo quando foi utilizá-la. Por isso, a ideia inicial do projeto é a 
etapa principal e requer muito cuidado e projeção. Não podemos idealizar algo que não atenda ou 
que seja algo muito ruim de utilização. A performance foi uma das principais ideias que foram 
levantadas.


* Auxilio na criação na documentação do projeto:

	*	Após a idealização do projeto, é necessário levantar a documentação que será feita de todo o
escopo do projeto, da arquitetura, dos processos. Devido a isso, criamos: Caso de Uso; Modelo
EER; Desenho da arquitetura do projeto; Burndown das sprints; Vídeos explicativos; Imagens
ilustrando as telas da aplicação;


<b>Aprendizados Efetivos</b>

* Aprendizado no que se trata uma API:

	*	Eu já havia feito Programação e Desenvolvimento de Sistemas em 2010 e quando comecei a estudar 
na Fatec, foi quando eu retornei aos estudos na área de programação. Com isso, mesmo com a minha
bagagem de experiência na área de Infra de Redes, o termo e o que é API foi algo bem complexo 
de entender e aplicar em prática. Foi algo muito divertido, envolvente e desafiador aplicar a
criação de API em nosso projeto.



* Aprendizado em trabalhar com requisições GET, PUT, POST e DELETE utilizando a linguagem Javascript:

	*	Após entender como era o funcionamento e como criava uma API no back-end, mais precisamente
utilizando o Django Rest Framework, criamos por meio do JavaScript as funções de requisições,
fazendo com que a gente conseguisse coletar, deletar, criar ou atualizar dados diretamente no 
banco de dados, utilizando credenciais de acesso da aplicação como segurança.


* Aprendizado em HTML e CSS:

	*	Para quem nunca havia entrado no mundo de desenvolvimento Web, apenas Desktop, foi um desafio bem grande como era a criação de templates em HTML e utilizar CSS para dar estilo. Foi muito animador e muito prazeroso aprender sobre esse assunto e hoje eu utilizo muito para a criação de minhas aplicações profissionais e educacionais.

* Aprendizado em Django Rest Framework:

	*	Após entender o que era API e como uma API funcionava, era partir para a parte prática. Utilizamos o Django Rest Framework como Framework para a criação da API. Utilizamos como método de autenticação as credenciais de acesso da própria aplicação.

* Aprendizado em Models, Views e Templates do Django:

	*	O modelo MVC e MVT eram termos que eu ainda não conhecia que são termos do mundo de desenvolvimento de aplicações web. Ao estudar Django mais a fundo, descobri que é utilizado o modelo MVT, onde Model é utilizado para a criação de tabela em banco de dados, Views é utilizado para trabalhar com a "transmissão" e "recebimento" de dados com os templates (Front-End: HMTL; CSS; JS;)

* Aprendizado em implementação de dados do Django conectando ao banco de dados PostgreSQL:

	*	Foi entendido que o Django utiliza de drivers desenvolvidos em python para a conexão e administração do banco de dados através do Model do Django. Alguns deles seriam: Psycopg2; Pymongo; pyodbc; SqlLite;
 
* Aprendizado no sistema operacional Linux com base Debian:

	*	Ao trabalhar com a linguagem Python e com o framework Django, entendi que era hora de desenvolver em ambiente Linux, no qual eu já era familiarizado por trabalhar com esse O.S. 

* Aprendizado em trabalhar em equipe utilizando a metodologia ágil SCRUM:
	
	* Como no projeto anterior, foi utilizado a metodologia SCRUM como metodologia ágil. Desta forma, conseguimos praticar ainda mais esta metodologia e aplicar novos conceitos. 
	
* Aprendizado em utilização de repositórios de código utilizando comandos do GIT:

	* Em todo o projeto, utilizamos do GitLab como repositório de arquivos. Com isso, praticamos ainda mais o seu uso e a sua aplicabilidade. 	

* Deploy Heroku:

	*	Para que pudéssemos publicar a nossa aplicação, utilizamos de uma plataforma gratuita Heroku. 


#
#
<h3>3º Semestre:</h3>

* <B>Projeto SCORE WIZARD</b>

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
