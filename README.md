 <p align="center">
  <img src="https://img.shields.io/badge/Django-0d1117?style=for-the-badge&logo=django&logoColor=00f0ff" />
  <img src="https://img.shields.io/badge/Django%20REST-0d1117?style=for-the-badge&logo=django&logoColor=00f0ff" />
  <img src="https://img.shields.io/badge/JWT-0d1117?style=for-the-badge&logo=jsonwebtokens&logoColor=00f0ff" />
  <img src="https://img.shields.io/badge/PostgreSQL-0d1117?style=for-the-badge&logo=postgresql&logoColor=00f0ff" />
</p>

# 🔐 Django JWT Authentication (DRF)

Implementação de autenticação e autorização baseada em tokens **JWT (JSON Web Tokens)** utilizando **Django REST Framework (DRF)**. Este projeto demonstra autenticação stateless, gerenciamento de tokens e controle de acesso a endpoints em APIs REST.

---

## 🚀 Funcionalidades

- **Autenticação baseada em tokens:** geração de Access Token e Refresh Token utilizando `djangorestframework-simplejwt`.
- **Gerenciamento de usuários:** endpoints para cadastro, login e renovação de tokens.
- **Rotas protegidas:** endpoints que exigem um token válido no cabeçalho `Authorization: Bearer <token>`.
- **Estrutura modular:** organização em aplicativos Django separados para configuração e autenticação (`userauth` e `djangojwtauth`).

---

## 🛠️ Tecnologias utilizadas

- Python 3.11+
- Django
- Django REST Framework (DRF)
- SimpleJWT
- SQLite / PostgreSQL

---

## ⚙️ Como executar o projeto localmente

### 1. Clonar o repositório

```bash
git clone https://github.com/LeonSantana7/django-jwt-auth.git
cd django-jwt-auth
```

### 2. Criar e ativar o ambiente virtual

```bash
python -m venv venv
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

**Windows (CMD):**

```bat
venv\Scripts\activate
```

### 3. Instalar as dependências

```bash
pip install -r requirements.txt
```

Caso o projeto não tenha um arquivo `requirements.txt`, instale as dependências manualmente:

```bash
pip install django djangorestframework djangorestframework-simplejwt
```

### 4. Executar as migrações

```bash
python manage.py migrate
```

Se você tiver criado ou alterado modelos, gere as migrações antes:

```bash
python manage.py makemigrations
python manage.py migrate
```

### 5. Iniciar o servidor

```bash
python manage.py runserver
```

A API estará disponível em:

`http://127.0.0.1:8000/`

---

## 🔌 Endpoints principais

| Método | Endpoint | Descrição | Autenticação |
|---|---|---|---|
| `POST` | `/api/users/register/` | Cadastro de usuário | Não |
| `POST` | `/api/token/` | Login e obtenção dos tokens | Não |
| `POST` | `/api/token/refresh/` | Renovação do Access Token | Não |
| `GET` | `/api/protected-route/` | Exemplo de rota protegida | Sim — Bearer Token |

> **Observação:** os endpoints acima representam a estrutura documentada do projeto. Confirme se os caminhos correspondem às rotas configuradas no código.

---

## 🔑 Exemplo de autenticação

### Obter tokens

Envie uma requisição `POST` para `/api/token/` com as credenciais do usuário:

```json
{
  "username": "seu_usuario",
  "password": "sua_senha"
}
```

Exemplo de resposta:

```json
{
  "refresh": "seu_refresh_token",
  "access": "seu_access_token"
}
```

### Acessar uma rota protegida

Inclua o Access Token no cabeçalho da requisição:

```http
Authorization: Bearer seu_access_token
```

O acesso será permitido se o token for válido e o endpoint exigir esse tipo de autenticação.

---

## 📁 Estrutura do projeto

```text
django-jwt-auth/
├── djangojwtauth/       # Configurações principais do Django
├── userauth/            # Aplicação de usuários e autenticação
├── db.sqlite3           # Banco de dados local, se versionado
├── manage.py            # Utilitário de gerenciamento do Django
├── requirements.txt     # Dependências do projeto
└── README.md            # Documentação
```

A estrutura pode variar conforme a implementação atual do repositório.

---

## 🔒 Boas práticas de segurança

- Não compartilhe senhas, chaves secretas ou tokens reais.
- Não versione arquivos `.env` com credenciais.
- Utilize HTTPS em ambientes de produção.
- Configure corretamente os tempos de expiração dos tokens.
- Mantenha as dependências atualizadas.
- Utilize variáveis de ambiente para configurações sensíveis.

---

## 👨‍💻 Autor

**Leon Santana**


Sugestões, melhorias e contribuições são bem-vindas por meio de issues e pull requests.
