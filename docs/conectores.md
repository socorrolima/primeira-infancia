# Conectores — Documentação

## Contrato BaseConnector

Todo conector deve implementar três métodos:

| Método | Retorno | Propósito |
|--------|---------|-----------|
| `test_connection()` | `ConnectorResult` | Verifica se o serviço está acessível |
| `fetch_sample()` | `ConnectorResult` | Retorna uma pequena amostra de dados |
| `get_metadata()` | `dict` | Informações estáticas sobre a fonte |

## Conectores Implementados

### IBGE
- **Endpoint**: `GET https://servicodados.ibge.gov.br/api/v1/localidades/municipios`
- **Dados**: Todos os 5.570 municípios brasileiros com ID, nome e UF
- **Formato**: JSON REST, sem autenticação

### CadSUAS
- **Endpoint**: `https://aplicacoes.mds.gov.br/sagi/ri/relatorios/cadsuas`
- **Dados**: Portal HTML com relatórios de unidades SUAS (CRAS, CREAS)
- **Formato**: HTML — retorna metadados de acesso

### Programa Criança Feliz
- **Endpoint**: `https://aplicacoes.mds.gov.br/sagi/vis/data3/data-table.php`
- **Dados**: Dados de visitação domiciliar — compartilha URL com VIS DATA
- **Formato**: Portal interativo

### VIS DATA
- **Endpoint**: `https://aplicacoes.mds.gov.br/sagi/vis/data3/data-table.php`
- **Dados**: Plataforma de visualização SAGI/MDS (BPC, CadÚnico, SUAS)
- **Formato**: Portal interativo / JSON via parâmetros

### DATASUS
- **Endpoint**: `https://datasus.saude.gov.br/transferencia-de-arquivos`
- **Dados**: SINASC, SIM, SIAB — nascimentos e mortalidade infantil
- **Formato**: FTP / DBC comprimido

### Dados.gov.br
- **Endpoint**: `https://dados.gov.br/api/publico/conjuntos-dados`
- **Dados**: Busca por datasets com termo "primeira infância"
- **Formato**: JSON REST (API CKAN)

## Como Adicionar um Novo Conector

1. Criar `backend/connectors/novo_connector.py` herdando `BaseConnector`
2. Implementar `test_connection()`, `fetch_sample()` e `get_metadata()`
3. Adicionar URL em `config/settings.py`
4. Registrar em `services/connector_service.py` (CONNECTOR_REGISTRY + CONNECTOR_INFO)
5. Adicionar rota em `api/routes.py` (ou o loop existente cuida automaticamente se registrado)
