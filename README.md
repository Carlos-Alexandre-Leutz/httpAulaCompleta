Esse conteúdo foi criado no canal Alexandre Leutz.

Assista ao vídeo com a explicação em:
https://youtu.be/cJ2_WPJ6Cqw


# CRUD com Firebase Realtime Database

Este projeto demonstra como realizar operações CRUD (Create, Read, Update, Delete) com o Firebase Realtime Database. Abaixo estão as URLs e instruções para testar cada operação.

## URLs de Teste

### 1. GET (Obter Dados)
- **URL:** `https://aula-http-canal-default-rtdb.firebaseio.com/textos.json`
- **Método:** `GET`
- **Descrição:** Esta URL retorna todos os dados armazenados na coleção "textos" em formato JSON.

### 2. POST (Criar Novo Dado)
- **URL:** `https://aula-http-canal-default-rtdb.firebaseio.com/textos.json`
- **Método:** `POST`
- **Descrição:** Esta URL permite criar um novo dado na coleção "textos". O corpo da requisição deve conter o texto a ser salvo em formato JSON. Exemplo de corpo da requisição:
  ```json
  {
    "text": "Seu texto aqui"
  }
### 4. DELETE (Deletar Dado)

- **URL:** `https://aula-http-canal-default-rtdb.firebaseio.com/textos/{ID_DO_DADO}.json `


**Descrição:**  
Substitua `{ID_DO_DADO}` pelo ID do dado que deseja deletar. Esta URL permite remover um dado específico da coleção "textos".

**Como Utilizar:**

- **GET:** Copie e cole a URL no seu navegador ou use uma ferramenta como Postman para realizar a requisição e visualizar todos os dados salvos.

- **POST:** Utilize uma ferramenta como Postman ou um script em JavaScript para enviar uma requisição POST com o corpo da requisição contendo o texto a ser criado. Exemplo:

  ```javascript
  fetch('https://aula-http-canal-default-rtdb.firebaseio.com/textos.json', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({ text: 'Seu texto aqui' })
  })
  .then(response => response.json())
  .then(data => console.log(data));

## Operações com Firebase Realtime Database

### PUT: Atualizar um Dado

Envie uma requisição PUT para atualizar um dado existente, substituindo `{ID_DO_DADO}` pelo ID do dado que deseja atualizar e inclua o novo texto no corpo da requisição. 

Exemplo:
```javascript
fetch('https://aula-http-canal-default-rtdb.firebaseio.com/textos/{ID_DO_DADO}.json', {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ text: 'Texto atualizado' })
})
.then(response => response.json())
.then(data => console.log(data));
```
## DELETE: Remover um Dado

Envie uma requisição `DELETE` para remover um dado específico, substituindo `{ID_DO_DADO}` pelo ID correto do dado a ser deletado.

### Exemplo

```javascript
fetch('https://aula-http-canal-default-rtdb.firebaseio.com/textos/{ID_DO_DADO}.json', {
  method: 'DELETE'
})
.then(response => response.json())
.then(data => console.log(data));
```

# Status de Resposta HTTP: Entendendo o Código 200 e Outros Principais Códigos

Quando você faz uma requisição a um servidor, ele retorna um código de status HTTP para indicar o resultado da sua solicitação. Esses códigos são essenciais para entender o que aconteceu com a sua requisição. Vamos focar nos códigos mais comuns, começando pelo famoso `200 OK`.

## Código 200 - OK

O código `200` é o status de resposta mais desejado. Ele indica que a requisição foi bem-sucedida. Se você fez uma requisição `GET`, significa que os dados foram recuperados corretamente. Em uma requisição `POST`, o código `200` confirma que o recurso foi criado ou modificado com sucesso.

**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/dados')
  .then(response => {
    if (response.status === 200) {
      return response.json();
    }
  });
```
## Código 201 - Created

O `201` aparece principalmente em respostas a requisições `POST` e indica que o recurso foi criado com sucesso no servidor.

**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/novo-recurso', {
  method: 'POST',
  body: JSON.stringify({ nome: 'Novo Recurso' }),
  headers: { 'Content-Type': 'application/json' }
})
.then(response => {
  if (response.status === 201) {
    console.log('Recurso criado com sucesso!');
  }
});
```

## Código 204 - No Content

O `204` significa que a requisição foi bem-sucedida, mas o servidor não tem conteúdo para retornar. Isso é comum em requisições `DELETE`.

**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/recurso/123', {
  method: 'DELETE'
})
.then(response => {
  if (response.status === 204) {
    console.log('Recurso deletado com sucesso!');
  }
});

```

## Código 400 - Bad Request

O código `400` indica que houve um erro na requisição, geralmente por causa de dados inválidos. O servidor não conseguiu processar a solicitação devido a uma má formatação ou parâmetro incorreto.
**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/atualizar-recurso', {
  method: 'POST',
  body: 'dados_invalidos',
  headers: { 'Content-Type': 'application/json' }
})
.then(response => {
  if (response.status === 400) {
    console.log('Erro na requisição: Dados inválidos.');
  }
});

```

## Código 401 - Unauthorized

O `401` aparece quando a autenticação é necessária e falhou ou não foi fornecida. É um alerta de que o usuário precisa de credenciais válidas para acessar o recurso.
**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/recurso-protegido', {
  headers: { 'Authorization': 'Bearer token_invalido' }
})
.then(response => {
  if (response.status === 401) {
    console.log('Acesso não autorizado: Autenticação necessária.');
  }
});

```

## Código 403 - Forbidden

O código `403` é retornado quando o servidor entende a requisição, mas se recusa a autorizá-la. Mesmo que o usuário esteja autenticado, ele não tem permissão para acessar o recurso.
**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/recurso-restrito', {
  headers: { 'Authorization': 'Bearer token_valido' }
})
.then(response => {
  if (response.status === 403) {
    console.log('Acesso proibido: Você não tem permissão para acessar este recurso.');
  }
});

```

## Código 404 - Not Found

O `404` é um dos códigos mais conhecidos. Ele indica que o recurso solicitado não foi encontrado no servidor. É comum em URLs incorretas ou recursos inexistentes.
**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/recurso-inexistente')
.then(response => {
  if (response.status === 404) {
    console.log('Recurso não encontrado: Verifique a URL.');
  }
});

```

## Código 500 - Internal Server Error

O `500` é um erro genérico do servidor, que ocorre quando algo deu errado no lado do servidor, mas o servidor não pode fornecer mais detalhes.
**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/recurso', {
  method: 'POST',
  body: JSON.stringify({ nome: 'Dados' }),
  headers: { 'Content-Type': 'application/json' }
})
.then(response => {
  if (response.status === 500) {
    console.log('Erro no servidor: Tente novamente mais tarde.');
  }
});

```

## Código 503 - Service Unavailable

O `503` significa que o servidor está temporariamente indisponível, geralmente devido a manutenção ou sobrecarga. É um aviso de que o servidor não pode lidar com a requisição no momento.
**Exemplo de Uso:**
```javascript
fetch('https://api.exemplo.com/recurso')
.then(response => {
  if (response.status === 503) {
    console.log('Serviço indisponível: Tente novamente mais tarde.');
  }
});

```

