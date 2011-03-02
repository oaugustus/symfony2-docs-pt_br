A especificação do HTTP e os fundamentos do Symfony2
====================================================

Para ir longe com o Symfony2, nós iremos começar primeiro discutindo o Protocolo de 
Trasnferência de Hipertexto (HTTP) - o formato de mensagens simples e refrescante usado 
por todos os clientes (ex. navegadores web) e servidores quando se comunicam um com o 
outro. Isto é importante porque, como iremos descobrir, Symfony 2 tem sido incansávelmente
arquitetado em seu núcleo para usar HTTP e não reinventá-lo. O produto final é um framework
que, diferente de muitos outros, é uma abstração em torno das regras fundamentais da World 
Wide Web. Percebendo ou não, HTTP é algo que você usa todo dia. Com Symfony2 você irá 
aprender como aproveitá-lo e dominá-lo.

O Cliente envia a Requisição
----------------------------

A Web é construída em torno da idéia de que cada comunicação começa quando um cliente faz
uma requisição a um servidor. A requisição é uma simples mensagem de texto criada pelo
cliente em um formato especial conhecido como HTTP. Embora haja muitos tipos diferentes
de clientes - navegadores web, web services, leitores RSS, etc - cada um deles envia 
requisições no mesmo formato básico. Por exemplo:

::

    GET /index.html HTTP/1.1
    Host: www.example.com
    Accept: text/html
    User-Agent: Mozilla/5.0 (Linux; X11)
	
A primeira linha da requisição HTTP é a mais importante delas (e como é de fato, a única
obrigatória delas). Ela contém duas coisas: a URI e o método HTTP. A URI (URL se combinada 
com o cabeçalho do host) unicamente identifica a localização do recurso enquanto o método 
HTTP define o que você quer fazer com o recurso. Neste exemplo, a única localização do 
recurso é `/index.html` e o método HTTP é o GET. Em outras palavras, a requisiçaõ do cliente
é para recuperar o recurso identificado por `/index.html`. 

Os métodos HTTP são verbos da requisição HTTP e definem as poucas maneiras comuns com as 
quais podemos agir sobre os recursos:

* GET Recupera o recurso do servidor;
* POST Cria um recurso no servidor;
* PUT Atualiza o recurso no servidor;
* DELETE Delta o recurso do servidor;

Com isto em mente, nós podemos imaginar o que uma requisição HTTP pode fazer para deletar 
uma entrada específica de um blog:

::

    DELETE /blog/15 HTTP/1.1
	
..

    Nota:
	Há realmente nove métodos HTTP definidos pela especificação HTTP, mas muitos deles não 
	são largamente usados ou suportados. Na realidade, muitos naveadores modernos não suportam 
	os métodos PUT e DELETE. Um cabeçalho adicional é comummente suportado é o método HEAD, que 
	diz que a resposta deve ser idêntica à de uma requisição GET, mas sem o corpo da resposta, 
	ou seja, somente seu cabeçalho.
	
Em adição à primeira linha, uma requisiação HTTP comummente contém outras linhas de informação
conhecidas como cabeçalhos da requisição HTTP. Os cabeçalhos fornecem uma larga lista de 
informações adicionais tais como o `Host` requisitado, o formato de resposta que o cliente aceita
(`Accept`) e a aplicação que o cliente está utilizando para fazer a requisição (`User-Agent`).
Existem muitos outros cabeçalhos e nós podemos encontrar uma Lista dos campos de cabeçalhos HTTP 
no artigo da Wikipedia. 
