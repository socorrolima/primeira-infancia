# Estrutura de Arquivos

```
primeira-infancia/
├── requirements.txt          — Dependências Python
├── .env.example              — Variáveis de ambiente de exemplo
├── .gitignore
├── README.md
├── backend/
│   ├── app.py                — Instância FastAPI + rotas estáticas + template
│   ├── main.py               — Entry point (uvicorn)
│   ├── config/
│   │   └── settings.py       — Configurações via pydantic-settings
│   ├── connectors/
│   │   ├── base_connector.py     — Contrato abstrato ABC
│   │   ├── ibge_connector.py     — IBGE Localidades
│   │   ├── cadsuas_connector.py  — CadSUAS MDS
│   │   ├── crianca_feliz_connector.py — Programa Criança Feliz
│   │   ├── visdata_connector.py  — VIS DATA SAGI
│   │   ├── datasus_connector.py  — DATASUS Saúde
│   │   └── dadosgov_connector.py — Dados.gov.br
│   ├── services/
│   │   └── connector_service.py  — Orquestração e registro de conectores
│   ├── api/
│   │   └── routes.py             — Endpoints REST FastAPI
│   ├── models/
│   │   └── connector_result.py   — Pydantic models de resposta
│   ├── utils/
│   │   ├── logger.py             — Logger centralizado
│   │   └── request_helper.py     — timed_get com tratamento de erros
│   ├── templates/
│   │   └── index.html            — Interface web (Jinja2 + Bootstrap)
│   ├── static/
│   │   ├── css/style.css         — Estilos customizados
│   │   └── js/app.js             — Lógica frontend
│   ├── logs/
│   │   └── application.log       — Log gerado em runtime
│   └── tests/
│       ├── test_base_connector.py
│       ├── test_ibge_connector.py
│       ├── test_dadosgov_connector.py
│       └── test_connector_service.py
└── docs/
    ├── arquitetura.md
    ├── conectores.md
    ├── instalacao.md
    └── estrutura.md
```
