# Biblioteca de Prompts Úteis para o Dia a Dia do PO

> 💡 **PAPEL DESTE ARQUIVO:**  
> Coleção de comandos e prompts estruturados para acelerar seu trabalho no chat do Antigravity, garantindo que a IA adote a postura correta em cada fase do ciclo de produto.

---

## 1. Fase de Descoberta e Diagnóstico

### Prompt: "Não me proponha solução ainda"
```markdown
@analista leia o relato bruto abaixo sobre a dor que o setor de atendimento está enfrentando. NÃO me proponha nenhuma funcionalidade, botão ou tela agora. Apenas:
1. Descreva qual é a dor real por trás do pedido;
2. Aponte como as pessoas contornam isso hoje (workarounds);
3. Faça 3 perguntas sobre fatos do passado para clarificar o impacto.

[Colar aqui a mensagem do cliente ou stakeholder]
```

### Prompt: "Extrair fatos e termos de ata de reunião"
```markdown
@facilitador analise a transcrição da reunião salva em @fontes/reuniao-hoje.md.
Separe a saída em:
1. Fatos confirmados pelo cliente;
2. Hipóteses e suposições do time (marque com ⚠️);
3. Novos termos para avaliar no @contexto/glossario.md;
4. Regras de negócio mencionadas para o @contexto/regras-de-negocio.md.
```

---

## 2. Fase de Diagnóstico e Escrita

### Prompt: "Diagnóstico e Requisitos Ancorados nas Personas"
```markdown
@analista com base na solicitação abaixo e nas personas em @contexto/personas-usuario.md:
1. Identifique quais personas são afetadas por esta demanda;
2. Resgate a dor e o workaround documentados nelas que justificam esta necessidade;
3. Liste os requisitos funcionais essenciais e regras aplicáveis.
Apresente o resumo e aguarde minha aprovação antes de redigirmos a história formal.

[Colar a demanda/pedido aqui]
```

### Prompt: "Redigir história no padrão ouro"
```markdown
@escritor redija a especificação da história acima seguindo estritamente a estrutura de @exemplos/historia-boa.md e as regras de @.agents/rules/02-padrao-historias.md.
Certifique-se de incluir:
- Critérios BDD para Caminho Feliz, Caminho de Erro e Estado Vazio;
- Vinculação às regras de @contexto/regras-de-negocio.md;
- Seção explícita de "Fora de Escopo".
```

---

## 3. Fase de Revisão e Auditoria

### Prompt: "O Teste do Dev Irritado"
```markdown
@critico assuma o papel de um desenvolvedor sênior extremamente cético e exigente que acabou de receber o card abaixo para programar na próxima sprint.
Encontre todos os furos lógicos, ambiguidades de texto e casos de borda não tratados.
Classifique cada achado por severidade (🔴 Bloqueante, 🟡 Atenção, 🟢 Sugestão) e termine com as 3 perguntas mais duras sobre o comportamento do sistema.

[Colar aqui o rascunho da história]
```

### Prompt: "De onde veio essa afirmação?"
```markdown
@critico audite o documento abaixo e liste todas as afirmações, números, prazos, volumetrias e regras de negócio.
Para cada uma, indique se ela tem respaldo em @contexto/ ou se foi assumida/inventada pela IA.
```

---

## 4. Fase de Modelagem Visual

### Prompt: "Mapear Fluxo de Estados (Mermaid)"
```markdown
@escritor com base na funcionalidade especificada, use a skill mapear-fluxo para gerar o diagrama Mermaid de transição de estados do ciclo de vida deste item (do estado inicial até a conclusão/cancelamento).
```
