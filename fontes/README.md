# Pasta `fontes/` — Depósito de Insumos Brutos

> 💡 **PAPEL DESTA PASTA:**  
> Esta pasta armazena os materiais brutos que servem de evidência e insumo para o trabalho de Product Ownership: gravações de entrevistas, transcrições de reuniões, documentos legados, relatórios de pesquisa e planilhas de referência.

---

## 1. Por que separar `fontes/` de `contexto/`?

- **`contexto/`** é o cérebro limpo e destilado (fatos curtos, regras ativas, glossário).
- **`fontes/`** é o arquivo histórico bruto. A IA **NÃO** lê esta pasta automaticamente; ela só acessa quando você apontar expressamente (ex: `@fontes/2026-08-30-reuniao-suporte.md`). Isso evita estourar o limite da janela de contexto da IA.

---

## 2. Convenção de Nomenclatura

Para manter o histórico organizado, use sempre a data no formato ISO no início do arquivo:

```
fontes/
├── AAAA-MM-DD-tipo-assunto.md
├── 2026-08-15-transcricao-entrevista-atendente.md
├── 2026-08-20-ata-alinhamento-diretoria.md
└── 2026-08-25-pesquisa-satisfacao-usuarios.pdf
```

---

## 3. Fluxo de Trabalho com Insumos

1. Cole o texto da reunião ou documento bruto nesta pasta;
2. Chame o comando `/discovery` ou a persona `@facilitador`;
3. A IA extrai os fatos verificáveis e propõe a atualização dos arquivos em `contexto/`.
