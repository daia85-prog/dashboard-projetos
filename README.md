# 📊 Dashboard Projetos - Infraestrutura TI

> Sistema de acompanhamento de status de projetos de infraestrutura para gestores.

---

## 🚀 Versão Atual: **5.3.1** (18/01/2026)

---

## 📁 Estrutura de Arquivos (7 arquivos do projeto)

| # | Arquivo | Descrição |
|---|---------|-----------|
| 1 | `index.html` | Página inicial com resumo e seletor de views |
| 2 | `view-simples.html` | Dashboard consolidado (visão resumida) |
| 3 | `view-detalhada.html` | Dashboard segmentado por status (visão completa) |
| 4 | `admin.html` | Área administrativa para importar/exportar dados |
| 5 | `dados.json` | Dados dos projetos (gerado pelo admin.html) |
| 6 | `Template_Projetos_v5.xlsx` | Planilha Excel para preenchimento dos dados |
| 7 | `CHANGELOG_BUGS.md` | Registro de versões, bugs e correções |

> **Nota:** O `README.md` é o 8º arquivo no repositório, usado apenas para documentação.

---

## ✨ Funcionalidades

### KPIs do Dashboard
- **No Prazo** - Projetos com go-live dentro do prazo original
- **Atraso Médio** - Média de dias de atraso nos go-lives
- **Projetos Atualizados** - % de projetos atualizados nos últimos 7 dias
- **Tempo Médio Parado** - Média de dias sem atualização

### Filtros Disponíveis
- 🔍 Busca por nome do projeto
- 📊 Status (Em Andamento, Concluído, Atrasado, etc.)
- 🚦 Situação (Verde, Amarelo, Vermelho, Cinza)
- 👤 PMO Interno responsável
- ⏰ Projetos Parados (7+, 15+, 30+, 60+ dias)
- 📅 **Go-Live** (Este mês, Próx. 30/60/90 dias, Atrasados)

### Impressão
- Página atual (filtrada)
- Todos os projetos
- Apenas críticos
- **Projetos específicos** (seleção por checkboxes)

### Painel "Próximos Go Lives"
Mostra os **próximos projetos a entrarem em produção**, ordenados por data:
- 📅 **Data do Go-Live** - Data de entrada em produção
- ⏱️ **Indicador de dias** - Quantos dias faltam (ou "X dias atrás" se atrasado)
- 🏷️ **Nome do projeto** - Com cor indicando situação (verde/amarelo/vermelho)

> **Importante:** O Go-Live é a data de **implantação final** do projeto, não etapas intermediárias.

---

## 🔄 Como Atualizar os Dados

1. Abra a planilha `Template_Projetos_v5.xlsx`
2. Preencha/atualize os dados dos projetos
3. Selecione tudo: **Ctrl+T** (Excel Desktop) ou **Ctrl+A** (Excel Online)
4. Copie: **Ctrl+C**
5. Abra o `admin.html` no navegador
6. Cole os dados: **Ctrl+V**
7. Clique em **"Carregar e Validar"**
8. Clique em **"Exportar dados.json"**
9. Faça upload do `dados.json` no GitHub
10. Aguarde 1-2 min e acesse o dashboard com **Ctrl+Shift+R**

---

## 📋 Histórico de Versões

| Versão | Data | Mudanças |
|--------|------|----------|
| **5.3.1** | 18/01/2026 | Correção NaN nos KPIs, Filtros zeram cards, Data hoje/ontem, Próximos Go Lives corrigido |
| 5.3 | 17/01/2026 | KPIs simplificados, Filtro Go-Live, Impressão por nome do projeto |
| 5.2 | 16/01/2026 | Correção KPIs, Filtros parados expandidos (7+, 15+, 30+, 60+) |
| 5.0 | 12/01/2026 | Automação planilha, Responsáveis separados, Sistema anti-burla |
| 4.x | - | Versões anteriores |

---

## 👩‍💻 Desenvolvido por

**Infraestrutura TI - Invent Corp**

---

*Para detalhes técnicos e registro de bugs, consulte o arquivo `CHANGELOG_BUGS.md`*
