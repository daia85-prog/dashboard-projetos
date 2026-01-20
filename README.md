# 📊 Dashboard de Projetos - Infraestrutura

## Versão Atual: v5.5.2

Dashboard executivo para gestão de projetos de infraestrutura. Desenvolvido para visualização rápida de KPIs, status de projetos e tomada de decisão.

---

## 📁 Arquivos do Sistema

| Arquivo | Descrição |
|---------|-----------|
| `index.html` | Página inicial com seleção de visões |
| `view-simples.html` | Dashboard resumido com KPIs e gráficos |
| `view-detalhada.html` | Dashboard completo segmentado por status |
| `admin.html` | Área administrativa para importar dados |
| `dados.json` | Arquivo de dados (gerado pelo admin) |
| `Template_Projetos_v5.xlsx` | Planilha modelo para importação |

---

## 📋 Estrutura de Campos

### Colunas da Planilha (A-N)

| Coluna | Campo | Tipo | Exemplo |
|--------|-------|------|---------|
| A | Projeto | Texto | "ALPHA - Automação CD" |
| B | Localização | Texto | "São Paulo - SP" |
| C | Status | Texto | "Em Andamento" |
| D | Situação/RAG | Texto | "Verde" / "Amarelo" / "Vermelho" |
| E | Progresso | Número | 75 ou 75% |
| F | Etapa Atual | Texto | "Desenvolvimento" |
| G | PMO Interno | Texto | "Daiana" |
| H | Go Live Original | Data | 15/03/2025 |
| I | Go Live Atual | Data | 20/03/2025 |
| J | Bloqueador | Texto | "Aguardando retorno do cliente" |
| K | Última Atualização | Data | 18/01/2026 |
| L | Dias Sem Atualização | Número | 5 (calculado auto se vazio) |
| M | Observações | Texto | "Reunião agendada para sexta" |
| N | Atividades | Texto | "C\|14/10/2025\|01 - KICKOFF;P\|\|02 - Análise" |

### Valores Aceitos para Status
- `Em Andamento`
- `Concluído`
- `Atrasado`
- `Aguardando Cliente`
- `Não Iniciado`

### Valores Aceitos para Situação/RAG
- `Verde` - Projeto no prazo
- `Amarelo` - Atenção necessária
- `Vermelho` - Projeto crítico
- `Cinza` - Sem definição

---

## 🔧 Regras de Negócio

### Projeto Crítico (isCritico)
Um projeto é considerado **crítico** se atender a QUALQUER uma das condições:
- Situação/RAG = "Vermelho"
- Status = "Atrasado"
- Dias sem atualização > 15 (e não concluído)

### Cálculo Automático de "Dias Parado"
Se o campo "Dias Sem Atualização" (coluna L) estiver vazio, mas houver data em "Última Atualização" (coluna K), o sistema calcula automaticamente a diferença em dias.

### Tratamento de Bloqueador
O campo bloqueador é limpo automaticamente:
- Valores `NaN`, `-`, vazio, `undefined`, `null` são convertidos para vazio
- Apenas bloqueadores com texto válido são exibidos

### Formato de Datas
Todas as datas são padronizadas para `dd/mm/aaaa`:
- Aceita: `15/03/2025`, `2025-03-15`, `15-03-2025`, números seriais do Excel
- Saída sempre: `15/03/2025`

---

## 📊 KPIs do Dashboard

| KPI | Descrição | Fórmula |
|-----|-----------|---------|
| No Prazo | % projetos com Go Live no prazo | Go Live Atual ≤ Go Live Original |
| Atraso Médio | Média de dias de atraso | (Go Live Atual - Go Live Original) / n |
| Projetos Atualizados | % atualizados nos últimos 7 dias | Dias sem atualização ≤ 7 |
| Tempo Médio Parado | Média de dias sem atualização | Soma(diasSemAtual) / n |

---

## 📋 Checklist de Atividades (20 itens)

O campo Atividades (coluna N) usa formato estruturado:
```
STATUS|DATA|DESCRIÇÃO;STATUS|DATA|DESCRIÇÃO;...
```

**STATUS:**
- `C` = Concluído
- `P` = Pendente

**Exemplo:**
```
C|14/10/2025|01 - KICKOFF INTERNO;C|15/10/2025|02 - Analisar documentos;P||03 - Layout Elétrico
```

### Lista Padrão de Atividades
1. KICKOFF INTERNO - Gestor
2. Analisar documentos (Masterdata + Cronograma + Gravação)
3. Análise/Recebimento Layout Elétrico
4. Reportar pontos críticos ao PMO/Gestor
5. Participar reunião de apresentação dos times
6. Registrar TODOS os contatos do cliente
7. Enviar documento: Sugestão de Servidores
8. Enviar documento: Solicitação Range IPs
9. Enviar documento: Solicitação Acesso Remoto
10. Acompanhar retorno do cliente diariamente
11. Follow-up após 7 dias se sem resposta
12. Agendar reunião de definição
13. Realizar reunião de definição
14. Documentar acordos/definições com o cliente
15. TERMO DE SEGURANÇA: Coletar assinaturas
16. VALIDAÇÃO DE ACESSOS: Testar acessos
17. Criar procedimento de acesso
18. Compartilhar com todos os times
19. LEMBRETES: 1 (+15 dias) 2 (+30 dias) 3 FINAL (+45 dias)
20. Atualizar documentação no OneDrive

---

## 🚀 Como Usar

### 1. Preparar Dados
1. Abra `Template_Projetos_v5.xlsx`
2. Preencha os dados dos projetos (linha 2 tem exemplo)
3. **Apague a linha de exemplo antes de usar!**

### 2. Importar no Dashboard
1. Acesse `admin.html`
2. Selecione os dados na planilha (Ctrl+A)
3. Copie (Ctrl+C)
4. Cole no campo de texto
5. Clique em "Carregar e Validar"
6. Exporte o `dados.json`

### 3. Publicar
1. Faça upload do `dados.json` no mesmo diretório dos HTMLs
2. Acesse `index.html` no navegador

---

## 📤 Exportações

### Imprimir
- Filtro atual (projetos visíveis)
- Todos os projetos
- Apenas críticos
- Projetos específicos (seleção por checkbox)

### Gerar PDF
- Mesmas opções de impressão
- Arquivo baixado: `Relatorio_Projetos_Infraestrutura_DD-MM-AAAA.pdf`

---

## 📝 Changelog

Ver `CHANGELOG_BUGS.md` para histórico completo de versões.

---

## 👩‍💻 Desenvolvido por
Infraestrutura TI - Invent Corp

**Última atualização:** Janeiro 2026
