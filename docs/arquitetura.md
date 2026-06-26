# Arquitetura — Fase 1

## Visão Geral

A Fase 1 é uma aplicação FastAPI que valida conectividade com seis fontes de dados públicas brasileiras relacionadas à primeira infância. Nenhum dado é persistido.

## Camadas

```
Request HTTP
    └── FastAPI (app.py)
        └── APIRouter (api/routes.py)
            └── ConnectorService (services/connector_service.py)
                └── ConcreteConnector (connectors/*.py)
                    └── BaseConnector (connectors/base_connector.py)
                        └── timed_get (utils/request_helper.py)
```

## Padrões Utilizados

- **Template Method**: `BaseConnector.run()` orquestra `test_connection()` + `fetch_sample()`
- **Factory**: `ConnectorService.run_connector()` instancia conectores por ID
- **Settings via Pydantic**: todas as URLs e configurações centralizadas em `config/settings.py`
- **Modelo padronizado**: `ConnectorResult` garante resposta uniforme em todos os endpoints

## Decisões de Design

- Sem banco de dados na Fase 1 — apenas validação de conectividade
- Sem autenticação — todas as fontes são públicas
- Sem filas ou async HTTP — simplicidade intencional para validação
- Um arquivo por conector — facilita adição de novas fontes
