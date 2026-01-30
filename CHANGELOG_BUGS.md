# 📋 CHANGELOG & REGISTRO DE BUGS - Dashboard Projetos Infraestrutura

> **Última atualização:** 29/01/2026  
> **Versão atual:** 6.2.1

---

## v6.2.1 (29/01/2026) - Refinamentos Executivos 🎯

### ✅ Melhorias Pontuais

#### 2.1 Meta no Card Saúde
- Linha de % críticos agora mostra: "12% (meta < 10%)"
- Linha de atraso médio agora mostra: "4 dias (meta < 3)"
- Tira dúvida na reunião sem precisar explicar

#### 2.2 Subtítulo em Decisões Necessárias
- Adicionado: "Projetos críticos com bloqueador, ordenados por tempo parado"
- Explica a lógica de priorização para a diretoria

#### 2.3 PMO Mais Carregado
- Nova linha de destaque: "Mais carregado: Daiana (8 projetos, 3 críticos)"
- Facilita discussão de capacidade e carga

#### 2.4 Alert Bar Diferenciada
- Texto agora detalha tipo de problema: "1 atrasado e 2 parados há 15+ dias"
- Card mostra volume total, alert mostra detalhamento

#### 2.5 Mensagem Go-Live Vazio
- Quando filtro não encontra nada: "Nenhum Go-Live previsto nesta janela. Clique em 'Todos' para ver todas as datas."
- Quando não há Go-Lives: "Verifique se as datas estão preenchidas nos projetos."

#### 2.6 Próxima Ação no Modal
- Nova linha "➡️ Próxima ação:" no resumo executivo
- Usa bloqueador (prefixado com "Resolver:") ou observações
- Foco em ação, não só status

#### 3. Texto "Apenas Críticos" Atualizado
- Descrição agora inclui: "Atrasados, vermelhos, parados 15+ dias ou com bloqueador"
- Alinhado com a lógica real do isCritico()

---

## v6.2 (29/01/2026) - Valor para Diretoria 🚀

### ✅ Novos Recursos

#### 1. KPI "Saúde do Portfólio" (index.html)
Card destacado no topo mostrando:
- Indicador visual: 🟢 Saudável / 🟡 Moderada / 🔴 Crítica
- % de projetos críticos (meta < 10%)
- Atraso médio em dias

**Regras de cor:**
- Verde: < 10% críticos
- Amarelo: 10-25% críticos
- Vermelho: > 25% críticos

#### 2. Seção "Decisões Necessárias" (index.html)
Bloco destacado mostrando até 5 projetos críticos COM bloqueador:
- Nome do projeto
- Descrição do bloqueador
- "Bloqueia há X dias"
- Responsável (PMO)
- Ordenado por dias parado (desc)

#### 3. Distribuição por PMO (view-detalhada.html)
Seção "👥 Distribuição de projetos por PMO interno":
- Gráfico de barras horizontais
- Total de projetos por PMO
- Badge com quantidade de críticos
- Ordenado por quantidade total

#### 4. Botão "🏠 Início" (todas as views)
Adicionado botão de navegação para retornar à página inicial:
- view-simples.html ✅
- view-detalhada.html ✅
- admin.html ✅

#### 5. Rodapé com versão e data (todas as páginas)
Rodapé padronizado exibindo:
Dashboard Projetos Infraestrutura · v6.2 · Atualizado em: DD/MM/AAAA HH:MM

#### 6. Microcopy orientada à ação
- Alert bar: "X projeto(s) atrasado(s) e Y parado(s) há 15+ dias. Clique para ver detalhes."
- Botão "🚨 Ver Críticos" na alert bar do index

#### 7. Card "Projetos Críticos" (index.html) 🆕
Card destacado em vermelho na navegação principal:
- Contagem de projetos críticos em tempo real
- Link direto para view-detalhada.html?filter=criticos
- Destaque visual diferenciado

#### 8. Filtros "Janela de Go-Live" (index.html) 🆕
Botões executivos na seção Próximos Go Lives:
- Todos | Até 30 dias | 30-60 dias | 60-90 dias
- Filtragem dinâmica da timeline

#### 9. Modal com Resumo Executivo (views) 🆕
Bloco resumo no topo do modal de projeto:
- Badges: Status, Situação (cor), Progresso
- Linha resumo: Go-Live (com delta), Dias parado, PMO
- Bloqueador destacado quando existir
- Delta positivo/negativo em relação ao go-live original

#### 10. Suporte a Filtro via URL 🆕
- view-detalhada.html?filter=criticos → ativa filtro automaticamente
- view-simples.html?filter=criticos → ativa filtro automaticamente

---

### 🐛 Bugs Corrigidos

#### BUG #018 - Botão "Voltar/Início" faltando na view-simples
**Problema:** Barra de botões não tinha opção para retornar ao index.html
**Solução:** Adicionado botão "🏠 Início" como primeiro da esquerda

#### BUG #019 - Botão "Voltar/Início" faltando na view-detalhada
**Problema:** Mesmo problema da view-simples
**Solução:** Adicionado botão "🏠 Início" como primeiro da esquerda

#### BUG #020 - "Projetos específicos" não funcionava em PDF/Impressão
**Problema:** Ao marcar checkboxes de projetos específicos, a opção não era automaticamente selecionada, gerando todos os projetos ao invés dos selecionados
**Solução:** Adicionado `onchange="autoSelectSpecificPrint/Pdf()"` nos checkboxes que automaticamente seleciona a opção "specific" quando qualquer checkbox é marcado

#### BUG #021 - Checkboxes dos projetos não apareciam 🆕
**Problema:** CSS `.print-option input { display: none; }` escondia TODOS os inputs, incluindo os checkboxes de seleção de projetos
**Solução:** Alterado para `.print-option input[type="radio"] { display: none; }` para esconder apenas os radio buttons

---

## v6.1.1 (29/01/2026) - Correção de Modais

### 🐛 Bugs Corrigidos

#### BUG #015 - Modal de Impressão sem opções de filtro
**Problema:** Diálogo de impressão abria direto sem opções de filtro
**Solução:** Restaurado modal com 4 opções: Filtro atual, Todos, Críticos, Específicos

#### BUG #016 - Modal de PDF sem opções de filtro
**Problema:** PDF gerava direto sem opções de filtro
**Solução:** Restaurado modal idêntico ao de impressão

#### BUG #017 - Botão "Imprimir" sumiu do modal de detalhes
**Problema:** Modal de projeto não tinha mais o botão de imprimir individual
**Solução:** Restaurado botão "🖨️ Imprimir" no header do modal

---

## v6.0 (20/01/2026) - Arquitetura Dual

### ✅ Novas Funcionalidades
- Separação em duas tabelas: Projetos e Atividades
- 20 atividades padronizadas por projeto
- Timeline visual no modal de detalhes
- Admin com drag-and-drop de Excel
- KPIs com tooltips explicativos
- Filtro "🚨 Apenas Críticos"

---

## 📁 ARQUIVOS DO PROJETO

| # | Arquivo | Descrição |
|---|---------|-----------|
| 1 | admin.html | Administração - upload Excel |
| 2 | dados.json | Dados JSON |
| 3 | index.html | Página inicial |
| 4 | Template_Projetos_v6.xlsx | Planilha modelo |
| 5 | view-detalhada.html | Dashboard detalhado |
| 6 | view-simples.html | Dashboard resumido |
| 7 | CHANGELOG_BUGS.md | Este arquivo |
| 8 | README.md | Documentação |

---

## 🎯 PROJETO CRÍTICO = Atrasado OU Vermelho OU Parado≥15 OU Bloqueador

## 📊 SAÚDE: Verde(<10%) | Amarelo(10-25%) | Vermelho(>25%)

---

**Contato:** Infraestrutura TI - Invent Corp | PMO: Daiana
