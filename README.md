# Criando uma API Express

## Preparando o ambiente

1. Crie uma pasta no seu computador
2. Abra sua pasta no VS Code
3. Instale o [Node.js](https://nodejs.org/pt-br) no seu computador
4. Digite o comando `npm install express` no terminal para instalar o Express, um framework para Node.js que fornece recursos mínimos para construção de servidores web
5. Digite o comando `npm install cors express` para instalar o CORS, um mecanismo de segurança que controla acesso entre domínios diferentes no navegador

## Criando a API

1. Crie um arquivo nomeado index.js dentro da sua pasta e cole o código abaixo

```jsx
const express = require('express');const os = require('os');
const app = express();
app.get('/', (req, res) => {
    res.send(`   
    <h1>Monitor de Sistemas Operacionais</h1>   
    <p><strong>Hostname:</strong> ${os.hostname()}</p>    
    <p><strong>Plataforma:</strong> ${os.platform()}</p>    
    <p><strong>Porta:</strong> ${os.port()}</p>    
    <p><strong>Arquitetura:</strong> ${os.arch()}</p>    
    <p><strong>Memória Total:</strong> ${Math.round(os.totalmem()/1024/1024)} MB</p>    
    <p><strong>Memória Livre:</strong> ${Math.round(os.freemem()/1024/1024)} MB</p>    
    <p><strong>CPUs:</strong> ${os.cpus().length}</p>    
    <p><strong>Uptime:</strong> ${Math.round(os.uptime()/60)} minutos</p>  `);});
const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log("Servidor rodando"));
```

Você pode melhorar o código e adicionar informações usando os [recursos de Web API do JavaScript](https://developer.mozilla.org/en-US/docs/Web/API/Location/origin)

1. Teste o funcionamento rodando o comando `node index.js` no terminal
2. Se tudo estiver funcionando corretamente, uma página web mostrará algumas informações do hardware do seu equipamento
3. API funcional, hora de fazer o commit para o GitHub!

## Disponibilizando a API no Render

1. Verifique se seu projeto foi enviado com sucesso para o GitHub
2. Faça login ou crie uma conta no [Render](https://render.com/)
3. Clique em **Create new project**
4. Selecione a opção **New web service**
5. Configure o Render para puxar os arquivos do seu repositório
6. Na página de configurações, defina **Build Command** como `node` e **Start Command** como `node index.js` 
7. Confirme tudo e aguarde o Render publicar sua API
8. Clique no link disponibilizado na interface do Render para testar o funcionamento
9. Se tudo estiver correto, a página irá mostrar as configurações do servidor onde sua API foi hospedada
