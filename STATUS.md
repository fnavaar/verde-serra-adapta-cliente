# STATUS

- **Fase atual:** 1 — fundação pública e operação administrativa visível.
- **Progresso:** 1 de 13 tasks concluída (7,7%); as demais permanecem pendentes ou bloqueadas conforme a tabela da fase.
- **Task concluída:** F1-T01 — consolidar e aprovar inventário de conteúdo.
- **Champion de testes/aprovações:** Manoela — Sócia; aprovação humana registrada em 2026-08-31.
- **Pré-condição do inventário:** atendida — todos os hotéis compráveis no site são escopo; conteúdo aprovado; textos e imagens pertencem ao Circuito Elegante.
- **Projeto de construção:** Skip `Circuito Elegante` — projectId 54747 — Skip Cloud running.
- **Versão validada:** Skip `0.0.4`; preview https://circuito-elegante-f07ca--preview.goskip.app; não publicado em produção.
- **Evidência F1-T01:** catálogo com 80 hotéis, busca por nome/cidade/UF/estado/região ampla/região turística, filtros, detalhes, 404 e CTA de reserva inerte; QA e teste humano aprovados.
- **Próxima task:** F1-T02 — Confirmar Skip/RBAC; matriz de papéis recebida: Monica e Manoela = Admin; Rubens e Priscila = Gestor.
- **Evidência F1-T02:** projeto Skip e autenticação nativa `users` acessíveis; coleção `users` não possui campo de papel, guarda `/admin`, matriz técnica persistida ou fluxo documentado de convite/ativação sem senha.
- **Estado F1-T02:** bloqueada por falta de mecanismo seguro de provisionamento de usuários/papéis e fluxo de ativação; nenhuma conta, senha ou permissão foi criada.
- **Gate:** disponibilizar fluxo seguro de convite/ativação e confirmar mecanismo aprovado para provisionar os quatro usuários sem expor credenciais.
