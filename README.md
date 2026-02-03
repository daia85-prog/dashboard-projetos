# 📊 Dashboard de Status de Projetos - Infraestrutura TI

> **Versão:** 9.0  
> **Última atualização:** 03/02/2026  
> **Desenvolvido para:** Douglas (Gestor) - Invent Corp  
> **PMO:** Daiana

---

## 📁 ESTRUTURA DE ARQUIVOS

| Arquivo | Descrição |
|---------|-----------|
| **index.html** | Dashboard principal - KPIs, Visão Macro/Micro, Fases, Tratativas |
| **admin.html** | Administração - importar Excel, gerenciar projetos |
| **Dashboard_Projetos_v9.xlsx** | Planilha modelo com dados dos projetos |

---

## 🎯 FUNCIONALIDADES v9

### Dashboard Principal (index.html)

- **Visão Executiva (Macro)**: Cards de fases com % de conclusão
- **Visão por Projeto (Micro)**: Cards individuais de projetos
- **8 Fases padronizadas** com 23 atividades por projeto
- **Sistema de Tratativas**: Histórico de atualizações por atividade
- **Filtros**: Status, Prioridade, Local, Responsável
- **KPIs**: Total, Concluídos, Em Andamento, Atrasados, Críticos
- **Modal de Projeto**: Detalhes, atividades, tratativas
- **Impressão/PDF**: Exportar relatórios

### Administração (admin.html)

- Upload de Excel via drag-and-drop
- Gerenciamento de projetos
- Visualização de atividades padrão
- Exportar dados JSON

---

## 📋 ESTRUTURA DE FASES E ATIVIDADES

| Fase | Atividades |
|------|------------|
| 1. Kickoff | Reunião de Kickoff, Definição de Escopo |
| 2. Levantamento & Design | Levantamento Técnico, Documentação de Arquitetura, Elaboração do Cronograma |
| 3. Provisionamento | Solicitação de Acessos, Aquisição de Equipamentos, Preparação de Ambiente |
| 4. Implantação | Instalação Física, Configuração de Rede, Integração de Sistemas |
| 5. Homologação | Testes Funcionais, Testes de Performance, Validação com Cliente |
| 6. Go Live | Janela de Mudança (GMUD), Migração para Produção, Validação Pós-Migração |
| 7. Hypercare | Monitoramento Intensivo, Correção de Incidentes, Ajustes e Otimização |
| 8. Encerramento | Documentação Final, Treinamento/Repasse, Aceite Formal |

**Total: 23 atividades por projeto**

---

## 🎨 REGRAS DE CORES

### Por Progresso
| Cor | Condição |
|-----|----------|
| 🟢 Verde | ≥ 80% concluído |
| 🟡 Amarelo | 40-79% concluído |
| 🔴 Vermelho | < 40% concluído |

### Por Status de Atividade
| Status | Cor |
|--------|-----|
| Concluído | Verde |
| Em andamento | Azul |
| Aguardando | Amarelo |
| Não Iniciado | Cinza |

---

## 📊 PROJETOS INCLUÍDOS (30)

### Concluídos (13)
BARBECUE B2B, BELEZA, CANDELABRIA, CDSK, COUGAR, ESPERANÇA, GAVIÃO, OCTOPUS SC, OPTIMUS PRIME, PROMO B2B CD GRU, PTL SP, REISADO, SUPER DIVINOPOLIS

### Em Andamento (13)
BETA, BETA ESTEIO, BP, BR, CRISTAL MG RETROFIT, DIA, ELETRO, FLOWER, NAVEPARK, OCTOPUS MS, PBL GUATEMALA, REVERSE, TITANIO

### Não Iniciados (4)
DIAMANTE, MASTER, MKT CHILE, MKT PERU

---

## 🔧 COMO USAR

1. Acesse: https://daia85-prog.github.io/dashboard-projetos/
2. Use os toggles para alternar entre Visão Macro e Micro
3. Clique em um projeto para ver detalhes
4. Clique em uma atividade para ver tratativas
5. Use os filtros para encontrar projetos específicos

---

## 📞 Contato

**Desenvolvido por:** Infraestrutura TI - Invent Corp  
**PMO:** Daiana  
**Versão:** 9.0
