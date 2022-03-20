<h1 align='center'>API Fake JSON-Server</h1>

<h2>Sobre:</h2>  
Atividade sobre a utilização da **API Fake do JSON-Server** juntamente com **JSON-Server-Auth** para treino e posterior utilização no capstone do M3.

<br><br>

### Tecnologias utilizadas:
* [JSON-Server](https://www.npmjs.com/package/json-server)
* [JSON-Server-Auth](https://www.npmjs.com/package/json-server-auth)
* [Insomnia](https://insomnia.rest/)

<br><br>

### Endpoints:
Há um total de 8 endpoints, subdivididos entre cadastro de usuários, login, criação e leitura de comentários e cadastro de pets.
<br>

A url base da API é: [atividade11-json-server-base.heroku.com](atividade11-json-server-base.heroku.com)

<br><hr>

### Rotas que não precisam de autenticação:
<hr><br>

<h3 align='center'>Criação de usuário:</h3>

``` 
POST /register - REQUISIÇÃO
```
```
{
  "email": "olivier@mail.com",
  "password": "bestPassw0rd",
  "firstname": "Olivier",
  "lastname": "Monge",
  "age": 32
}
```
<br>

```
Retorno esperado: 

  {
	"accessToken": "xxx.xxx.xxx",
	"user": {
		"email": "olivier@mail.com",
		"firstname": "Olivier",
		"lastname": "Monge",
		"age": 32,
		"id": 1
	}
  }

```

<br><hr>

### Rotas que precisam de autenticação:
<hr><br>

**email** e **senha** são necessários.
```
POST /login - REQUISIÇÃO 
```
```
{
  "email": "olivier@mail.com",
  "password": "bestPassw0rd"
}
```

<br>
A resposta contém o token (lembrar que ele expira em 1 hora):

<br>

```
Retorno de sucesso:

 {
	"accessToken": "xxx.xxx.xxx",
	"user": {
		"email": "olivier@mail.com",
		"firstname": "Olivier",
		"lastname": "Monge",
		"age": 32,
		"id": 1
	}
  }
```
<br>

### cadastrando seu pet:

<br>

```
POST /animals 
```

Lembrar que é necessário passar o **userId** e **token**:
```
{
  "type": "tipo do animal",
  "name": "nome do animal",
  "userId": number
}
```

<br><hr>
<h3 align='center'>Para acessar os dados:</h3>
<hr><br>

### Podemos utilizar os query params para filtrar pelo tipo na requisição /animals:

<br>

```
GET /animals(query Params)
```

<p>Ex: /animals?type=Cachorro</p>


```
Retorno esperado - FORMATO DA RESPOSTA:

[
	{
		"type": "Cachorro",
		"name": "Lua",
		"userId": 2,
		"id": 1
	}
]
```
<br><hr>

### Cadastrando seu comentário:

<hr><br>

```
POST /comments
```

<br>

Lembrar que é necessário passar o **userId** e **token**:

<br>

```
{ 
	"comments": "comentário", 
	"userId": 1
}
```

```
Retorno de sucesso:

 {
	"comments": "comentário",
	"userId": 1,
	"id": 1
}
```
<br><hr>
<h3 align='center'>Para acessar os dados:</h3>
<hr><br>

```
GET /comments
```

```
[
	{
		"text": "comentário",
		"userId": 1,
		"id": 1
	}
]
```

<br><hr>

### Cadastrando seu ToDo List:

<hr><br>

```
POST /todo
```

<br>

Lembrar que é necessário passar o **userId** e **token**:

<br>

```
{
	"text": "todo de exemplo",
  "userId": 1
}
```

```
Retorno de sucesso:

{
	"text": "todo de exemplo",
	"userId": 1,
	"id": 1
}
```
<br><hr>
<h3 align='center'>Para acessar os dados:</h3>
<hr><br>

```
GET /todo
```

```
Resposta:
[
  {
  	"text": "todo de exemplo",
  	"userId": 1,
  	"id": 1
  }
]
```


<br><hr>

### Cadastrando sua bio:

<hr><br>

```
POST /bio
```

<br>

É necessário passar o **userId** e **token** para escrevê-la:

<br>

```
{
  "text": "bio de exemplo",
  "userId": 1
}
```

```
Retorno de sucesso:

{
	"text": "bio de exemplo",
	"userId": 1,
	"id": 1
}
```
<br><hr>
<h3 align='center'>Para acessar os dados:</h3>
<hr><br>

```
GET /bio
```

Lembrar que todos terão acesso de leitura a ela, por isso não há necessidade de passar o token:
```
Resposta:
[
  {
  	"text": "bio de exemplo",
  	"userId": 1,
  	"id": 1
  }
]
```