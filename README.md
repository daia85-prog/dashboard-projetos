# 📊 Dashboard de Status de Projetos - Infraestrutura TI

> **Versão:** 6.1.1  
> **Última atualização:** 29/01/2026  
> **Desenvolvido para:** Douglas (Gestor) - Invent Corp  
> **PMO:** Daiana

---

## 📁 ESTRUTURA DE ARQUIVOS

| Arquivo | Descrição |
|---------|-----------|
| `index.html` | Página inicial - KPIs resumidos, navegação |
| `view-simples.html` | Dashboard resumido - tabela única, gráficos |
| `view-detalhada.html` | Dashboard completo - seções por status |
| `admin.html` | Administração - importar Excel via drag-and-drop |
| `Template_Projetos_v6.xlsx` | Planilha modelo com 2 abas (Projetos + Atividades) |
| `dados.json` | Dados em JSON (gerado pelo admin) |
| `CHANGELOG_BUGS.md` | Registro de bugs e correções |
| `README.md` | Este arquivo - documentação completa |

---

## 📋 ESTRUTURA DA PLANILHA v6

### Aba "Projetos" (10 colunas)

| # | Coluna | Obrigatório | Descrição |
|---|--------|-------------|-----------|
| A | **Projeto** | ✅ Sim | Nome do projeto |
| B | **Localização** | Não | Cidade/Estado (ex: São Paulo - SP) |
| C | **Status** | ✅ Sim | Em Andamento, Concluído, Atrasado, Aguardando, Não Iniciado |
| D | **Situação** | ✅ Sim | Verde, Amarelo, Vermelho, Cinza |
| E | **PMO Interno** | Não | Responsável interno |
| F | **Go Live Original** | Não | Data prevista original |
| G | **Go Live Atual** | Não | Data prevista atualizada |
| H | **Bloqueador** | Não | Impedimento atual |
| I | **Observações** | Não | Anotações gerais |

### Aba "Atividades" (6 colunas)

| # | Coluna | Descrição |
|---|--------|-----------|
| A | **Projeto** | Nome do projeto (deve existir na aba Projetos) |
| B | **Atividade** | Nome da atividade (ex: 01 - KICKOFF INTERNO) |
| C | **Status** | Concluída, Em Andamento, Pendente |
| D | **Data Início** | Data de início |
| E | **Data Conclusão** | Data de conclusão |
| F | **Dias** | Duração em dias |

### 20 Atividades Padrão

1. KICKOFF INTERNO
2. Analisar documentos recebidos do cliente
3. Solicitar acessos necessários
4. Agendar e realizar Kick-off Externo
5. Criar lista de CIs
6. Encaminhar equipamentos de Infraestrutura
7. Criar/Alterar Plano de Implantação
8. Acompanhar Desenvolvimento pela Fábrica
9. Criar lista técnica para o cliente
10. Acompanhar GO/NO-GO
11. Acompanhar Testes Funcionais
12. Acompanhar Cutover/Go-Live
13. Criar lista de IPs e VLANs
14. Migrar servidores e serviços
15. Acompanhar Hypercare
16. Preparar ambiente (VMs, rede, servidores)
17. Instalar e configurar banco de dados
18. Atualizar WMS Interno
19. Atualizar documentação OneDrive
20. Finalização/Encerramento

---

## 🎯 REGRAS DE NEGÓCIO

### Status (coluna C - Projetos)
- **Em Andamento** - Projeto em execução ativa
- **Concluído** - Projeto finalizado com sucesso
- **Atrasado** - Passou da data de go-live prevista
- **Aguardando** - Bloqueado, aguardando cliente/terceiros
- **Não Iniciado** - Planejado mas ainda não iniciou

### Situação/RAG (coluna D - Projetos)
- 🟢 **Verde** - No prazo, sem problemas
- 🟡 **Amarelo** - Atenção, risco moderado
- 🔴 **Vermelho** - Crítico, risco alto
- ⚫ **Cinza** - Concluído ou não iniciado

### Projeto Crítico (alerta automático)
Um projeto é **CRÍTICO** se atender QUALQUER condição:
1. ⏰ Status = "Atrasado"
2. 🔴 Situação = "Vermelho"
3. 📅 Dias Parado ≥ 15 dias sem atualização
4. 🚫 Possui Bloqueador preenchido

---

## 🖨️ FUNCIONALIDADES DE IMPRESSÃO/PDF

### Modal de Impressão (🖨️ Imprimir)
Abre modal com 4 opções:
1. **Filtro atual** - Imprime apenas projetos visíveis na tela
2. **Todos os projetos** - Imprime todos os projetos
3. **Apenas críticos** - Imprime apenas projetos críticos
4. **Projetos específicos** - Seleciona por checkboxes

### Modal de PDF (📄 Gerar PDF)
Mesmas 4 opções do modal de impressão.
Gera arquivo PDF com:
- Cabeçalho com data/hora
- Cards de resumo (Total, Concluídos, Em Andamento, Críticos)
- Tabela detalhada dos projetos selecionados

### Botão Imprimir no Modal do Projeto
Ao clicar em um projeto na tabela:
1. Abre modal de detalhes
2. Botão "🖨️ Imprimir" no canto superior direito
3. Gera relatório formatado apenas daquele projeto
4. Inclui: dados do projeto + timeline de atividades

---

## 📊 KPIs EXIBIDOS

| KPI | Descrição | Fórmula |
|-----|-----------|---------|
| **No Prazo** | % de projetos dentro do prazo | (Projetos com Go Live ≥ hoje) / Total |
| **Atraso Médio** | Média de dias de atraso | Σ(GoLive Atual - GoLive Original) / n |
| **Projetos Atualizados** | % com atualização recente | (Projetos atualizados ≤ 7 dias) / Total |
| **Tempo Médio Parado** | Média de dias sem atualização | Σ(Dias Parado) / n |

---

## 🔧 COMO USAR

### Fluxo de Atualização

1. **Atualize a planilha** Excel com os dados dos projetos
2. Abra **admin.html** no navegador
3. **Arraste o arquivo Excel** para a área indicada
4. Clique em **"Exportar dados.json"**
5. **Substitua o dados.json** no repositório
6. Faça commit e push para o GitHub
7. Aguarde atualização do GitHub Pages

### Acesso às Views

- **index.html** → Página inicial com resumo
- **view-simples.html** → Tabela única com filtros
- **view-detalhada.html** → Seções separadas por status

---

## 🐛 BUGS CONHECIDOS

Ver arquivo `CHANGELOG_BUGS.md` para histórico completo.

### Resolvidos em v6.1.1:
- [x] Modal de impressão sem opções de filtro
- [x] Modal de PDF sem opções de filtro
- [x] Botão imprimir sumiu do modal de detalhes

---

## 📞 Contato

**Desenvolvido por:** Infraestrutura TI - Invent Corp  
**PMO:** Daiana  
**Versão:** 6.1.1  
**Última atualização:** 29/01/2026
