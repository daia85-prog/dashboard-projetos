# 📋 Changelog e Histórico de Bugs

## Dashboard de Projetos - Infraestrutura

---

## v5.5.2 (20/01/2026) - Refinamentos de Nomenclatura

### ✅ Melhorias
- **`etapaAtual` padronizado** - Campo renomeado para consistência (mantém `etapa` para compatibilidade)
- **`observacoes` padronizado** - Campo sempre com este nome no JSON
- **Linha de exemplo na planilha** - Template com dados fictícios para referência
- **README.md** - Documentação técnica completa
- **CHANGELOG_BUGS.md** - Este arquivo de histórico

---

## v5.5.1 (20/01/2026) - Padronização Core

### ✅ Melhorias
- **Função `parseDateBR()`** - Converte qualquer formato de data para dd/mm/aaaa
  - Aceita: números Excel, aaaa-mm-dd, dd-mm-aaaa, dd/mm/aaaa
  - Sempre retorna: dd/mm/aaaa
- **Função `cleanBloqueador()`** - Remove valores inválidos
  - Trata: NaN, -, vazio, undefined, null
  - Resultado: texto limpo ou vazio
- **Cálculo automático de "Dias Parado"**
  - Se coluna L vazia mas coluna K tem data → calcula automaticamente
  - Validação mostra quantos foram calculados
- **Preview com destaque** - Dias > 15 aparecem em laranja na pré-visualização

### 🐛 Bugs Corrigidos
- Bloqueador mostrava "NaN" quando vazio
- Datas em formato ISO não eram convertidas

---

## v5.5.0 (20/01/2026) - Resumo Executivo + Alert Inteligente

### ✅ Novas Funcionalidades
- **Resumo Executivo** - Frase automática abaixo dos KPIs
  - "30 projetos em carteira: 5 concluídos, 13 em andamento. Foco: 5 atrasados..."
- **Alert Bar Inteligente**
  - 🔴 Vermelho: projetos atrasados ou parados 15+ dias
  - 🟡 Amarelo: projetos que requerem atenção
  - 🟢 Verde: tudo em dia
- **Ícones nos Cards de Status**
  - 📊 Total | ✅ Concluídos | ⏳ Em Andamento | 🔴 Atrasados | ⏸️ Aguardando | 🚨 Críticos
- **Hierarquia Visual Melhorada** - Números maiores, labels menores
- **Botão "Gerar PDF"** em vez de só "PDF"

### 🐛 Bugs Corrigidos
- Layout da index.html quebrado (itens empilhados) → corrigido com CSS grid

---

## v5.4.1 (20/01/2026) - Modal PDF com Opções

### ✅ Novas Funcionalidades
- **Modal de PDF** - Mesmas opções que impressão:
  - Filtro atual
  - Todos os projetos
  - Apenas críticos
  - Projetos específicos

### 🐛 Bugs Corrigidos
- PDF gerava direto sem perguntar opções

---

## v5.4.0 (19/01/2026) - Checklist de 20 Atividades

### ✅ Novas Funcionalidades
- **Migração de 12 etapas fixas para 20 atividades flexíveis**
- **Formato estruturado**: `STATUS|DATA|DESCRIÇÃO;...`
- **Modal com checklist visual**:
  - Barra de progresso
  - Seção de concluídas (verde)
  - Seção de pendentes (amarelo)
- **PDF com atividades** - Grid 2 colunas com descrição e data

### ⚠️ Breaking Change
- Planilha agora usa coluna N única (Atividades) em vez de colunas N-Y (Etapa 1-12)

---

## v5.3.3 (19/01/2026) - PDF Export

### ✅ Novas Funcionalidades
- **Exportação para PDF** via html2pdf
- **Dados de teste** - 30 projetos fictícios para demonstração

---

## v5.3.2 (18/01/2026) - Correção de Filtros

### 🐛 Bugs Corrigidos
- **isCritico()** - Removido "has blocker" da lógica
- **Filtro de status** - Cards não zeravam ao filtrar
- **Parsing do admin** - Correção na leitura de colunas

---

## v5.3.0 (17/01/2026) - KPIs Simplificados

### ✅ Novas Funcionalidades
- **4 KPIs principais**: No Prazo, Atraso Médio, Projetos Atualizados, Tempo Médio Parado
- **Filtro por Go-Live**: Este mês, 30/60/90 dias, Atrasados
- **Impressão por projetos específicos** - Checkbox para selecionar

---

## Bugs Conhecidos

### Em Monitoramento
- [ ] Em telas muito pequenas (<320px), alguns elementos podem sobrepor
- [ ] Impressão em Firefox pode ter margens diferentes

### Resolvidos Recentemente
- [x] v5.5.1: Bloqueador com NaN
- [x] v5.5.0: Layout index.html quebrado
- [x] v5.4.1: PDF sem modal de opções
- [x] v5.3.2: Filtro de críticos incorreto

---

## Contato

**Desenvolvido por:** Infraestrutura TI - Invent Corp  
**Última atualização:** 20/01/2026
