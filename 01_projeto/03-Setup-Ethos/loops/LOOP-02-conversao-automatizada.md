# LOOP-02 — Conversão automatizada

**Status:** RASCUNHO — validar na call de setup  
**Fase de origem:** Fase 4  
**Sistemas usados:** contrato de métrica F1, eventos de reserva F2 e visão por hotel F3  
**Agente responsável:** Analista de conversão

## 1. Meta
- **O que atingir:** medir a taxa de automatização de reservas por hotel e período com fonte e evento rastreáveis.
- **Prazo do ciclo:** [VALIDAR NA CALL DE SETUP].

## 2. Validação
- **Como saber:** taxa = concluídas por fluxo automatizado/Omni comprovado ÷ concluídas elegíveis na mesma fonte/hotel/período × 100.
- **Modo:** assistente mede; gestor/champion dá veredito.
- **Fonte independente:** contrato de métrica + eventos validados — [VALIDAR NA CALL DE SETUP].
- **Onde está hoje / alvo / unidade / cadência:** baseline, alvo e cadência [VALIDAR NA CALL DE SETUP]; unidade `%`.
- **Quem valida:** gestor/champion — [VALIDAR NA CALL DE SETUP].
- **Veredito:** atingido somente se cálculo reproduzível e alvo aprovado; D=0 = não aplicável; fonte/evento/meta ausentes = bloqueado.

## 3. Conectores
| Conector | Dado | Permissão mínima | Uso | Plano B | Status |
|---|---|---|---|---|---|
| fonte de métricas | eventos por hotel/período | leitura | cálculo | planilha/contrato | validar |

## 4. Skills
| Skill | Uso | Entrada | Saída | Obrigatória? |
|---|---|---|---|---|
| métricas/consulta | calcular e explicar | dados autorizados | taxa e inconsistências | sim |

## 5. Arranque
### Instruções permanentes
Nunca estime, atribua ou declare sucesso sem fonte/evento aprovados. Deduplicate por ID; registre versão, período e limitações. Não altera reserva, meta ou dado de origem.

### Primeiras tarefas
1. Confirmar contrato, baseline e acesso. 2. Reproduzir cálculo com fixture. 3. Rodar ciclo mínimo e pedir veredito.

- **Perseguir a meta sozinho:** não.
- **Limites:** leitura somente; sem meta inventada ou decisão de conversão.
- **Condição de pausa:** fonte incompleta, duplicidade sem resolução, D=0 ou ausência de aprovação.

## Dependências e riscos
- **Pré-condições:** SPEC-1-004 aceita; F2/F3 com eventos/visão validados.
- **Riscos:** atribuição indevida ou taxa enganosa.
- **Rollback:** parar ciclo e preservar cálculo/versionamento.
- **SPEC da fase 4:** [VALIDAR NA CALL DE SETUP].

## Evidências de origem
- Escopo Definitivo §§1,4–5; SPEC-1-004.