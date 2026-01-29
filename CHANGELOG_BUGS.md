# 📋 CHANGELOG & REGISTRO DE BUGS - Dashboard Projetos Infraestrutura

> **Última atualização:** 29/01/2026  
> **Versão atual:** 6.1.1

---

## v6.1.1 (29/01/2026) - Correção de Modais

### 🐛 Bugs Corrigidos

#### BUG #015 - Modal de Impressão sem opções de filtro
**Problema:** Ao clicar em "Imprimir", o diálogo do navegador abria direto sem as opções de filtro que existiam antes.

**Antes esperado:**
- Modal com 4 opções: Filtro atual, Todos os projetos, Apenas críticos, Projetos específicos
- Lista de checkboxes para selecionar projetos específicos
- Busca por nome do projeto

**Solução:** Restaurado modal completo de impressão com todas as funcionalidades.

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

#### BUG #016 - Modal de PDF sem opções de filtro  
**Problema:** Ao clicar em "Gerar PDF", gerava o PDF direto sem opções de filtro.

**Antes esperado:**
- Modal idêntico ao de impressão com 4 opções
- Permitir gerar PDF apenas dos projetos críticos ou específicos

**Solução:** Restaurado modal completo de PDF com mesmas funcionalidades do modal de impressão.

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

#### BUG #017 - Botão "Imprimir" sumiu do modal de detalhes do projeto
**Problema:** Ao abrir o modal de detalhes de um projeto (clicando na linha), não tinha mais o botão "🖨️ Imprimir" que permitia imprimir apenas aquele projeto.

**Antes esperado:**
- Botão verde "🖨️ Imprimir" no cabeçalho do modal, ao lado do X de fechar
- Ao clicar, abre nova janela formatada com os dados daquele projeto específico

**Solução:** Restaurado botão `printProject()` no header do modal de detalhes.

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

## v6.1 (28/01/2026) - Correção de Carregamento

### 🐛 Bugs Corrigidos
- localStorage não carregava dados salvos → Corrigido para priorizar dados.json

---

## v6.0 (20/01/2026) - Arquitetura Dual (Projetos + Atividades)

### ✅ Novas Funcionalidades
- Separação em duas tabelas: Projetos e Atividades
- 20 atividades padronizadas por projeto
- Timeline visual no modal de detalhes
- Checklist de atividades com status individual
- Admin com drag-and-drop de Excel
- KPIs com tooltips explicativos
- Filtro "🚨 Apenas Críticos"
- Seção "Decisões Necessárias" expandida

### 🛠️ Melhorias
- Cálculo automático de progresso baseado em atividades
- Cálculo automático de dias parado
- Export de dados.json pelo admin

---

## v5.5.1 (20/01/2026) - Correções

### 🐛 Bugs Corrigidos
- Bloqueador com "NaN dias" → Validação de datas
- Layout index.html quebrado → CSS grid corrigido

---

## v5.5.0 (19/01/2026) - Index como Hub

### ✅ Novas Funcionalidades
- Index.html redesenhado como página inicial
- Cards de resumo rápido
- Botões para views
- Seção "Próximos Go Lives"

---

## v5.4.1 (20/01/2026) - Modal PDF com Opções

### ✅ Novas Funcionalidades
- Modal de PDF com opções de seleção (igual impressão)

---

## v5.4.0 (19/01/2026) - Checklist de 20 Atividades

### ✅ Novas Funcionalidades
- Migração de 12 etapas fixas para 20 atividades flexíveis
- Formato estruturado: `STATUS|DATA|DESCRIÇÃO;...`
- Modal com checklist visual

---

## v5.3 (17/01/2026) - Melhorias UX

### ✅ Novas Funcionalidades
- KPIs renomeados (No Prazo, Atraso Médio, etc.)
- Filtro por Go-Live (Este mês, 30/60/90 dias)
- Impressão por projetos específicos (checkboxes)
- Busca de projetos na lista de impressão

---

## 📁 LISTA DE ARQUIVOS DO PROJETO

| # | Arquivo | Descrição |
|---|---------|-----------|
| 1 | `admin.html` | Interface de administração - upload de Excel |
| 2 | `dados.json` | Dados em JSON (projetos + atividades) |
| 3 | `index.html` | Página inicial com resumo e navegação |
| 4 | `Template_Projetos_v6.xlsx` | Planilha modelo para importação |
| 5 | `view-detalhada.html` | Dashboard com análise detalhada |
| 6 | `view-simples.html` | Dashboard resumido com KPIs |
| 7 | `CHANGELOG_BUGS.md` | Este arquivo - histórico de versões |
| 8 | `README.md` | Documentação técnica completa |

---

## 🎯 REGRAS DE NEGÓCIO - PROJETO CRÍTICO

Um projeto é **CRÍTICO** se atender QUALQUER condição:
1. ⏰ Status = "Atrasado"
2. 🔴 Situação = "Vermelho"
3. 📅 Dias Parado ≥ 15
4. 🚫 Possui Bloqueador preenchido

---

## Contato

**Desenvolvido por:** Infraestrutura TI - Invent Corp  
**PMO:** Daiana  
**Última atualização:** 29/01/2026
