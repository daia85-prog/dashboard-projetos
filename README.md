# 📊 Dashboard de Status de Projetos - Infraestrutura TI

> **Versão:** 5.3.2  
> **Última atualização:** 18/01/2026  
> **Desenvolvido para:** Douglas (Gestor) - Invent Corp  
> **PMO:** Daiana

---

## 📁 ESTRUTURA DE ARQUIVOS

| Arquivo | Descrição |
|---------|-----------|
| `index.html` | Página inicial - menu, carregamento de dados, próximos go-lives |
| `view-simples.html` | Visão resumida - KPIs, cards, gráficos, tabela única |
| `view-detalhada.html` | Visão detalhada - seções separadas por status |
| `admin.html` | Administração - colar dados da planilha |
| `Template_Projetos_v5.xlsx` | Planilha modelo (template vazio) |
| `Template_Projetos_v5_TestData.xlsx` | Planilha com 30 projetos fictícios para teste |
| `CHANGELOG_BUGS.md` | Registro de bugs e correções |
| `README.md` | Este arquivo - documentação completa |

---

## 📋 CAMPOS DA PLANILHA (18 colunas)

| # | Coluna | Obrigatório | Descrição |
|---|--------|-------------|-----------|
| A | **Projeto** | ✅ Sim | Nome do projeto |
| B | **Localização** | Não | Cidade/Estado do CD (ex: São Paulo - SP) |
| C | **Status** | ✅ Sim | Em Andamento, Concluído, Atrasado, Aguardando Cliente, Não Iniciado |
| D | **Situação** | ✅ Sim | Verde, Amarelo, Vermelho, Cinza (RAG) |
| E | **Progresso** | Não | Percentual (ex: 70%) |
| F | **Etapa Atual** | Não | Fase atual do projeto |
| G | **PMO Interno** | Não | Responsável interno |
| H | **Go Live Original** | Não | Data prevista original (dd/mm/aaaa) |
| I | **Go Live Atual** | Não | Data prevista atualizada (dd/mm/aaaa) |
| J | **Bloqueador** | Não | Impedimento atual |
| K | **Última Atualização** | Não | Data da última atualização |
| L | **Dias Parado** | Não | Quantos dias sem atualização |
| M | **Observações** | Não | Anotações gerais do projeto |
| N | **Etapa 1 - Kick-off** | Não | Data de conclusão do kick-off |
| O | **Etapa 2 - Levantamento** | Não | Data de conclusão do levantamento |
| P | **Etapa 3 - Desenvolvimento** | Não | Data de conclusão do desenvolvimento |
| Q | **Etapa 4 - Homologação** | Não | Data de conclusão da homologação |
| R | **Etapa 5 - Go Live** | Não | Data de realização do go-live |

---

## 🎯 REGRAS DE NEGÓCIO

### Status (coluna C)
- **Em Andamento** - Projeto em execução
- **Concluído** - Projeto finalizado
- **Atrasado** - Passou da data de go-live
- **Aguardando Cliente** - Bloqueado por dependência do cliente
- **Não Iniciado** - Ainda não começou

### Situação/RAG (coluna D)
- **Verde** 🟢 - No prazo, sem problemas
- **Amarelo** 🟡 - Atenção, risco moderado
- **Vermelho** 🔴 - Crítico, risco alto
- **Cinza** ⚫ - Concluído ou não iniciado

### Projeto Crítico (alerta automático)
Um projeto é considerado **CRÍTICO** se atender QUALQUER uma das condições:
1. Status = "Atrasado"
2. Situação = "Vermelho"
3. Dias Parado > 15
4. Tem bloqueador preenchido

---

## 📊 KPIs CALCULADOS

| KPI | Fórmula | Descrição |
|-----|---------|-----------|
| **% No Prazo** | (projetos com GoLive Atual ≤ GoLive Original) / total com data | Taxa de entregas no prazo |
| **Atraso Médio** | média(GoLive Atual - GoLive Original) em dias | Média de dias de atraso |
| **Taxa Atualização** | projetos com dias ≤ 7 / total não concluídos | % de projetos atualizados na semana |
| **Aging Médio** | média(Dias Parado) | Tempo médio sem atualização |

---

## 🖨️ FUNCIONALIDADES DE IMPRESSÃO

### Opções de impressão:
1. **Filtro atual** - Imprime apenas projetos visíveis na tela
2. **Todos os projetos** - Imprime todos sem filtros
3. **Apenas críticos** - Imprime só os projetos críticos
4. **Projetos específicos** - Seleciona manualmente com checkboxes

### Melhorias implementadas (v5.3.2):
- 🔍 **Campo de busca** - Digitar para filtrar projetos na lista
- 🔤 **Ordem alfabética** - Lista de projetos ordenada A-Z
- 📅 **Histórico de etapas** - Modal mostra datas das etapas concluídas
- 📝 **Observações** - Modal exibe campo de observações

---

## 🔧 FILTROS DISPONÍVEIS

| Filtro | Opções |
|--------|--------|
| **Busca** | Texto livre (nome do projeto) |
| **Status** | Em Andamento, Concluído, Atrasado, Aguardando, Não Iniciado |
| **Situação** | Verde, Amarelo, Vermelho |
| **Go Live** | Próximos 7 dias, Próximos 30 dias, Atrasados |
| **Parados** | Mais de 7 dias, Mais de 15 dias |
| **PMO** | Lista dinâmica dos PMOs cadastrados |

---

## 📅 PRÓXIMOS GO-LIVES (index.html)

Exibe timeline com os próximos go-lives:
- 🔴 **HOJE!** - Go-live é hoje
- 🟡 **em X dias** - Go-live nos próximos 7 dias
- 🟢 **em X dias** - Go-live entre 8-30 dias
- ⚪ **em X dias** - Go-live após 30 dias

---

## 🐛 HISTÓRICO DE CORREÇÕES

### v5.3.2 (18/01/2026)
- ✅ #012 - Busca de projetos na impressão
- ✅ #013 - Lista ordenada alfabeticamente
- ✅ #014 - Histórico de etapas no modal
- ✅ #015 - Observações no modal

### v5.3.1 (18/01/2026)
- ✅ #008 - KPI "NaN dias" corrigido (validação de datas)
- ✅ #009 - Filtros não zeravam cards (usar filteredProjects)
- ✅ #010 - Data "hoje/ontem" incorreta (comparar só dia)
- ✅ #011 - Próximos Go Lives redesenhado (timeline)

### v5.3 (17/01/2026)
- ✅ Checkbox para seleção de projetos na impressão
- ✅ Labels simplificados nos KPIs
- ✅ Filtro de Go-Live

---

## 💾 COMO USAR

### Passo a passo:
1. Preencher a planilha `Template_Projetos_v5.xlsx`
2. Selecionar e copiar os dados (SEM o cabeçalho)
3. Abrir `index.html` no navegador
4. Clicar em "⚙️ Carregar Dados"
5. Colar os dados e clicar "Carregar"
6. Navegar pelas visualizações

### Atualização de dados:
- Os dados ficam salvos no localStorage do navegador
- Para atualizar: repetir o processo de colar novos dados
- Para limpar: usar botão "Limpar Dados" no admin

---

## 🏗️ ARQUITETURA TÉCNICA

### Tecnologias:
- HTML5 + CSS3 (inline, sem dependências externas)
- JavaScript vanilla (sem frameworks)
- LocalStorage para persistência
- Responsivo (desktop/tablet)

### Funções principais:
- `loadData()` - Carrega dados do localStorage
- `parseData(text)` - Converte texto colado em objetos
- `updateDashboard()` - Atualiza KPIs e cards (usa filteredProjects)
- `applyFilters()` - Aplica filtros selecionados
- `renderTable()` / `renderSections()` - Renderiza tabelas
- `openModal(name)` - Abre detalhes do projeto (com etapas e obs)
- `executePrint()` - Prepara e executa impressão
- `filterProjectCheckboxes()` - Filtra lista de projetos por busca
- `populateProjectsCheckboxes()` - Preenche lista ordenada A-Z

---

## 📞 MANUTENÇÃO FUTURA

### Para adicionar novo campo:
1. Adicionar coluna na planilha (Template)
2. Atualizar `colMap` no `admin.html`
3. Adicionar campo no `data.push()` do `admin.html`
4. Exibir campo nos HTMLs (tabela/modal)

### Para adicionar novo filtro:
1. Adicionar `<select>` na seção de filtros
2. Capturar valor em `applyFilters()`
3. Adicionar lógica de filtro no `filter()`

### Para adicionar novo KPI:
1. Adicionar card HTML na seção `.kpis-section`
2. Calcular valor em `updateDashboard()`
3. Atualizar `getElementById` com o valor

---

## 🔗 HOSPEDAGEM

### Opções testadas:
- ✅ **GitHub Pages** - Funciona 100% (recomendado para testes)
- ✅ **Abrir local** - Funciona no navegador
- ⚠️ **SharePoint** - Funciona, pode ter limitações de JS
- ✅ **Azure Static Web Apps** - Melhor opção corporativa

---

## 📝 NOTAS IMPORTANTES

1. **Datas** devem estar no formato `dd/mm/aaaa`
2. **Progresso** pode ter ou não o símbolo `%`
3. **Campos vazios** são tratados como `-`
4. **Ordem das colunas** na planilha é flexível (mapeamento por nome)
5. **localStorage** tem limite de ~5MB (suficiente para 1000+ projetos)
6. **Sempre usar filteredProjects** nos cálculos de cards/KPIs (não projects)
7. **Validar datas** com isNaN() antes de cálculos para evitar NaN

---

> **Desenvolvido com 💜 para facilitar a gestão de projetos de infraestrutura**
