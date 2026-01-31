# Dashboard PMO v7.0 - Visão Executiva com Macro Etapas

## 🆕 O QUE MUDOU NA v7.0

### Nova Funcionalidade: Toggle Visão Executiva / Visão Completa

**Visão Executiva (Macro)** 🎯
- Agrupa atividades por 8 macro etapas estratégicas
- Mostra % de conclusão de cada macro
- Ideal para apresentações à diretoria
- Cards visuais com cores (verde/amarelo/vermelho)
- Lista os projetos envolvidos em cada macro

**Visão Completa (Detalhes)** 📋
- Dashboard tradicional com cards de projetos
- Visão operacional completa
- Mesma interface da v6.2.1

### Alteração no Excel

**NOVA COLUNA F: "Macro Etapa"**

A aba "ATIVIDADES" agora tem 6 colunas:
- A: Projeto
- B: Atividade
- C: Data Início
- D: Data Fim
- E: Status
- **F: Macro Etapa** ⬅️ NOVA!

---

## 📋 AS 8 MACRO ETAPAS

Use EXATAMENTE estes textos na coluna F:

```
1. Iniciação
2. Planejamento & Documentação
3. Provisionamento de Recursos
4. Implementação
5. Testes & Homologação
6. Deploy em Produção
7. Estabilização
8. Encerramento
```

### Mapeamento das Atividades V5 → Macros

| Sua atividade atual | Macro Etapa (coluna F) |
|---------------------|------------------------|
| KICKOFF INTERNO | 1. Iniciação |
| Documentação Layout Lógico | 2. Planejamento & Documentação |
| Documentação Layout Elétrico | 2. Planejamento & Documentação |
| Solicitação de Acesso Remoto | 3. Provisionamento de Recursos |
| Solicitação de VPN | 3. Provisionamento de Recursos |
| Solicitação Range de IPs | 3. Provisionamento de Recursos |
| Instalação Física Equipamentos | 4. Implementação |
| Configuração de Rede | 4. Implementação |
| Validação Acesso Remoto - Homolog | 5. Testes & Homologação |
| Validação VPN - Homolog | 5. Testes & Homologação |
| Testes de Integração | 5. Testes & Homologação |
| Validação Acesso Remoto - Produção | 6. Deploy em Produção |
| Validação VPN - Produção | 6. Deploy em Produção |
| Cutover Produção | 6. Deploy em Produção |
| Monitoramento Intensivo | 7. Estabilização |
| Lembretes (validações periódicas) | 7. Estabilização |
| Criar procedimento de trabalho | 8. Encerramento |
| Range de IPs - Atualizar documentação | 8. Encerramento |
| Aceite Formal | 8. Encerramento |
| Concluído | 8. Encerramento |

---

## 🚀 COMO USAR

### Passo 1: Preparar o Excel

**Opção A - Começar do zero:**
1. Use o template `template-dados-v7.csv` como exemplo
2. Copie a estrutura para o seu Excel
3. Preencha seus projetos

**Opção B - Migrar seus dados atuais:**
1. Abra seu Excel atual
2. Na aba "ATIVIDADES", adicione coluna F "Macro Etapa"
3. Configure validação de dados (lista suspensa):
   - Dados → Validação de Dados
   - Permitir: Lista
   - Origem: `1. Iniciação,2. Planejamento & Documentação,3. Provisionamento de Recursos,4. Implementação,5. Testes & Homologação,6. Deploy em Produção,7. Estabilização,8. Encerramento`

### Passo 2: Preencher Macro Etapas

**Estratégia recomendada:**
1. Comece com 2-3 projetos piloto (ex: COUGAR, BETA)
2. Preencha a coluna F dessas atividades usando a tabela de mapeamento acima
3. Teste o dashboard
4. Se aprovado, classifique os outros projetos

**IMPORTANTE:** 
- Projetos **COM** macro etapa → Aparecem na Visão Executiva + Completa
- Projetos **SEM** macro etapa → Aparecem apenas na Visão Completa
- Sistema é 100% compatível com dados antigos (sem macro)

### Passo 3: Carregar no Dashboard

1. Abra `admin.html`
2. Faça upload do Excel
3. Confira o resumo:
   - Total de atividades
   - Atividades COM macro etapa
   - Atividades SEM macro etapa
4. Clique em "Ver Dashboard"

### Passo 4: Usar o Dashboard

**No index.html:**
- Use o toggle no topo para alternar entre visões
- **Visão Executiva:** Mostra cards de macro etapas com % e projetos
- **Visão Completa:** Mostra cards de projetos (igual v6.2.1)
- Filtros funcionam nas duas visões

---

## 📊 EXEMPLO VISUAL

### Visão Executiva
```
┌─────────────────────────────────────┐
│  1. Iniciação               100%    │
│  ████████████████████████████       │
│  8/8 atividades concluídas          │
│  Projetos: COUGAR, BETA, NAVEPARK   │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│  2. Plan. & Documentação    75%     │
│  ████████████████████░░░░░░         │
│  12/16 atividades concluídas        │
│  Projetos: COUGAR, BETA             │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│  3. Provisionamento         33%     │
│  ████████░░░░░░░░░░░░░░░░░░         │
│  4/12 atividades concluídas         │
│  Projetos: COUGAR, BETA             │
└─────────────────────────────────────┘
```

### Cores
- 🟢 Verde: 100% concluído
- 🟡 Amarelo: 50-99% concluído
- 🔴 Vermelho: 0-49% concluído

---

## ⚠️ DICAS IMPORTANTES

### Para Douglas/Diretoria
- **Use Visão Executiva** - mostra o big picture em 8 etapas
- **Exporte PDF** - mesma funcionalidade da v6.2.1
- **Cores intuitivas** - verde = ok, amarelo = atenção, vermelho = crítico

### Para Você (Operacional)
- **Use Visão Completa** - tem todos os detalhes que você precisa
- **Classifique aos poucos** - não precisa preencher tudo de uma vez
- **Teste primeiro** - valide com 2 projetos antes de classificar todos

### Compatibilidade
- ✅ Projetos sem macro continuam funcionando normalmente
- ✅ Você pode adicionar macros gradualmente
- ✅ Visão Completa idêntica à v6.2.1

---

## 🎯 PRÓXIMOS PASSOS (Roadmap Futuro)

Se a Visão Executiva for aprovada pela diretoria:

**v7.1 (Possível):**
- Timeline visual tipo Gantt
- Drill-down (clicar na macro e ver atividades)
- Exportar só Visão Executiva

**v7.2 (Possível):**
- Filtro por macro etapa na Visão Completa
- Dashboard comparativo (macro x projeto)

---

## 📁 ESTRUTURA DE ARQUIVOS

```
dashboard-pmo-v7/
├── index.html              ← Dashboard com toggle
├── admin.html              ← Carregamento de dados
├── view-detalhada.html     ← (mantém da v6.2.1)
├── view-simples.html       ← (mantém da v6.2.1)
├── template-dados-v7.csv   ← Template com macro etapas
└── README-v7.md            ← Este arquivo
```

---

## 🆘 TROUBLESHOOTING

**Problema:** Visão Executiva está vazia
- **Solução:** Preencha a coluna F "Macro Etapa" em pelo menos 1 projeto

**Problema:** Cards não aparecem na Visão Executiva
- **Solução:** Verifique se o texto da macro está EXATAMENTE igual (com números e pontos)

**Problema:** Quero voltar para v6.2.1
- **Solução:** Basta usar a Visão Completa - funciona igual

**Problema:** Excel não tem validação de dados
- **Solução:** Não é obrigatório. Pode digitar manualmente (mas cuidado com erros de digitação)

---

## 📞 SUPORTE

Qualquer dúvida:
1. Verifique a tabela de mapeamento acima
2. Teste com 1 projeto piloto primeiro
3. Me avise se encontrar bugs

**Versão:** 7.0  
**Data:** 30/01/2025  
**Autor:** Claude + Daia  
