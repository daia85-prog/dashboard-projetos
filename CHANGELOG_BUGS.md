# 📋 REGISTRO DE BUGS E CORREÇÕES - Dashboard Projetos Infraestrutura

> **Última atualização:** 18/01/2026
> **Versão atual:** 5.3.2

---

## 🆕 MELHORIAS v5.3.2 (18/01/2026)

### MELHORIA #012 - Busca de projetos na impressão
**Descrição:** Adicionado campo de busca para filtrar projetos na lista de impressão.

**Funcionalidade:** Digite o nome do projeto para localizar rapidamente entre muitos projetos.

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

### MELHORIA #013 - Lista de projetos ordenada alfabeticamente
**Descrição:** A lista de projetos para impressão agora é exibida em ordem alfabética.

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`

---

### MELHORIA #014 - Histórico de etapas no modal de detalhes
**Descrição:** O modal de detalhes do projeto agora exibe as datas de conclusão das etapas anteriores (Kick-off, Levantamento, Desenvolvimento, Homologação, Go-Live).

**Campos necessários na planilha:** 
- Etapa 1 - Kick-off
- Etapa 2 - Levantamento
- Etapa 3 - Desenvolvimento
- Etapa 4 - Homologação
- Etapa 5 - Go Live

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`, `admin.html`

---

### MELHORIA #015 - Observações/Anotações no modal de detalhes
**Descrição:** O modal de detalhes agora exibe o campo de observações/anotações do projeto.

**Campo na planilha:** Observações (ou Anotações)

**Arquivos afetados:** `view-simples.html`, `view-detalhada.html`, `admin.html`

---

## ✅ CORREÇÕES v5.3.1 (18/01/2026)

### BUG #008 - KPI "Atraso Médio" mostrando "NaN dias"
### BUG #009 - Filtros não zeram os cards de status (regressão)
### BUG #010 - Data "hoje" incorreta na página inicial
### BUG #011 - "Próximos Go Lives" mostrando dados incorretos

---

## 📦 ESTRUTURA DE ARQUIVOS v5.3.2

| Arquivo | Descrição |
|---------|-----------|
| index.html | Página inicial com menu e carregamento de dados |
| view-simples.html | Visão resumida com KPIs e tabela |
| view-detalhada.html | Visão detalhada com seções por status |
| admin.html | Página de administração para colar dados |
| Template_Projetos_v5.xlsx | Planilha modelo para entrada de dados |
| CHANGELOG_BUGS.md | Este arquivo de registro |
| README.md | Documentação do projeto |
