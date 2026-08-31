# LOOP-03 — Saúde operacional

**Status:** RASCUNHO — validar na call de setup  
**Fase de origem:** Fase 4  
**Sistemas usados:** área administrativa e registros/exceções da Fase 3  
**Agente responsável:** Analista de saúde operacional

## 1. Meta
- **O que atingir:** manter visíveis exceções de indicação/comissão e registros sem desfecho, encaminhando ao owner humano.
- **Prazo do ciclo:** [VALIDAR NA CALL DE SETUP].

## 2. Validação
- **Como saber:** relatório de exceções por hotel com estado, owner, prazo e pendência.
- **Modo:** assistente conta o que foi feito; humano valida no fim.
- **Fonte independente:** área administrativa da plataforma — [VALIDAR NA CALL DE SETUP].
- **Onde está hoje / alvo / unidade / cadência:** [VALIDAR NA CALL DE SETUP].
- **Quem valida:** gestor/champion — [VALIDAR NA CALL DE SETUP].
- **Veredito:** válido somente quando política de comissão, alçadas, owner/SLA e fonte estiverem registrados.

## 3. Conectores
| Conector | Dado | Permissão mínima | Uso | Plano B | Status |
|---|---|---|---|---|---|
| plataforma administrativa | exceções e registros | leitura | fila/relatório | revisão manual | validar |

## 4. Skills
| Skill | Uso | Entrada | Saída | Obrigatória? |
|---|---|---|---|---|
| análise de exceções | priorizar e consolidar | registros autorizados | fila/relatório | sim |

## 5. Arranque
### Instruções permanentes
Leia registros autorizados, exponha pendências e indique owner/prazo definidos. Não calcula, aprova ou paga comissão; não altera alçada nem decide exceção.

### Primeiras tarefas
1. Confirmar política, fonte, owner/SLA e acesso. 2. Gerar fila com dados sintéticos. 3. Revisar com gestor e registrar veredito.

- **Perseguir a meta sozinho:** não.
- **Limites:** sem decisão de comissão, escrita financeira ou comunicação externa.
- **Condição de pausa:** política/owner/SLA ausente, acesso negado ou registro incompleto.

## Dependências e riscos
- **Pré-condições:** F3 aceita; regra de comissão e rastreabilidade de indicação aprovadas.
- **Riscos:** transformar alerta em decisão financeira.
- **Rollback:** pausar ciclo e manter relatório; nenhum registro é alterado automaticamente.
- **SPEC da fase 4:** [VALIDAR NA CALL DE SETUP].

## Evidências de origem
- Escopo Definitivo §5 F3–F4; §6 risco 4.