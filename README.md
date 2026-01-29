# 📊 Dashboard de Status de Projetos - Infraestrutura TI

> **Versão:** 6.2  
> **Última atualização:** 29/01/2026  
> **Desenvolvido para:** Douglas (Gestor) - Invent Corp  
> **PMO:** Daiana

---

## 📁 ESTRUTURA DE ARQUIVOS

| Arquivo | Descrição |
|---------|-----------|
| index.html | Página inicial - KPIs, Saúde do Portfólio, Decisões, navegação |
| view-simples.html | Dashboard resumido - tabela única, gráficos, filtros |
| view-detalhada.html | Dashboard completo - seções por status, gráfico PMO |
| admin.html | Administração - importar Excel via drag-and-drop |
| Template_Projetos_v6.xlsx | Planilha modelo com 2 abas (Projetos + Atividades) |
| dados.json | Dados em JSON (gerado pelo admin) |
| CHANGELOG_BUGS.md | Registro de bugs e correções |
| README.md | Este arquivo - documentação completa |

---

## 📋 ESTRUTURA DA PLANILHA v6

### Aba "Projetos" (9 colunas)

| Coluna | Obrigatório | Descrição |
|--------|-------------|-----------|
| Projeto | ✅ Sim | Nome do projeto |
| Localização | Não | Cidade/Estado (ex: São Paulo - SP) |
| Status | ✅ Sim | Em Andamento, Concluído, Atrasado, Aguardando, Não Iniciado |
| Situação | ✅ Sim | Verde, Amarelo, Vermelho, Cinza |
| PMO Interno | Não | Responsável interno |
| Go Live Original | Não | Data prevista original (DD/MM/AAAA) |
| Go Live Atual | Não | Data prevista atualizada (DD/MM/AAAA) |
| Bloqueador | Não | Impedimento atual |
| Observações | Não | Anotações gerais |

### Aba "Atividades" (6 colunas)

| Coluna | Descrição |
|--------|-----------|
| Projeto | Nome do projeto (deve existir na aba Projetos) |
| Atividade | Nome da atividade |
| Status | Concluída, Em Andamento, Pendente |
| Data Início | Data de início (DD/MM/AAAA) |
| Data Conclusão | Data de conclusão (DD/MM/AAAA) |
| Dias | Duração em dias |

---

## 🎯 REGRAS DE NEGÓCIO

### Status do Projeto
- **Em Andamento** - Projeto em execução ativa
- **Concluído** - Projeto finalizado com sucesso
- **Atrasado** - Passou da data de go-live prevista
- **Aguardando** - Bloqueado, aguardando cliente/terceiros
- **Não Iniciado** - Planejado mas ainda não iniciou

### Situação/RAG
- 🟢 **Verde** - No prazo, sem problemas
- 🟡 **Amarelo** - Atenção, risco moderado
- 🔴 **Vermelho** - Crítico, risco alto
- ⚫ **Cinza** - Concluído ou não iniciado

### Projeto Crítico (alerta automático)
Um projeto é **CRÍTICO** se atender QUALQUER condição:
1. Status = "Atrasado"
2. Situação = "Vermelho"
3. Dias Parado ≥ 15
4. Possui Bloqueador preenchido

### Saúde do Portfólio
| Status | Condição |
|--------|----------|
| 🟢 Saudável | < 10% projetos críticos |
| 🟡 Moderada | 10-25% projetos críticos |
| 🔴 Crítica | > 25% projetos críticos |

---

## 📊 KPIs EXIBIDOS

| KPI | Descrição |
|-----|-----------|
| No Prazo | % de projetos com Go Live Atual ≤ Original |
| Atraso Médio | Média de dias de atraso nos go-lives |
| Projetos Atualizados | % atualizados nos últimos 7 dias |
| Tempo Médio Parado | Média de dias sem atualização |

---

## 🆕 FUNCIONALIDADES v6.2

### Página Inicial (index.html)
- **Saúde do Portfólio**: Semáforo global indicando saúde geral
- **Decisões Necessárias**: Projetos críticos com bloqueador
- **Próximos Go Lives**: Timeline dos próximos 5 go-lives
- **Cards de navegação**: Acesso rápido às views

### Visão Resumida (view-simples.html)
- KPIs com tooltips explicativos
- Filtros completos (status, situação, PMO, dias parado, go-live)
- Checkbox "Apenas Críticos"
- Modal de impressão com opções de filtro
- Modal de PDF com opções de filtro
- Botão imprimir dentro do modal de projeto

### Visão Detalhada (view-detalhada.html)
- **Gráfico de Distribuição por PMO** (novo!)
- Seções organizadas por status
- Modal de projeto com timeline de atividades
- Mesmas funcionalidades de impressão/PDF

### Administração (admin.html)
- Upload de Excel via drag-and-drop
- Cálculo automático de progresso
- Cálculo automático de dias parado
- Export de dados.json

---

## 🔧 COMO USAR

### Fluxo de Atualização

1. Atualize a planilha Excel com os dados dos projetos
2. Abra admin.html no navegador
3. Arraste o arquivo Excel para a área indicada
4. Clique em "Exportar dados.json"
5. Substitua o dados.json no repositório GitHub
6. Faça commit e push
7. Aguarde atualização do GitHub Pages

### Acesso às Views

- **index.html** → Página inicial com resumo executivo
- **view-simples.html** → Tabela única com filtros
- **view-detalhada.html** → Seções separadas + gráfico PMO

---

## 🖨️ IMPRESSÃO E PDF

### Opções disponíveis:
1. **Filtro atual** - Imprime apenas projetos visíveis na tela
2. **Todos os projetos** - Imprime todos os projetos
3. **Apenas críticos** - Imprime apenas projetos críticos
4. **Projetos específicos** - Seleciona por checkboxes com busca

### Imprimir projeto individual:
1. Clique em um projeto para abrir o modal
2. Clique no botão "🖨️ Imprimir" no canto superior direito
3. Gera relatório formatado com dados + timeline de atividades

---

## 📞 Contato

**Desenvolvido por:** Infraestrutura TI - Invent Corp  
**PMO:** Daiana  
**Versão:** 6.2  
**Última atualização:** 29/01/2026
