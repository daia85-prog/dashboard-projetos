# 🧪 GUIA DE TESTE - v7.2

## 🎯 OBJETIVO DO TESTE

Validar que a correção da v7.2 eliminou a inconsistência entre Visão Macro e Visão Micro.

---

## ⏱️ TEMPO ESTIMADO: 10 minutos

---

## 📋 PREPARAÇÃO

### 1. Substitua o arquivo
- Baixe o novo `index.html` (v7.2)
- Substitua no seu repositório ou pasta local

### 2. Carregue dados
- Abra `admin.html`
- Faça upload do Excel com dados reais
- Confirme "Dados carregados com sucesso"

---

## ✅ TESTE 1: Visão Executiva (Macro)

### Passo 1: Abra index.html
- URL: `index.html` no navegador
- Deve mostrar "Dashboard de Infraestrutura v7.2"

### Passo 2: Clique em "Visão Executiva (Macro)"
- Verifique os cards de fases
- Anote onde COUGAR aparece

**Resultado esperado:**
```
✅ COUGAR deve aparecer em APENAS UMA fase
✅ Provavelmente será "5. Testes & Homologação"
✅ Com percentual baixo (0% ou 25%)
```

### Passo 3: Anote os projetos por fase
Preencha a tabela:

| Fase | Projetos | % |
|------|----------|---|
| 1. Iniciação | _______ | __% |
| 2. Planejamento | _______ | __% |
| 3. Provisionamento | _______ | __% |
| 4. Implementação | _______ | __% |
| 5. Testes | _______ | __% |
| 6. Deploy | _______ | __% |
| 7. Estabilização | _______ | __% |
| 8. Encerramento | _______ | __% |

**Checklist:**
- [ ] Cada projeto aparece em apenas UMA linha
- [ ] COUGAR não está duplicado em múltiplas fases

---

## ✅ TESTE 2: Drill-Down (Macro → Micro)

### Passo 1: Na Visão Macro, clique no badge "COUGAR"
- Localize a fase onde COUGAR está
- Clique no badge dele

### Passo 2: Valide a Visão por Projeto
- Deve alternar para "Visão por Projeto (Micro)"
- O campo de busca deve estar preenchido com "COUGAR"
- Deve mostrar apenas o card do COUGAR

**Resultado esperado:**
```
✅ Transição automática para Visão Micro
✅ Filtro aplicado corretamente
✅ Card do COUGAR visível
```

---

## ✅ TESTE 3: Consistência Fase Atual

### Passo 1: Olhe o card do COUGAR na Visão Micro
- Localize o box azul "Fase atual"
- Anote o nome da fase e o percentual

**Exemplo:**
```
📘 Fase atual: 5. Testes & Homologação
   0% da fase concluído
```

### Passo 2: Compare com a Visão Macro
- Volte para "Visão Executiva (Macro)"
- Encontre COUGAR na lista
- Compare fase e percentual

**Resultado esperado:**
```
✅ Fase na Macro = Fase no Micro
✅ Percentual é consistente (pode haver pequena diferença por arredondamento)
```

**Tabela de Validação:**

| Aspecto | Visão Macro | Visão Micro | ✅ Bate? |
|---------|-------------|-------------|---------|
| **Fase do COUGAR** | _________ | _________ | [ ] Sim / [ ] Não |
| **Percentual** | ____% | ____% | [ ] Sim / [ ] Não |

---

## ✅ TESTE 4: Múltiplos Projetos

Repita o teste com outros 2 projetos:

### Projeto 2: BETA

**Visão Macro:**
- Fase: _____________
- Percentual: ____%

**Visão Micro:**
- Fase atual: _____________
- Percentual da fase: ____%

**Consistente?** [ ] Sim / [ ] Não

---

### Projeto 3: _____________ (escolha outro)

**Visão Macro:**
- Fase: _____________
- Percentual: ____%

**Visão Micro:**
- Fase atual: _____________
- Percentual da fase: ____%

**Consistente?** [ ] Sim / [ ] Não

---

## ✅ TESTE 5: Filtros e Navegação

### Passo 1: Teste filtros na Visão Macro
- [ ] Filtro de status funciona
- [ ] Filtro de localização funciona
- [ ] Filtro de responsável funciona
- [ ] Busca por nome funciona

### Passo 2: Teste navegação
- [ ] Alternar Macro ↔ Micro funciona
- [ ] Badges são clicáveis
- [ ] Volta para Macro sem perder dados

---

## ✅ TESTE 6: Cores de Risco

Valide as cores dos cards na Visão Macro:

| Percentual | Cor Esperada | Projetos | ✅ OK? |
|------------|--------------|----------|--------|
| ≥ 80% | 🟢 Verde | _______ | [ ] |
| 40-79% | 🟡 Amarelo | _______ | [ ] |
| < 40% | 🔴 Vermelho | _______ | [ ] |

---

## ✅ TESTE 7: Mensagens de Alerta

Verifique se aparecem alertas nas fases:

- [ ] Fase com 0%: Mostra "⏳ Aguardando início em todos os projetos"
- [ ] Fase com <40%: Mostra "⚠️ Fase com baixa execução no portfólio"
- [ ] Fase com ≥40%: Não mostra alerta

---

## 🎯 CHECKLIST FINAL

Antes de aprovar a v7.2, confirme:

### Funcionalidade:
- [ ] Cada projeto aparece em APENAS UMA fase na macro
- [ ] Fase macro = fase micro para todos os projetos
- [ ] Percentuais são consistentes entre macro e micro
- [ ] Drill-down (clicar em badge) funciona
- [ ] Filtros funcionam em ambas as visões
- [ ] Navegação macro ↔ micro fluida

### Visual:
- [ ] Cores refletem os percentuais (verde/amarelo/vermelho)
- [ ] Badges são clicáveis com hover roxo
- [ ] Mensagens de alerta aparecem quando necessário
- [ ] Box azul "Fase atual" aparece nos cards
- [ ] Título mostra "v7.2"

### Performance:
- [ ] Carregamento é rápido (<2 segundos)
- [ ] Sem erros no console do navegador (F12)
- [ ] Transições são suaves

---

## 🐛 SE ENCONTRAR PROBLEMAS

### Problema: Projeto duplicado em múltiplas fases
**Ação:** Reporte imediatamente - bug crítico não corrigido

### Problema: Fase macro ≠ fase micro
**Ação:** 
1. Verifique se os dados do Excel estão corretos
2. Recarregue os dados
3. Se persistir, reporte

### Problema: Percentuais muito diferentes
**Ação:** Pequenas diferenças (1-2%) são normais por arredondamento. Diferenças >5% devem ser reportadas.

### Problema: Badges não clicáveis
**Ação:** Verifique se JavaScript está habilitado no navegador

---

## ✅ RESULTADO DO TESTE

**Data do teste:** __/__/____

**Testador:** __________

**Versão testada:** v7.2

**Status geral:**
- [ ] ✅ APROVADO - Pronto pra produção
- [ ] ⚠️ APROVADO COM RESSALVAS - Listar abaixo
- [ ] ❌ REPROVADO - Bugs críticos encontrados

**Observações:**
_____________________________________
_____________________________________
_____________________________________

**Bugs encontrados:**
_____________________________________
_____________________________________
_____________________________________

**Aprovação final:**
- [ ] Sim, pode substituir a v7.1 no GitHub
- [ ] Não, precisa de correções adicionais

---

## 🚀 APÓS APROVAÇÃO

1. **Substitua no GitHub:**
   ```
   git add index.html
   git commit -m "fix: correção consistência macro x micro v7.2"
   git push origin main
   ```

2. **Comunique a equipe:**
   > "Dashboard atualizado para v7.2 - correção de inconsistência entre visões macro e micro. Cada projeto agora aparece em apenas uma fase."

3. **Agende apresentação pro Douglas:**
   - Mostre o antes/depois
   - Explique a correção
   - Destaque a consistência

---

**BOM TESTE!** 🧪
