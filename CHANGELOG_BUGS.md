# 📋 REGISTRO DE BUGS E CORREÇÕES - Dashboard Projetos Infraestrutura

> **Última atualização:** 17/01/2026
> **Versão atual:** 5.3

---

## 🆕 NOVIDADES v5.3 (17/01/2026)

### 1. KPIs com Nomes Simplificados
**Mudança:** Renomeados para linguagem mais clara e direta.

| Antes | Agora |
|-------|-------|
| On-Time (Go Live) | **No Prazo** |
| Delta Médio GoLive | **Atraso Médio** |
| Taxa Atualização | **Projetos Atualizados** |
| Aging Médio | **Tempo Médio Parado** |

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

### 2. Novo Filtro por Go-Live
**Funcionalidade:** Filtrar projetos pelo período do Go-Live.

| Opção | Descrição |
|-------|-----------|
| Todos | Sem filtro |
| Este Mês | Go-lives até o fim do mês atual |
| Próx. 30 dias | Go-lives nos próximos 30 dias |
| Próx. 60 dias | Go-lives nos próximos 60 dias |
| Próx. 90 dias | Go-lives nos próximos 90 dias |
| Atrasados | Go-live já passou e projeto não concluído |

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

### 3. Impressão por Projetos Específicos
**Mudança:** Substituída seleção por números (1;3;5) por seleção por nome do projeto.

**Antes:**
- Input de texto: "Digite os números separados por ;"
- Ex: 1;3;5;10

**Agora:**
- Lista de checkboxes com nomes dos projetos
- Botão "Selecionar todos" para marcar/desmarcar
- Visual mais intuitivo e menos propenso a erros

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

## 🛠 BUGS CORRIGIDOS

### BUG #001 - Filtros não atualizam os cards de status
**Problema:** Ao aplicar filtros (status, situação, PMO, dias parados), os cards superiores (Total, Concluídos, Em Andamento, etc.) continuavam mostrando os números totais ao invés dos filtrados.

**Causa:** A função `updateDashboard()` usava `projects` (array original) ao invés de `filteredProjects` (array filtrado) para calcular os números dos cards.

**Solução:** Alterar todas as referências de `projects` para `filteredProjects` na atualização dos cards:
```javascript
// ERRADO (antes)
document.getElementById('totalProjects').textContent = projects.length;

// CORRETO (depois)
document.getElementById('totalProjects').textContent = filteredProjects.length;
```

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

### BUG #002 - Gráficos não atualizam com filtros
**Problema:** Os gráficos (pizza e barras) não refletiam os dados filtrados.

**Causa:** A função `renderCharts()` usava `projects` ao invés de `filteredProjects`.

**Solução:** 
1. Chamar `renderCharts()` dentro de `updateDashboard()` após aplicar filtros
2. Usar `filteredProjects` em todas as contagens dos gráficos

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

### BUG #003 - Gráficos repetitivos na View Resumida
**Problema:** Os dois gráficos (Distribuição e Por Status) mostravam praticamente a mesma informação, só mudando o estilo.

**Solução:** Substituir o segundo gráfico por "Projetos Parados" - barras horizontais mostrando dias sem atualização de cada projeto, com cores indicando criticidade:
- 🔴 Vermelho: > 15 dias
- 🟡 Amarelo: 7-15 dias
- 🟢 Verde: < 7 dias

**Arquivos afetados:** `view-simples.html`

---

### BUG #004 - Atalho de teclado errado nas instruções
**Problema:** Instruções diziam "Ctrl+A" para selecionar tudo no Excel, mas no Excel Desktop é "Ctrl+T".

**Solução:** Atualizar instruções para:
- Excel Desktop: **Ctrl+T**
- Excel Online: **Ctrl+A**

**Arquivos afetados:** `admin.html`, `Template_Projetos_v5.xlsx` (aba Instruções)

---

### BUG #005 - GitHub Pages não atualiza após upload
**Problema:** Usuário fazia upload dos arquivos mas dashboard não refletia mudanças.

**Causa:** 
1. Usuário não estava exportando o `dados.json` do admin.html
2. Cache do navegador
3. Demora de 1-2 minutos do GitHub Pages para rebuild

**Solução:** Documentar workflow completo:
1. Preencher planilha
2. Copiar dados (Ctrl+T / Ctrl+A)
3. Colar no admin.html
4. Clicar "Carregar e Validar"
5. Clicar "Exportar dados.json" ← **PASSO CRÍTICO**
6. Upload no GitHub
7. Aguardar 1-2 min
8. Hard refresh (Ctrl+Shift+R)

**Arquivos afetados:** `admin.html` (instruções adicionadas)

---

### BUG #006 - "?" aparecendo antes do nome dos KPIs (v5.2)
**Problema:** O tooltip de ajuda (?) aparecia antes do texto do KPI ao invés de ao lado.

**Causa:** Estrutura HTML incorreta do kpi-header.

**Solução:** Reestruturar HTML separando label e help icon corretamente:
```html
<div class="kpi-header">
    <div class="kpi-label">No Prazo</div>
    <div class="kpi-help">?<div class="kpi-tooltip">Explicação...</div></div>
</div>
```

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

### BUG #007 - Busca não encontrava projeto BETA (v5.2)
**Problema:** Ao digitar "Bet" na busca, projeto BETA não aparecia.

**Causa:** Não era bug - o filtro "Parados 15+ dias" estava ativo e BETA tinha apenas 12 dias sem atualização. Os filtros são cumulativos.

**Solução:** Documentação e esclarecimento. Comportamento correto.

---

## ✅ MELHORIAS IMPLEMENTADAS

### v5.3 (17/01/2026)
- ✅ KPIs com nomes simplificados (No Prazo, Atraso Médio, etc.)
- ✅ Filtro por Go-Live (Este mês, 30/60/90 dias, Atrasados)
- ✅ Impressão por projetos específicos (checkboxes com nomes)
- ✅ Filtro de parados expandido (7+, 15+, 30+, 60+ dias)

### v5.2 (16/01/2026)
- ✅ Correção do posicionamento do "?" nos KPIs
- ✅ Filtros de parados expandidos (7+, 15+, 30+, 60+ dias)
- ✅ Opção de impressão por números específicos

### v5.0 (12/01/2026)
- ✅ Automação da Planilha (Progresso, Situação, Retrocesso)
- ✅ Responsáveis Separados (PMO/Infra Interno/Cliente)
- ✅ Nova ordem de colunas na tabela
- ✅ Modal de Impressão com opções
- ✅ Card "Parados 15+ dias"

---

## ⚠️ PONTOS DE ATENÇÃO PARA FUTURAS MODIFICAÇÕES

### Ao modificar filtros:
1. **SEMPRE** usar `filteredProjects` (não `projects`) para:
   - Contagem dos cards
   - Renderização de gráficos
   - Renderização de tabelas
   - Renderização de seções

2. **SEMPRE** chamar `renderCharts()` dentro de `updateDashboard()`

3. **Filtro de Go-Live** usa `parseDate()` - manter formato dd/mm/aaaa

### Ao adicionar novos campos:
1. Atualizar `parseData()` no `admin.html`
2. Atualizar `dados.json` de exemplo
3. Atualizar tabelas em ambas as views
4. Atualizar modal de detalhes

### Ao modificar etapas:
1. Atualizar lista na aba "Listas" da planilha
2. Atualizar tabela TabelaProgresso (Etapa → %)
3. Named Range "Etapa" já cobre 50 linhas

### Ao modificar impressão:
1. A lista de checkboxes é gerada dinamicamente em `populateProjectsCheckboxes()`
2. A seleção é processada em `executePrint()` buscando checkboxes marcados

---

## 📁 ESTRUTURA DE ARQUIVOS

```
dashboard-projetos/
├── index.html              # Página inicial com cards resumo
├── view-simples.html       # Dashboard consolidado
├── view-detalhada.html     # Dashboard segmentado por status
├── admin.html              # Importação/exportação de dados
├── dados.json              # Dados dos projetos (atualizar via admin)
├── Template_Projetos_v5.xlsx   # Planilha com automações
└── CHANGELOG_BUGS.md       # Este arquivo - registro de mudanças
```

---

## 🔄 WORKFLOW DE ATUALIZAÇÃO

```
Planilha (Excel)
     ↓ Ctrl+T / Ctrl+A + Ctrl+C
admin.html (Validar)
     ↓ Exportar
dados.json (Download)
     ↓ Upload
GitHub Repository
     ↓ 1-2 min
GitHub Pages (Live)
     ↓ Ctrl+Shift+R
Dashboard Atualizado
```

---

## 📊 HISTÓRICO DE VERSÕES

| Versão | Data | Principais Mudanças |
|--------|------|---------------------|
| 5.3 | 17/01/2026 | KPIs simplificados, Filtro Go-Live, Impressão por nome |
| 5.2 | 16/01/2026 | Correção KPIs, Filtros parados expandidos |
| 5.0 | 12/01/2026 | Automação planilha, Responsáveis separados |
| 4.x | - | Versões anteriores |

---

*Documento mantido para evitar regressão de bugs em futuras modificações.*
