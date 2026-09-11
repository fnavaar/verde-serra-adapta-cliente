# AP-2026-09-11-1515 — Persistência de frontend no ciclo de QA do Skip

- Status: candidato
- Escopo: projeto do cliente (Circuito Elegante / Skip Cloud)
- Task/SPEC: F1-T02 · SPEC-1-002
- Sinal: arquivos de frontend escritos via MCP não persistiram na árvore do projeto após um ciclo de QA cuja migration falhou (versão 0.0.7): só as migrations sobreviveram, o QA ficou verde e a falha só apareceu no teste humano ("cliquei em entrar e nada aconteceu").
- Evidência: Debug Summary do dia; leitura dos arquivos reais do Skip após o QA 0.0.7 (App.tsx original, use-auth.tsx ausente, /login com 404) vs. QA verde reportado; correção na 0.0.8 reescrevendo os 6 arquivos.
- Regra reutilizável: após qualquer apply_changes, verificar a persistência real dos arquivos de frontend (skip_file_read) e exercitar o caminho do usuário no preview antes de declarar a task pronta — QA verde não prova que os arquivos chegaram à árvore.
- Quando aplicar: todo ciclo de implementação no Skip Cloud, especialmente quando uma migration falha no mesmo ciclo ou quando o QA passa sem exercício funcional do preview.
- Quando não aplicar: falhas de migration puramente de backend (migrations têm verificação própria em skip_cloud_list_migrations).
- Confiança: alta — causa raiz demonstrada por leitura dos arquivos e reprodução do sintoma no preview.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
