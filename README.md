# 📊 Dashboard de Projetos - Infraestrutura

## Versão: v6.0 - Nova Arquitetura

Dashboard executivo para gestão de projetos de infraestrutura com **múltiplas atividades por projeto**.

---

## 🆕 Novidades da v6.0

### Nova Arquitetura de Dados
- **Múltiplas linhas por projeto** para atividades
- Registro de **Data Início** e **Data Fim** por atividade
- **Dias de duração** calculados automaticamente
- **Análise de gargalos**: quais atividades mais atrasam

### Nova Importação
- **Arquivo Excel direto** (arraste ou selecione)
- Lê automaticamente abas "Projetos" e "Atividades"
- Sem copiar/colar manual

### Modal com Timeline
- Barra de progresso visual
- Seções: Concluídas, Em Andamento, Pendentes
- Mostra datas de início → fim
- Dias de duração por atividade

---

## 📁 Arquivos do Sistema

| Arquivo | Descrição |
|---------|-----------|
| `index.html` | Página inicial |
| `view-simples.html` | Dashboard resumido |
| `view-detalhada.html` | Dashboard completo |
| `admin.html` | Importação de planilha Excel |
| `dados.json` | Dados exportados |
| `Template_Projetos_v6.xlsx` | Planilha modelo |

---

## 📋 Estrutura da Planilha v6.0

### Aba "Projetos" (1 linha por projeto)

| Coluna | Campo | Exemplo |
|--------|-------|---------|
| A | Projeto | BETA |
| B | Localização | São Paulo - SP |
| C | Status | Em Andamento |
| D | Situação | Verde / Amarelo / Vermelho |
| E | Progresso | 75 |
| F | PMO Interno | Daiana |
| G | Go Live Original | 15/01/2026 |
| H | Go Live Atual | 28/02/2026 |
| I | Bloqueador | Aguardando cliente |
| J | Última Atualização | 18/01/2026 |
| K | Dias Parado | 2 |
| L | Observações | Texto livre |

### Aba "Atividades" (múltiplas linhas por projeto)

| Coluna | Campo | Exemplo |
|--------|-------|---------|
| A | ID | A0001 |
| B | Projeto | BETA |
| C | Atividade | 01 - KICKOFF INTERNO |
| D | Status | Concluído / Em Andamento / Pendente |
| E | Responsável | Daiana |
| F | Data Início | 10/01/2026 |
| G | Data Fim | 12/01/2026 |
| H | Dias Duração | 2 |
| I | Observações | OK |

---

## 📊 Lista de 20 Atividades Padrão

1. KICKOFF INTERNO
2. Analisar documentos (Masterdata/Cronograma)
3. Análise/Recebimento Layout Elétrico
4. Reportar pontos críticos ao PMO
5. Reunião apresentação dos times
6. Registrar contatos do cliente
7. Enviar doc: Sugestão de Servidores
8. Enviar doc: Solicitação Range IPs
9. Enviar doc: Solicitação Acesso Remoto
10. Acompanhar retorno do cliente
11. Follow-up 7 dias sem resposta
12. Agendar reunião de definição
13. Realizar reunião de definição
14. Documentar acordos com cliente
15. TERMO SEGURANÇA: Coletar assinaturas
16. VALIDAÇÃO ACESSOS: Testar acessos
17. Criar procedimento de acesso
18. Compartilhar com todos os times
19. LEMBRETES: +15d, +30d, +45d
20. Atualizar documentação OneDrive

---

## 🚀 Como Usar

### 1. Abrir Template
Abra `Template_Projetos_v6.xlsx`

### 2. Preencher Projetos
Na aba "Projetos", adicione/edite seus projetos

### 3. Preencher Atividades
Na aba "Atividades", adicione uma linha para cada atividade de cada projeto

### 4. Importar
1. Acesse `admin.html`
2. Arraste o arquivo Excel ou clique para selecionar
3. Verifique o resumo da importação
4. Clique em "Exportar dados.json"

### 5. Publicar
Copie `dados.json` para o mesmo diretório dos HTMLs

---

## 📈 Funcionalidades

### Dashboard
- KPIs: No Prazo, Atraso Médio, Projetos Atualizados, Tempo Médio Parado
- Cards clicáveis por status
- Gráficos de distribuição e bloqueadores
- Filtros por Go-Live, status, situação

### Modal de Projeto
- Timeline de atividades com datas
- Barra de progresso visual
- Seções coloridas por status
- Observações do projeto

### Impressão/PDF
- Filtro atual
- Todos os projetos
- Apenas críticos
- Projetos específicos

### Análise (admin)
- Top 5 atividades que mais atrasam
- Média de dias por atividade
- Impacto (Alto/Médio/Baixo)

---

## 👩‍💻 Desenvolvido por
Infraestrutura TI - Invent Corp

**Versão:** 6.0  
**Data:** Janeiro 2026
