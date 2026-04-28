# 🚀 Deploy de uma API Python completa (Flask) no Render

## 📌 O que vamos construir

Uma API REST simples com:

* Rotas GET
* Retorno em JSON
* Estrutura organizada
* Pronta para produção com Gunicorn

---

## 🧱 1. Estrutura do projeto

```
minha-api/
│── app.py
│── requirements.txt
```

---

## 🧠 2. Criando a API

Instale as dependências:

```bash
pip install flask gunicorn
```

Crie o arquivo `app.py`:

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

# Dados mockados
usuarios = [
    {"id": 1, "nome": "João"},
    {"id": 2, "nome": "Maria"}
]

@app.route("/")
def home():
    return jsonify({"mensagem": "API rodando 🚀"})

@app.route("/usuarios", methods=["GET"])
def listar_usuarios():
    return jsonify(usuarios)

@app.route("/usuarios/<int:id>", methods=["GET"])
def buscar_usuario(id):
    usuario = next((u for u in usuarios if u["id"] == id), None)
    if usuario:
        return jsonify(usuario)
    return jsonify({"erro": "Usuário não encontrado"}), 404

@app.route("/usuarios", methods=["POST"])
def criar_usuario():
    data = request.get_json()
    novo = {
        "id": len(usuarios) + 1,
        "nome": data.get("nome")
    }
    usuarios.append(novo)
    return jsonify(novo), 201

if __name__ == "__main__":
    app.run()
```

---

## 📄 3. Criar o requirements.txt

```bash
pip freeze > requirements.txt
```

---

## 📁 4. Subir para o GitHub

```bash
git init
git add .
git commit -m "API pronta"
git branch -M main
git remote add origin https://github.com/seu-usuario/minha-api.git
git push -u origin main
```

---

## ☁️ 5. Criar serviço no Render

1. Acesse o Render
2. Clique em **New + → Web Service**
3. Conecte ao GitHub
4. Selecione o repositório

---

## ⚙️ 6. Configuração do deploy

* **Environment:** Python 3
* **Build Command:**

  ```bash
  pip install -r requirements.txt
  ```
* **Start Command:**

  ```bash
  gunicorn app:app
  ```

---

## 🚀 7. Deploy

Clique em **Create Web Service**

Sua API ficará disponível em algo como:

```
https://minha-api.onrender.com
```

---

## 🧪 8. Testando a API

### 🔹 Rota inicial

```bash
curl https://minha-api.onrender.com/
```

---

### 🔹 Listar usuários

```bash
curl https://minha-api.onrender.com/usuarios
```

---

### 🔹 Buscar usuário

```bash
curl https://minha-api.onrender.com/usuarios/1
```

---

### 🔹 Criar usuário

```bash
curl -X POST https://minha-api.onrender.com/usuarios \
-H "Content-Type: application/json" \
-d '{"nome": "Carlos"}'
```

---

## 🔄 9. Deploy automático

Sempre que fizer:

```bash
git push
```

O Render atualiza automaticamente 🚀

---

## ⚠️ Boas práticas

* Use variáveis de ambiente (Render Dashboard)
* Não use dados em memória em produção (use banco de dados)
* Ative logs para debug

---

## 💡 Próximos passos

Para evoluir essa API:

* 🐘 Banco com PostgreSQL (no próprio Render)
* 🔐 Autenticação com JWT
* ⚡ Migrar para FastAPI (mais performático)
* 🧱 Usar Django para projetos maiores

---
