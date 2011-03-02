A especifica��o do HTTP e os fundamentos do Symfony2
====================================================

Para ir longe com o Symfony2, n�s iremos come�ar primeiro discutindo o Protocolo de 
Trasnfer�ncia de Hipertexto (HTTP) - o formato de mensagens simples e refrescante usado 
por todos os clientes (ex. navegadores web) e servidores quando se comunicam um com o 
outro. Isto � importante porque, como iremos descobrir, Symfony 2 tem sido incans�velmente
arquitetado em seu n�cleo para usar HTTP e n�o reinvent�-lo. O produto final � um framework
que, diferente de muitos outros, � uma abstra��o em torno das regras fundamentais da World 
Wide Web. Percebendo ou n�o, HTTP � algo que voc� usa todo dia. Com Symfony2 voc� ir� 
aprender como aproveit�-lo e domin�-lo.

O Cliente envia a Requisi��o
----------------------------

A Web � constru�da em torno da id�ia de que cada comunica��o come�a quando um cliente faz
uma requisi��o a um servidor. A requisi��o � uma simples mensagem de texto criada pelo
cliente em um formato especial conhecido como HTTP. Embora haja muitos tipos diferentes
de clientes - navegadores web, web services, leitores RSS, etc - cada um deles envia 
requisi��es no mesmo formato b�sico. Por exemplo:

::

    GET /index.html HTTP/1.1
    Host: www.example.com
    Accept: text/html
    User-Agent: Mozilla/5.0 (Linux; X11)
	
A primeira linha da requisi��o HTTP � a mais importante delas (e como � de fato, a �nica
obrigat�ria delas). Ela cont�m duas coisas: a URI e o m�todo HTTP. A URI (URL se combinada 
com o cabe�alho do host) unicamente identifica a localiza��o do recurso enquanto o m�todo 
HTTP define o que voc� quer fazer com o recurso. Neste exemplo, a �nica localiza��o do 
recurso � `/index.html` e o m�todo HTTP � o GET. Em outras palavras, a requisi�a� do cliente
� para recuperar o recurso identificado por `/index.html`. 

Os m�todos HTTP s�o verbos da requisi��o HTTP e definem as poucas maneiras comuns com as 
quais podemos agir sobre os recursos:

* GET Recupera o recurso do servidor;
* POST Cria um recurso no servidor;
* PUT Atualiza o recurso no servidor;
* DELETE Delta o recurso do servidor;

Com isto em mente, n�s podemos imaginar o que uma requisi��o HTTP pode fazer para deletar 
uma entrada espec�fica de um blog:

::

    DELETE /blog/15 HTTP/1.1
	
..

    Nota:
	H� realmente nove m�todos HTTP definidos pela especifica��o HTTP, mas muitos deles n�o 
	s�o largamente usados ou suportados. Na realidade, muitos naveadores modernos n�o suportam 
	os m�todos PUT e DELETE. Um cabe�alho adicional � comummente suportado � o m�todo HEAD, que 
	diz que a resposta deve ser id�ntica � de uma requisi��o GET, mas sem o corpo da resposta, 
	ou seja, somente seu cabe�alho.
	
Em adi��o � primeira linha, uma requisia��o HTTP comummente cont�m outras linhas de informa��o
conhecidas como cabe�alhos da requisi��o HTTP. Os cabe�alhos fornecem uma larga lista de 
informa��es adicionais tais como o `Host` requisitado, o formato de resposta que o cliente aceita
(`Accept`) e a aplica��o que o cliente est� utilizando para fazer a requisi��o (`User-Agent`).
Existem muitos outros cabe�alhos e n�s podemos encontrar uma Lista dos campos de cabe�alhos HTTP 
no artigo da Wikipedia. 
