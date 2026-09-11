# STATUS

- **Fase atual:** 1 — fundação pública e operação administrativa visível.
- **Progresso:** 2 de 13 tasks concluídas (15,4%); as demais permanecem pendentes ou bloqueadas conforme a tabela da fase.
- **Tasks concluídas:** F1-T01 — inventário de conteúdo (2026-08-31); F1-T02 — acesso administrativo/RBAC (2026-09-11).
- **Champion de testes/aprovações:** Manoela — Sócia; testes de F1-T02 executados por Priscila Bentes (owner) com aprovação registrada em 2026-09-11.
- **Pré-condição do inventário:** atendida — todos os hotéis compráveis no site são escopo; conteúdo aprovado; textos e imagens pertencem ao Circuito Elegante.
- **Projeto de construção:** Skip `Circuito Elegante` — projectId 54747 — Skip Cloud running.
- **Versão validada:** Skip `0.0.12`; preview https://circuito-elegante-f07ca--preview.goskip.app; não publicado em produção.
- **Evidência F1-T01:** catálogo com 80 hotéis, busca por nome/cidade/UF/estado/região ampla/região turística, filtros, detalhes, 404 e CTA de reserva inerte; QA e teste humano aprovados.
- **Evidência F1-T02:** campo `role` (gestor/usuario) na coleção auth com regras de acesso (leitura só do próprio registro; criação/exclusão por superusuário); 4 contas da matriz provisionadas sem senha compartilhada; `/admin` com guarda de rota e negação por padrão; `/login`, `/recuperar-senha` e logout funcionais; hook impede alteração de papel por não-superusuário; template de e-mail de definição de senha em português; QA Skip 0.0.12 verde; testes humanos confirmados (login de usuário comum OK, acesso restrito OK, Gestor OK via fluxo nativo de definição de senha, logout OK).
- **Segurança:** nenhuma senha, token ou credencial versionada; segredos temporários usados em exceções autorizadas foram apagados do projeto após o uso.
- **Próxima task:** F1-T03 — Aprovar baseline de métrica (SPEC-1-004); pré-condição: fonte autorizada; dono: Gestor.
- **Gate:** seleção da próxima task exige novo pedido do champion; F1-T03 depende de fonte autorizada para o contrato de métrica.
