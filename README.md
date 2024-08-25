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