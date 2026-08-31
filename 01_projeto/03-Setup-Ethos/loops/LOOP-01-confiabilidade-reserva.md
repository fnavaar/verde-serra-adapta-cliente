# LOOP-01 — Confiabilidade de reserva

**Status:** RASCUNHO — validar na call de setup  
**Fase de origem:** Fase 4  
**Sistemas usados:** eventos/trilha da plataforma (F1–F3) e Omni validado (F2)  
**Agente responsável:** Operador de confiabilidade

## 1. Meta
- **O que atingir:** manter visíveis e tratadas as falhas, fallbacks e pendências do fluxo de reserva por hotel.
- **Prazo do ciclo:** [VALIDAR NA CALL DE SETUP].

## 2. Validação
- **Como saber:** relatório com eventos de falha/fallback/pendência, estado e owner por hotel.
- **Modo:** assistente mede e humano valida no fim.
- **Fonte independente:** logs/trilha da plataforma e Omni — [VALIDAR NA CALL DE SETUP].
- **Onde está hoje / alvo / unidade / cadência:** [VALIDAR NA CALL DE SETUP].
- **Quem valida:** gestor/champion — [VALIDAR NA CALL DE SETUP].
- **Veredito:** ciclo é válido apenas se fonte, período e responsáveis estiverem registrados; caso contrário, bloqueado.

## 3. Conectores
| Conector | Dado | Permissão mínima | Uso | Plano B | Status |
|---|---|---|---|---|---|
| plataforma/Omni | eventos e falhas | leitura | consolidar relatório | registro manual | validar |

## 4. Skills
| Skill | Uso | Entrada | Saída | Obrigatória? |
|---|---|---|---|---|
| análise de eventos | agrupar falhas | eventos autorizados | relatório | sim |

## 5. Arranque
### Instruções permanentes
Leia apenas fontes autorizadas; agrupe por hotel/estado; não crie, cancele ou confirme reservas. Em dado ausente/erro, registre bloqueio e peça validação humana.

### Primeiras tarefas
1. Confirmar fonte/acesso e baseline. 2. Executar um ciclo com dados sintéticos/autorizados. 3. Medir e registrar pendências.

- **Perseguir a meta sozinho:** não.
- **Limites:** sem escrita Omni, e-mail ou decisão comercial.
- **Condição de pausa:** fonte/credencial ausente, evento ambíguo ou falha de integração.

## Dependências e riscos
- **Pré-condições:** F2/F3 aceitas; contrato Omni e papéis aprovados.
- **Riscos:** alerta sem fonte ou interpretação de falha como confirmação.
- **Rollback:** desativar ciclo e preservar relatório/evidência.
- **SPEC da fase 4:** [VALIDAR NA CALL DE SETUP].

## Evidências de origem
- Escopo Definitivo §5 F4; §6 risco 1 e 3.