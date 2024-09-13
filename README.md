Esse conteúdo foi criado no canal Alexandre Leutz.

Assista ao vídeo com a explicação em:
https://youtu.be/cJ2_WPJ6Cqw

Veja o site usado na aula 
https://carlos-alexandre-leutz.github.io/httpAulaCompleta/


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

# Envio de Dados com `fetch` no JavaScript

O envio de dados em uma requisição `fetch` no JavaScript pode ser feito de diferentes maneiras, dependendo do tipo de dados que você precisa enviar. Os dois métodos mais comuns são utilizando JSON e FormData.

## 1. Enviando Dados como JSON

JSON (JavaScript Object Notation) é o formato mais comum para enviar dados estruturados em uma requisição HTTP, especialmente para APIs RESTful.

### Passos:

1. **Crie o objeto JavaScript**: Primeiro, você cria um objeto JavaScript com os dados que deseja enviar.
2. **Converta para JSON**: Utilize a função `JSON.stringify()` para converter o objeto em uma string JSON.
3. **Configure a requisição fetch**: Na chamada `fetch`, defina o método como `POST` (ou outro método HTTP como `PUT`, `PATCH`, etc.), adicione os cabeçalhos adequados, como `Content-Type: application/json`, e inclua o corpo da requisição contendo a string JSON.

### Exemplo:

```javascript
const dados = {
  nome: "Alexandre",
  email: "alexandre@example.com"
};

fetch('https://api.exemplo.com/enviar-dados', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(dados)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Erro:', error));
```

# 
# Formas de Envio de Dados com `fetch` no JavaScript

## 2. Enviando Dados como FormData

O `FormData` é uma interface que permite construir facilmente um conjunto de pares chave/valor representando os campos de um formulário e seus respectivos valores. É útil para enviar dados que geralmente seriam enviados por meio de um formulário HTML, como arquivos ou múltiplos campos de texto.

### Passos:

1. **Crie um objeto FormData**: Você pode criar um objeto `FormData` vazio e adicionar os campos manualmente, ou usar um formulário HTML existente.
2. **Adicione campos ao FormData**: Utilize o método `.append()` para adicionar campos ao objeto `FormData`.
3. **Configure a requisição fetch**: No `fetch`, defina o método como `POST` (ou outro método HTTP) e inclua o objeto `FormData` no corpo da requisição.

### Exemplo:

```javascript
const formData = new FormData();
formData.append('nome', 'Alexandre');
formData.append('email', 'alexandre@example.com');
formData.append('arquivo', arquivoInput.files[0]); // Supondo que 'arquivoInput' seja um campo de upload de arquivo

fetch('https://api.exemplo.com/enviar-dados', {
  method: 'POST',
  body: formData
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Erro:', error));
```

## Diferenças entre JSON e FormData

- **JSON** é ideal para enviar dados estruturados e facilmente processados no servidor. É amplamente utilizado para comunicação com APIs RESTful.

- **FormData** é mais flexível para enviar dados mistos, como campos de texto e arquivos, em uma única requisição. Ele também simula como os dados seriam enviados em um formulário HTML padrão, o que é útil em situações onde você precisa enviar arquivos ou dados de múltiplos campos.

Escolher entre `JSON` e `FormData` depende do tipo de dados que você está enviando e dos requisitos do servidor que receberá a requisição.



# Tratando a resposta do servido

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

## `then` e `catch` no JavaScript

No JavaScript, `then` e `catch` são métodos utilizados para lidar com operações assíncronas, especialmente ao trabalhar com Promises. Eles ajudam a processar os resultados de uma promessa, seja em caso de sucesso (`then`) ou em caso de erro (`catch`).

### `then`

O método `then` é usado para manipular o resultado de uma Promise que foi resolvida com sucesso. Quando uma operação assíncrona (como uma requisição HTTP) é concluída sem erros, o código dentro do `then` é executado. Ele recebe como argumento uma função que processa o valor retornado pela Promise.

#### Exemplo de uso:

```javascript
fetch('https://api.exemplo.com/dados')
  .then(response => response.json()) // Tenta processar a resposta
  .then(data => console.log(data))   // Manipula os dados, se bem-sucedido
  .catch(error => console.error('Erro:', error)); // Manipula o erro, se ocorrer
```
## Resumindo:

- **`then`**: Usado para processar o resultado de uma Promise resolvida com sucesso.
- **`catch`**: Usado para capturar e processar erros de uma Promise rejeitada.

Esses métodos tornam o código assíncrono mais fácil de ler e entender, permitindo que o desenvolvedor trate de forma clara os diferentes resultados de uma operação assíncrona.

## Requisição Assíncrona

Uma requisição assíncrona é uma operação que permite que um programa envie uma solicitação para um servidor e continue executando outras tarefas enquanto aguarda a resposta. 

Em vez de bloquear o fluxo de execução do código até que a resposta seja recebida, a requisição assíncrona permite que o programa realize outras ações, melhorando a eficiência e a capacidade de resposta da aplicação.

Esse modelo é frequentemente implementado usando Promises e métodos como `fetch`, `then`, e `catch` no JavaScript, possibilitando que o desenvolvedor lide com operações de rede de forma não bloqueante e que reaja rapidamente aos resultados da requisição, seja com sucesso ou com erro.


# Axios

O `Axios` é uma biblioteca JavaScript usada para fazer requisições HTTP de maneira simples e eficiente. Ele é baseado em Promises, o que facilita o tratamento assíncrono das respostas das requisições. O `Axios` é muito popular em projetos front-end, especialmente em aplicações React, Angular e Vue.js, devido à sua facilidade de uso e flexibilidade.

## Principais Características do `Axios`:

- **Suporte a Promises**: Facilita o trabalho com operações assíncronas.
- **Interceptors**: Permite interceptar e modificar requisições ou respostas antes que elas sejam manipuladas, útil para autenticação e tratamento de erros.
- **Suporte a JSON**: Configurações padrão que permitem enviar e receber JSON de maneira simples.
- **Configuração de Cabeçalhos**: Permite definir cabeçalhos HTTP personalizados facilmente.
- **Suporte a Cancelamento de Requisições**: Útil para cancelar requisições em andamento, por exemplo, em casos de navegação entre páginas.
- **Suporte a Requisições tanto no Navegador quanto no Node.js**: Isso faz do `Axios` uma escolha versátil para projetos full-stack.

## Exemplo Básico de Uso:

```javascript
import axios from 'axios';

axios.post('https://api.exemplo.com/dados')

axios.put('https://api.exemplo.com/dados')

axios.delet('https://api.exemplo.com/dados')

axios.get('https://api.exemplo.com/dados')

  .then(response => console.log(response.data))
  .catch(error => console.error('Erro:', error));


```

