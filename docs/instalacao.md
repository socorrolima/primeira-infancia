# Instalação e Execução

## Pré-requisitos

- Python 3.11+
- pip

## Passos

```bash
# 1. Entrar no diretório do projeto
cd C:\Users\User\OneDrive\Documentos\Projetos_web\primeira-infancia

# 2. Criar ambiente virtual
python -m venv .venv

# 3. Ativar ambiente virtual (Windows)
.venv\Scripts\activate

# 4. Instalar dependências
pip install -r requirements.txt

# 5. Configurar variáveis de ambiente (opcional — há defaults)
copy .env.example .env

# 6. Iniciar o servidor
cd backend
python main.py
```

## Acessar a Interface

Abrir no navegador: http://localhost:8000

## Executar os Testes

```bash
cd backend
python -m pytest tests/ -v
```

## Endpoints Disponíveis

| Método | URL | Descrição |
|--------|-----|-----------|
| GET | http://localhost:8000/ | Interface web |
| GET | http://localhost:8000/api/connectors | Lista conectores (JSON) |
| POST | http://localhost:8000/api/test/ibge | Testa IBGE |
| POST | http://localhost:8000/api/test/cadsuas | Testa CadSUAS |
| POST | http://localhost:8000/api/test/crianca-feliz | Testa Criança Feliz |
| POST | http://localhost:8000/api/test/visdata | Testa VIS DATA |
| POST | http://localhost:8000/api/test/datasus | Testa DATASUS |
| POST | http://localhost:8000/api/test/dadosgov | Testa Dados.gov.br |
| GET | http://localhost:8000/docs | Swagger UI |
