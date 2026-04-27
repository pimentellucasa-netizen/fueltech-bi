# Fueltech BI — Análise de Pedidos

Dashboard de Business Intelligence para análise dos pedidos da Fueltech (2023–2026), com filtros encadeados, mapa coroplético do Brasil, comparações temporais estilo GA4 e diagnóstico por cliente.

## Como abrir

Basta abrir o arquivo `dashboard_fueltech.html` em qualquer navegador moderno (Chrome, Edge, Firefox). Não precisa de servidor — é um SPA estático.

```bash
# Windows
start dashboard_fueltech.html
# macOS
open dashboard_fueltech.html
# Linux
xdg-open dashboard_fueltech.html
```

## Estrutura

| Arquivo | Descrição |
|---|---|
| `dashboard_fueltech.html` | Dashboard principal (HTML/CSS/JS inline) |
| `dashboard_data.js` | Dados consolidados 2023–2026 (gerado a partir dos `.xltx`) |
| `dashboard_chart.js` | Biblioteca Chart.js (bundled) |
| `dashboard_geo.js` | TopoJSON dos estados do Brasil |

## Funcionalidades

- **Filtros encadeados**: cliente (Cd ou Nome), período (calendário GA4 com zoom dia→mês→ano + quick ranges), UF, tabela de compra, produto, vendedor.
- **KPIs**: pedidos, faturamento, ticket médio, clientes únicos.
- **Mapa coroplético** do Brasil com gradiente de intensidade.
- **Top 10 Produtos**: respeita o filtro de período e exibe unidades em cada barra.
- **Diagnóstico de cliente**: ao filtrar por Cd ou Nome, mostra os últimos 3 pedidos e flags de queda nas unidades.
- **Auto-fill Cd → Nome/Fantasia**: ao digitar o código, o campo de nome é populado automaticamente.
- **Comparação temporal YoY** (vs. mesmo período do ano anterior).
- **Tema claro/escuro** com persistência em localStorage.

## Processamento dos dados

Os arquivos brutos `.xltx` ficam no ERP da Fueltech e **não são versionados** neste repositório (ver `.gitignore`). O arquivo `dashboard_data.js` é gerado a partir deles via script Python (consulte o documento de especificação do projeto).

## Stack

HTML + CSS + JavaScript puro (sem framework).
- Chart.js para gráficos
- SVG para mapa coroplético
- localStorage para persistência de tema

---

*Projeto interno — Fueltech*
