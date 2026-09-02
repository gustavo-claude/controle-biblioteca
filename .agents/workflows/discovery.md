# Workflow: `/discovery`

> 💡 **OBJETIVO DO COMANDO:**  
> Orquestrar a preparação de sessões de levantamento com stakeholders e o processamento posterior de gravações ou atas salvas em `fontes/`, atualizando o cérebro do workspace com portões humanos de controle.

---

## Fluxo de Execução com Portões

```
[Início: Preparar Reunião OU Processar Notas Brutas]
        │
        ▼
[Fase 1: Preparação do Roteiro de Discovery]
        │
        ▼
   🛑 PORTÃO 1: PO ajusta o roteiro antes da reunião
        │
        ▼
[Reunião ocorre · PO salva notas/áudio em fontes/]
        │
        ▼
[Fase 2: @facilitador — Extração e Saneamento das Notas]
        │
        ▼
   🛑 PORTÃO 2: PO valida fatos extraídos e novas regras
        │
        ▼
[Fase 3: Atualização orientada dos arquivos de contexto/]
```

---

## Roteiro das Etapas

### Etapa 1: Gerar Roteiro de Perguntas (Pré-Reunião)
1. A IA lê `@contexto/produto.md` e identifica as lacunas de informação abertas.
2. Elabora 5 perguntas abertas de passado concreto ("Quando ocorreu...", "Como fizeram...").
3. 🛑 **PORTÃO 1 DE VALIDAÇÃO:**  
   > *Apresente o roteiro e pergunte: "PO, o roteiro cobre o objetivo da reunião? Deseja focar em algum ponto específico?"*  
   > **PARE AQUI E AGUARDE APROVAÇÃO.**

---

### Etapa 2: Processamento e Extração de Insumos (`@facilitador`)
1. O PO aponta para o arquivo de transcrição ou ata salvo em `fontes/AAAA-MM-DD-reuniao.md`.
2. A persona `@facilitador` varre o texto, separando:
   - Fatos novos confirmados;
   - Workarounds e gambiarras existentes;
   - Termos específicos de jargão falados na reunião;
   - Regras de negócio mencionadas.
3. 🛑 **PORTÃO 2 DE VALIDAÇÃO:**  
   > *Apresente o resumo estruturado e pergunte: "PO, estes fatos representam com fidelidade a reunião? Posso preparar as propostas de atualização do contexto?"*  
   > **PARE AQUI E AGUARDE APROVAÇÃO.**

---

### Etapa 3: Proposta de Atualização de Contexto
1. A IA gera as alterações sugeridas para:
   - `contexto/glossario.md` (novos termos ou sinônimos proibidos);
   - `contexto/regras-de-negocio.md` (novas regras invariantes com ID);
   - `contexto/decisoes.md` (decisões firmadas na sessão).
2. O PO revisa e aprova a gravação final nos arquivos de contexto.
