# CORRECTIONS.md — Medications

Base: HL7Norway/Medications@f757b7c (master). Usuário autorizou implementação de todas as propostas viáveis.

## Implementado

1. **`readme` → `README.md`** — substituiu arquivo de 4 bytes ("Test") por README.md adequado com propósito, estrutura, versionamento, licença.
2. **`.gitignore`** — expandido com fsh-generated/, output/, temp/, *.zip, *.log, .DS_Store, Thumbs.db.

## Não implementado (requer decisão do mantenedor ou revisão clínica)
- REA-003: revisão de status `draft` dos perfis FHIR (domínio clínico).
- REA-004: dependência externa `no-basis-Medication` — requer confirmação de disponibilidade.

## Validação
- Revisão estática concluída.
- Não executado: build FHIR/SUSHI (não aplicável).
