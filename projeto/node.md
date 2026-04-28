# 🚀 Deploy de uma API Node.js no Render

## 📦 Pré-requisitos

Antes de começar, você precisa ter:

* Node.js instalado
* Conta no GitHub
* Conta no Render
* Um projeto Node funcional

---

## 🧱 1. Criando uma API Node simples

Se ainda não tiver um projeto, crie um básico:

```bash
mkdir minha-api
cd minha-api
npm init -y
npm install express
```

Crie um arquivo `index.js`:

```js
const express = require("express");
const app = express();

const PORT = process.env.PORT || 3000;

app.get("/", (req, res) => {
  res.send("API rodando 🚀");
});

app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

---

## 📄 2. Configurar o package.json

Adicione o script de start:

```json
"scripts": {
  "start": "node index.js"
}
```

---

## 📁 3. Subir o projeto para o GitHub

```bash
git init
git add .
git commit -m "primeiro commit"
git branch -M main
git remote add origin https://github.com/seu-usuario/minha-api.git
git push -u origin main
```

---

## ☁️ 4. Criar serviço no Render

1. Acesse o Render
2. Clique em **"New +" → Web Service**
3. Conecte sua conta do GitHub
4. Selecione o repositório

---

## ⚙️ 5. Configurar o deploy

Preencha os campos:

* **Name:** minha-api
* **Environment:** Node
* **Build Command:**

  ```bash
  npm install
  ```
* **Start Command:**

  ```bash
  npm start
  ```

👉 Importante: o Render detecta automaticamente `process.env.PORT`, então não use porta fixa.

---

## 🚀 6. Fazer o deploy

Clique em **Create Web Service**

O Render vai:

* Instalar dependências
* Fazer build
* Subir o servidor

Após alguns segundos/minutos, sua API estará online:

```
https://minha-api.onrender.com
```

---

## 🧪 7. Testar a aplicação

Abra no navegador ou use:

```bash
curl https://minha-api.onrender.com
```

Resposta esperada:

```
API rodando 🚀
```

---

## 🔄 8. Deploy automático

Toda vez que você fizer:

```bash
git push
```

O Render fará deploy automático 🚀

---

## ⚠️ Problemas comuns

### ❌ App não inicia

* Verifique se existe `npm start`

### ❌ Porta errada

* Use sempre:

```js
process.env.PORT
```

### ❌ Build falha

* Confira se o `package.json` está correto

---

## 💡 Dicas extras

* Use `.env` para variáveis (configuradas no painel do Render)
* Ative logs para debug
* Use Docker se quiser mais controle

---
