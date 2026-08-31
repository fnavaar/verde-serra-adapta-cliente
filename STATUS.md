# STATUS

- **Fase atual:** 1 — fundação pública e operação administrativa visível.
- **Progresso:** 1 de 13 tasks concluída (7,7%); as demais permanecem pendentes ou bloqueadas conforme a tabela da fase.
- **Task concluída:** F1-T01 — consolidar e aprovar inventário de conteúdo.
- **Champion de testes/aprovações:** Manoela — Sócia; aprovação humana registrada em 2026-08-31.
- **Pré-condição do inventário:** atendida — todos os hotéis compráveis no site são escopo; conteúdo aprovado; textos e imagens pertencem ao Circuito Elegante.
- **Projeto de construção:** Skip `Circuito Elegante` — projectId 54747 — Skip Cloud running.
- **Versão validada:** Skip `0.0.4`; preview https://circuito-elegante-f07ca--preview.goskip.app; não publicado em produção.
- **Evidência F1-T01:** catálogo com 80 hotéis, busca por nome/cidade/UF/estado/região ampla/região turística, filtros, detalhes, 404 e CTA de reserva inerte; QA e teste humano aprovados.
- **Próxima task:** F1-T02 — Confirmar Skip/RBAC; decisão vigente: Manoela Poroger = Gestor; Monica Valladão, Rubens Regis e Priscila Bentes = usuários comuns.
- **Escopo F1-T02:** implementar o acesso definido na coleção nativa `users`, com Manoela como Gestor e sem Admin para os demais.
- **Estado F1-T02:** bloqueada após autorização: não há migration existente e a documentação oficial de migrations/hooks do MCP está indisponível por erro de parâmetros; não foi possível comprovar sintaxe segura para campo de papel, provisionamento ou convite.
- **Gate:** disponibilizar documentação funcional do mecanismo de migrations/hooks ou um fluxo seguro aprovado de provisionamento/ativação; não criar contas, senhas ou permissões por suposição.
