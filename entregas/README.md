# Pasta `entregas/` — Artefatos Formais de Saída

> 💡 **PAPEL DESTA PASTA:**  
> Esta pasta armazena todos os documentos formais produzidos pelo PO em parceria com a IA: histórias de usuário revisadas, especificações funcionais, relatórios de fatiamento de épicos e matrizes de priorização prontas para o time de desenvolvimento.

---

## 1. Padrão Obrigatório de Nomenclatura

Todo arquivo salvo nesta pasta deve seguir a regra de nomenclatura com data ISO e prefixo claro:

```
entregas/
├── AAAA-MM-DD-[TIPO]-[ID]-[assunto].md
├── 2026-08-31-US-01-abertura-chamado-anexo.md
├── 2026-08-31-EPICO-01-triagem-e-notificacoes.md
└── 2026-09-05-MATRIZ-priorizacao-sprint-12.md
```

---

## 2. Ciclo de Vida de uma Entrega

```
[Rascunho no Chat] 
       │
       ▼ (Skill: escrever-historia)
[Geração da História]
       │
       ▼ (Skill: revisar-criticamente / Persona @critico)
[Auditoria e Correções das 7 Lentes]
       │
       ▼ (Aprovação do PO)
[Arquivo Final Gravado em entregas/ com data e ID]
```

---

## 3. Regras de Manutenção

- Nunca edite uma entrega formal sem registrar a data da alteração ou gerar uma nova versão revisada;
- Arquivos desta pasta são os insumos diretos para o refinamento técnico da equipe de engenharia.
