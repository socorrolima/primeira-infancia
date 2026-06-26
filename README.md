# Conectores Primeira Infância — Fase 1

Sistema de validação de conectividade com bases públicas de dados da primeira infância.

## Objetivo da Fase 1

Validar a conectividade com seis fontes de dados governamentais e exibir uma amostra padronizada dos resultados retornados. Nenhum dado é armazenado.

## Fontes de Dados

| Conector | Fonte | Tipo |
|----------|-------|------|
| IBGE | API de Localidades | JSON REST |
| CadSUAS | Cadastro Nacional do SUAS | Portal HTML |
| Programa Criança Feliz | SAGI/MDS | Portal HTML |
| VIS DATA | SAGI/MDS | Portal interativo |
| DATASUS | Ministério da Saúde | FTP/Portal |
| Dados.gov.br | Portal de Dados Abertos | JSON REST |

## Arquitetura

```
backend/
├── app.py              # FastAPI app
├── main.py             # Entry point
├── config/             # Configurações centralizadas
├── connectors/         # Um conector por fonte (herdam BaseConnector)
├── services/           # Orquestração dos conectores
├── api/                # Rotas REST
├── models/             # Pydantic models
├── utils/              # Logger e request helper
├── templates/          # HTML (Jinja2)
└── static/             # CSS e JS
```

## Instalação

```bash
cd backend
python -m venv .venv
.venv\Scripts\activate      # Windows
pip install -r ../requirements.txt
```

## Como Executar

```bash
cd backend
python main.py
# Acesse: http://localhost:8000
```

## Endpoints da API

| Método | Rota | Descrição |
|--------|------|-----------|
| GET | / | Interface web |
| GET | /api/connectors | Lista conectores |
| POST | /api/test/ibge | Testa IBGE |
| POST | /api/test/cadsuas | Testa CadSUAS |
| POST | /api/test/crianca-feliz | Testa Criança Feliz |
| POST | /api/test/visdata | Testa VIS DATA |
| POST | /api/test/datasus | Testa DATASUS |
| POST | /api/test/dadosgov | Testa Dados.gov.br |

## Como Adicionar um Novo Conector

1. Crie `backend/connectors/novo_connector.py` herdando `BaseConnector`
2. Implemente `test_connection()`, `fetch_sample()` e `get_metadata()`
3. Adicione a URL em `config/settings.py`
4. Registre em `services/connector_service.py` (CONNECTOR_REGISTRY e CONNECTOR_INFO)
5. Adicione o endpoint em `api/routes.py`

## Roadmap

- **Fase 2**: Download e armazenamento dos arquivos brutos
- **Fase 3**: Transformação e padronização dos dados
- **Fase 4**: Persistência em PostgreSQL
- **Fase 5**: API de consulta e filtros
- **Fase 6**: Dashboard analítico
- **Fase 7**: Integração com agentes de IA
