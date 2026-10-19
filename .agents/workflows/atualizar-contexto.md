# Workflow: `/atualizar-contexto`

> 💡 **OBJETIVO DO COMANDO:**  
> Executar a rotina de higiene do workspace (ex: a rotina de 10 minutos de sexta-feira) para evitar que a documentação fique obsoleta e a IA comece a alucinar com regras antigas.

---

## Fluxo de Execução com Portões

```
[Início: Auditoria de Higiene de Contexto]
        │
        ▼
[Etapa 1: @facilitador — Varredura dos arquivos de contexto/]
        │
        ▼
   🛑 PORTÃO 1: PO avalia a lista de itens desatualizados ou podres
        │
        ▼
[Etapa 2: Aplicação das atualizações aprovadas]
```

---

## Roteiro das Etapas

### Etapa 1: Varredura de Higiene (`@facilitador`)
1. A IA lê todos os arquivos em `contexto/`:
   - Em `decisoes.md`: Verifica se alguma decisão atingiu o gatilho da cláusula *"Revisitar se..."*.
   - Em `regras-de-negocio.md`: Busca regras que foram modificadas ou revogadas nas entregas recentes.
   - Em `glossario.md`: Identifica novos termos surgidos em entregas que ainda não foram oficializados.
2. 🛑 **PORTÃO 1 DE AVALIAÇÃO:**  
   > *Apresente o checklist de higiene: "PO, encontrei [N] itens que precisam de revisão ou limpeza. Confirma as seguintes alterações nos arquivos de contexto?"*  
   > **PARE AQUI E AGUARDE APROVAÇÃO.**

---

### Etapa 2: Atualização e Consolidação
1. A IA aplica as modificações aprovadas diretamente nos arquivos de `contexto/`.
2. Emite um resumo consolidado do status de governança do workspace.
