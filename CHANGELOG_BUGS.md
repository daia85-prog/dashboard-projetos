# 📋 Changelog e Histórico de Bugs

## Dashboard de Projetos - Infraestrutura

---

## v6.0 (20/01/2026) - Nova Arquitetura ⭐

### 🚀 Grandes Mudanças
- **Nova estrutura de dados**: Múltiplas linhas de atividades por projeto
- **Importação via arquivo**: Arraste o Excel direto no admin
- **Timeline de atividades**: Modal com visualização detalhada
- **Análise de gargalos**: Top 5 atividades que mais atrasam

### ✅ Novas Funcionalidades
- **Aba "Atividades" na planilha**
  - 20 atividades padrão por projeto
  - Campos: ID, Projeto, Atividade, Status, Responsável
  - Data Início, Data Fim, Dias Duração, Observações
  
- **Admin.html redesenhado**
  - Upload de arquivo via drag & drop
  - Leitura automática de abas "Projetos" e "Atividades"
  - Preview com 3 abas: Projetos, Atividades, Análise
  - Estatísticas de importação
  
- **Modal com Timeline**
  - Barra de progresso visual (verde/amarelo/cinza)
  - Seções: Concluídas, Em Andamento, Pendentes
  - Mostra Data Início → Data Fim
  - Dias de duração por atividade
  
- **Compatibilidade v5**
  - Suporta formato antigo (string "STATUS|DATA|DESC;...")
  - Suporta formato novo (array de objetos)

### 📊 Dados de Teste
- 25 projetos reais extraídos das planilhas
- 500 atividades (25 x 20)
- Bloqueadores e observações reais

---

## v5.5.2 (20/01/2026) - Refinamentos de Nomenclatura

### ✅ Melhorias
- `etapaAtual` padronizado (mantém `etapa` para compatibilidade)
- `observacoes` padronizado no JSON
- Linha de exemplo na planilha
- README.md e CHANGELOG_BUGS.md

---

## v5.5.1 (20/01/2026) - Padronização Core

### ✅ Melhorias
- Função `parseDateBR()` - Converte qualquer formato para dd/mm/aaaa
- Função `cleanBloqueador()` - Remove NaN, -, vazio
- Cálculo automático de "Dias Parado"
- Preview com destaque para dias > 15

### 🐛 Bugs Corrigidos
- Bloqueador mostrava "NaN" quando vazio
- Datas em formato ISO não eram convertidas

---

## v5.5.0 (20/01/2026) - Resumo Executivo + Alert Inteligente

### ✅ Novas Funcionalidades
- Resumo Executivo automático
- Alert Bar inteligente (vermelho/amarelo/verde)
- Ícones nos Cards de Status
- Hierarquia visual melhorada
- Botão "Gerar PDF"

### 🐛 Bugs Corrigidos
- Layout da index.html quebrado → corrigido com CSS grid

---

## v5.4.1 (20/01/2026) - Modal PDF com Opções

### ✅ Novas Funcionalidades
- Modal de PDF com opções de seleção

---

## v5.4.0 (19/01/2026) - Checklist de 20 Atividades

### ✅ Novas Funcionalidades
- Migração de 12 etapas fixas para 20 atividades flexíveis
- Formato estruturado: `STATUS|DATA|DESCRIÇÃO;...`
- Modal com checklist visual

---

## Bugs Conhecidos

### Em Monitoramento
- [ ] Em telas < 320px, alguns elementos podem sobrepor
- [ ] Impressão em Firefox pode ter margens diferentes

### Resolvidos
- [x] v6.0: Compatibilidade com formato v5 de atividades
- [x] v5.5.1: Bloqueador com NaN
- [x] v5.5.0: Layout index.html quebrado

---

## Roadmap Futuro

### v6.1 (Planejado)
- [ ] Filtro por responsável
- [ ] Gráfico de Gantt simplificado
- [ ] Export para Excel das atividades

### v6.2 (Planejado)
- [ ] Notificações de atividades atrasadas
- [ ] Dashboard de responsáveis
- [ ] Comparativo entre projetos

---

## Contato

**Desenvolvido por:** Infraestrutura TI - Invent Corp  
**Última atualização:** 20/01/2026
