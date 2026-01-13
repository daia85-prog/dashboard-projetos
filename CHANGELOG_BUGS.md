# 📋 REGISTRO DE BUGS E CORREÇÕES - Dashboard Projetos Infraestrutura

> **Última atualização:** 12/01/2026
> **Versão atual:** 5.0

---

## 🐛 BUGS CORRIGIDOS

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

## ✅ MELHORIAS IMPLEMENTADAS (v5.0)

### Automação da Planilha
| Campo | Implementação |
|-------|---------------|
| Progresso | `=VLOOKUP(Etapa, TabelaProgresso, 2, FALSE)` |
| Situação | Fórmula complexa baseada em: dias parado > 15, bloqueador preenchido, status |
| Retrocesso | `=IF(MATCH(EtapaAtual) < MATCH(EtapaAnterior), "⚠️ RETROCESSO", "")` |

### Responsáveis Separados
- PMO Interno
- Infra Interno
- PMO Cliente
- Infra Cliente

### Nova ordem de colunas na tabela
1. Projeto
2. Localização
3. Go Live
4. Status
5. Situação
6. Progresso
7. Etapa
8. PMO Interno
9. Dias Parado

### Modal de Impressão
Opções adicionadas:
- Página atual (filtrada)
- Todos os projetos
- Apenas críticos

### Card "Parados 15+ dias"
Novo card nos dashboards para destacar projetos sem atualização.

---

## ⚠️ PONTOS DE ATENÇÃO PARA FUTURAS MODIFICAÇÕES

### Ao modificar filtros:
1. **SEMPRE** usar `filteredProjects` (não `projects`) para:
   - Contagem dos cards
   - Renderização de gráficos
   - Renderização de tabelas
   - Renderização de seções

2. **SEMPRE** chamar `renderCharts()` dentro de `updateDashboard()`

### Ao adicionar novos campos:
1. Atualizar `parseData()` no `admin.html`
2. Atualizar `dados.json` de exemplo
3. Atualizar tabelas em ambas as views
4. Atualizar modal de detalhes

### Ao modificar etapas:
1. Atualizar lista na aba "Listas" da planilha
2. Atualizar tabela TabelaProgresso (Etapa → %)
3. Named Range "Etapa" já cobre 50 linhas

---

## 📁 ESTRUTURA DE ARQUIVOS

```
dashboard-projetos/
├── index.html          # Página inicial com cards resumo
├── view-simples.html   # Dashboard consolidado
├── view-detalhada.html # Dashboard segmentado por status
├── admin.html          # Importação/exportação de dados
├── dados.json          # Dados dos projetos (atualizar via admin)
└── Template_Projetos_v5.xlsx  # Planilha com automações
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

*Documento mantido para evitar regressão de bugs em futuras modificações.*
