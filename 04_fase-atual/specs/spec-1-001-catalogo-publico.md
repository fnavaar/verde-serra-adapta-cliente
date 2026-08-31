# SPEC-1-001 — Catálogo público e migração

**Resultado:** preview com inicial → catálogo → detalhe de hotel, só com conteúdo aprovado. CTA de reserva é inerte: não chama Omni, não cria reserva e não solicita pagamento.

**Inclui:** catálogo, detalhe, vazio e 404. **Fora:** Omni, preço, reserva, pagamento, e-mail e dados de hóspede. **Pré-condição:** inventário aprovado (origem/destino, conteúdo, mídia/direito, status, aprovador). Sem inventário, parar.

**Aceite:** catálogo/detalhes aprovados acessíveis; incompletos/arquivados fora; CTA sem chamada externa; vazio/404 seguros.

**TDD:** RED item incompleto/slug inválido; GREEN dois hotéis sintéticos aprovados; regressão para vazio, arquivado e CTA.

**Tasks:** F1-T01, F1-T04, F1-T05, F1-T10.