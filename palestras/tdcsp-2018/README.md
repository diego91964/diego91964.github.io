# Otimizando a análise de logs e rastreamento de usuários utilizando Grafos


----

<!-- .slide: data-background="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/graph.jpg" -->

 <!-- .slide: data-state="dimbg" -->


# Hoje você vai saber como NoSQL mudou a minha vida de DevOps

e pode ajudar você a mudar a vida de outras pessoas.

----

# Por que você usa NoSQL?



----

<!-- .slide: data-background="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/graph-big-data.png"  -->

 <!-- .slide: data-state="dimbg"  -->

# Grandes quantidades de dados, pouco estruturados, em formato de texto, que deveriam ser interpretados.

----

# Quais informações precisavam ser extraídas?

----

<!-- .slide: data-background="#E47C06" -->

# Quais usuários se conectam do mesmo computador?

----

<!-- .slide: data-background="#DE0333" -->

# Qual serviço é o mais 'pesado' de uma aplicação?

----


<!-- .slide: data-background="#005398" -->

# Quais serviços de um app foram utilizados?

----


<!-- .slide: data-background="#009949" -->
# * Quais usuários possuem o mesmo padrão de uso do sistema?

----

# Dados Existentes

<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/neo4j-dados-selecionados.png" width = "80%">


----

# Como modelar estes dados?

----

#SQL ?

<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/neo4j-dados-sql.png" width = "80%">

----

<!-- .slide: data-background="#009949" -->

# Muitas linhas (200 ~ 300 Mb de texto por dia)

----

<!-- .slide: data-background="#009949" -->

# Rápido load and delete

----

<!-- .slide: data-background="#DE0333" -->

# Uma linha se relaciona com outra por diversos parâmetros


----


# Depois de alguns experimentos, escolhemos os Grafos implementados no Neo4J

----


# O que são grafos?



<!-- .slide: data-background="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/graph-sample.png"
 -->

 <!-- .slide:
data-state="dimbg"
  -->


----

<!-- .slide: data-background="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/caixeiro-viajante.jpg"
 -->

 <!-- .slide:
data-state="dimbg"
  -->

# Quais problemas podem ser resolvidos utilizando grafos?


----

# Teoria dos Grafos


<!-- .slide: data-background="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/graph-teory.jpg"
 -->

 <!-- .slide:
data-state="dimbg"
  -->


----


# E se guardarmos informações nos vérticies e nas arestas?

----

<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/neo4j-dados-propriedades.png" width = "80%">

----

# Relacionamentos


----

<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/neo4j-dados-relacionamento.png" width = "80%">

----


<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/neo4j-logo.png" width = "80%">



----

# Ciclo básico de um Banco de Dados

* Criar Modelo
* Carregar Dados
* Buscar Dados


----

<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/neo4j-dados-estrutura.png" width = "50%">


----

# Carregar Dados


----

# CARREGAR CSV

<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/csv-sample.png" width = "60%">

----

<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/load-csv.sample.png" width = "60%">


```

LOAD CSV WITH HEADERS FROM "https://neo4j.com/docs/developer-manual/3.4/csv/import/persons.csv" AS csvLine
CREATE (p:Person { id: toInteger(csvLine.id), name: csvLine.name })

```

[Import Tutorial](https://neo4j.com/docs/operations-manual/current/tutorial/import-tool/) / [Import CSV Cypher](https://neo4j.com/docs/developer-manual/current/get-started/cypher/importing-csv-files-with-cypher/)


----

# Protocolo Bolt

https://boltprotocol.org/

----

# Buscar Dados

----

# Linguagem Cypher

----

# Buscar

```

MATCH (actor:Person)-[:ACTED_IN]->(movie:Movie)

WHERE movie.title STARTS WITH "T"

RETURN movie.title AS title, actor.name AS cast

ORDER BY title ASC LIMIT 10;

```
[Fonte:Neo4j](https://neo4j.com/developer/cypher/)

----

# Inserir

```
CREATE (
         n:Person {
           name: 'Andres',
           title: 'Developer' }
      )
```

----

#Inserir Logs

```

MERGE (ip:IP {ip:'9.93.37.31'})
MERGE (url:URL {url:'/proin/wisi'})
MERGE (usuario:Usuario {idUsuario : '942'})
MERGE (data: Data { data : '23/6/2018' })
MERGE (hora: Hora { hora: '19:9:35' } )
MERGE (aplicacao: Aplicacao { idAplicacao : '2849' } )

MATCH (ip:IP) ,
      (url:URL),
      (usuario:Usuario),
      (data: Data),  
      (hora: Hora),
      (aplicacao: Aplicacao)  
WHERE ip.ip   = '9.93.37.31'    AND
      url.url = '/proin/wisi'   AND    
      usuario.idUsuario = '942' AND    
      data.data  = '23/6/2018'  AND
      hora.hora  = '19:9:35'    AND
      aplicacao.idAplicacao  = '2849'  
CREATE (req : Requisicao { tempo : '36'} )  
CREATE ( param :
         Parametro {  parm0:'val-0' ,
                      parm1:'val-1' ,
                      parm2:'val-2'  } )   
CREATE (param)       - [:resp_request]      -> (req)  
CREATE (ip)          - [:ip_request]        -> (req)
CREATE (url)         - [:url_request]       -> (req)  
CREATE (usuario)     - [:usuario_request]   -> (req)  
CREATE (data)        - [:data_request]      -> (req)  
CREATE (hora)        - [:hora_request]      -> (req)  
CREATE (aplicacao)   - [:aplicacao_request] -> (req)

```

----

# Questões

----



# Qual serviço é o mais 'pesado' de uma aplicação?

```

MATCH
  (url:URL) -[:url_request] ->
  (call:Requisicao) <- [:aplicacao_request] - (apl:Aplicacao)
WHERE apl.idAplicacao = 'x'
RETURN max(call.tempo)

```

----

# Quais serviços de uma aplicação foram utilizados?


```

MATCH
     (url:URL) -[:url_request] -> (call:Requisicao)
     <- [:aplicacao_request] - (apl:Aplicacao)
WHERE apl.idAplicacao = 'x'
RETURN url, apl

```



----

## Quais são os parâmetros passados para um serviço?

```

# Todos os serviços

MATCH (url:URL) -[:url_request] -> (call:Requisicao) <- [:resp_request] - (par:Parametro)
RETURN url,par

# Um serviço específico

MATCH (url:URL) -[:url_request] -> (call:Requisicao) <- [:resp_request] - (par:Parametro)
WHERE url.url = '/fugit/quisque'
RETURN url,par

```


----

## Dois usuários que utilizaram um serviço específico de um app

```

MATCH  
   (n1:Requisicao)   <- [:resp_request] - (app : Aplicacao) ,
   (n2 : Requisicao) <- [:resp_request] - (app) ,
   (n1) <- [:usuario_request]- (usuario1: Usuario) ,
   (n2) <- [:usuario_request]- (usuario2: Usuario)
WHERE app.idAplicacao = 'x'
RETURN n1 , n2

```

----

<!-- .slide: data-background="#009949" -->
# * Quais usuários possuem o mesmo padrão de uso do sistema?

----

# Lições aprendidas

----

<!-- .slide: data-background="#E47C06" -->

# NoSQL não é apenas desempenho

----

<!-- .slide: data-background="#DE0333" -->

# Utilize os pontos fortes do seu modelo

----

<!-- .slide: data-background="#009949" -->

# Soluções simples resolvem grandes problemas

----


<!-- .slide: data-background="#005398" -->

# Olhe para o lado, você pode ajudar outra pessoa


----

# Quer replicar os cenários apresentados?

----


<img src="https://github.com/diego91964/diego91964.github.io/blob/master/palestras/tdcsp-2018/img/qr-git.png" width = "70%">
https://github.com/diego91964/demo-log-neo4j

----


# Quer saber mais sobre NoSQL aplicado a DevOps e Métricas?

https://github.com/diego91964


----

# Diego Silva

diego.silva.facom@gmail.com

----

# Obrigado!
