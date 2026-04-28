# 🚀 Deploy de uma API Python (Flask) no Render

## 📦 Pré-requisitos

Antes de começar, você precisa ter:

* Python 3 instalado
* Conta no GitHub
* Conta no Render

---

## 🧱 1. Criando uma API Flask simples

Crie a pasta do projeto:

```bash
mkdir minha-api-python
cd minha-api-python
```

Crie um ambiente virtual:

```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows
```

Instale o Flask e o Gunicorn (necessário para produção):

```bash
pip install flask gunicorn
```

Crie o arquivo `app.py`:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "API Python rodando 🚀"

if __name__ == "__main__":
    app.run()
```

---

## 📄 2. Criar o requirements.txt

```bash
pip freeze > requirements.txt
```

---

## ⚙️ 3. Configurar o comando de start

O Render usa **Gunicorn**, então o comando será:

```bash
gunicorn app:app
```

👉 Estrutura: `arquivo:variável`

---

## 📁 4. Subir para o GitHub

```bash
git init
git add .
git commit -m "primeiro commit"
git branch -M main
git remote add origin https://github.com/seu-usuario/minha-api-python.git
git push -u origin main
```

---

## ☁️ 5. Criar serviço no Render

1. Acesse o Render
2. Clique em **"New +" → Web Service**
3. Conecte com o GitHub
4. Selecione o repositório

---

## ⚙️ 6. Configurar o deploy

Preencha assim:

* **Name:** minha-api-python
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

## 🚀 7. Fazer o deploy

Clique em **Create Web Service**

O Render vai:

* Instalar dependências
* Subir o servidor com Gunicorn
* Gerar uma URL pública

Exemplo:

```
https://minha-api-python.onrender.com
```

---

## 🧪 8. Testar a API

No navegador ou terminal:

```bash
curl https://minha-api-python.onrender.com
```

Resposta:

```
API Python rodando 🚀
```

---

## 🔄 9. Deploy automático

Sempre que fizer:

```bash
git push
```

O Render atualiza automaticamente 🚀

---

## ⚠️ Problemas comuns

### ❌ Erro: Module not found

* Verifique se está no `requirements.txt`

### ❌ App não inicia

* Confirme o comando:

```bash
gunicorn app:app
```

### ❌ Porta incorreta

* Não defina porta manualmente (o Render faz isso automaticamente)

---

## 💡 Dicas extras

* Use variáveis de ambiente no painel do Render

* Para projetos maiores, use:

  * Django
  * FastAPI

* Logs do deploy ajudam muito no debug

---

Também podemos criar:

* 🔐 Autenticação com JWT
* 🐘 Banco de dados PostgreSQL no Render
* ⚡ Deploy de FastAPI (mais performático que Flask)


