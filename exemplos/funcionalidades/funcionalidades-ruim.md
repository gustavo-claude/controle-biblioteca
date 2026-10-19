# [EXEMPLO RUIM] Lista de Funcionalidades do Produto: Classificação de Risco

> ⚠️ **CONTRA-EXEMPLO ANOTADO (O QUE NÃO FAZER):**  
> Este documento reúne os erros mais comuns ao listar funcionalidades de um sistema. Compare com `funcionalidades-bom.md`: lá cada item é uma linha de tabela, o título da funcionalidade segue Ação, Resultado e Objeto, há problema e benefício, e os limites vêm do contexto.

---

## 1. O que o sistema vai ter

- Triagem inteligente  
  > ❌ **ERRO 1 (Lista solta, sem tabela):** Não há ID, descrição, problema nem benefício. "Inteligente" não diz o que a pessoa faz no sistema.  
  > 🛠️ **Como corrigir:** Uma linha da tabela, como em `funcionalidades-bom.md`: ID, funcionalidade, descrição, problema que resolve e benefícios que traz.

- Tela moderna, robusta e em tempo real, feita em React, com a fila gravada no Redis  
  > ❌ **ERRO 2 (Adjetivo vago e solução técnica):** "Moderna" e "robusta" não se testam. React e Redis são decisão de engenharia, não funcionalidade.  
  > 🛠️ **Como corrigir:** Descreva o comportamento visível, por exemplo organizar a fila pelo grau de risco e pelo tempo de espera. Apague a tecnologia.

- O sistema diagnostica o paciente e prescreve a medicação da urgência  
  > ❌ **ERRO 3 (Funcionalidade dentro do que o contexto proíbe):** O briefing deste exemplo veta diagnóstico e prescrição. A lista trata a proibição como capacidade.  
  > 🛠️ **Como corrigir:** Tire o item da tabela e registre a proibição em Limites e Não-Escopo.

- Dashboard completo de gestão hospitalar, com farmácia, faturamento, folha e regulação de leitos  
  > ❌ **ERRO 4 (Escopo inflado):** O contexto limita o produto à classificação de risco. Estas áreas foram declaradas fora.  
  > 🛠️ **Como corrigir:** Mantenha na tabela só o que o contexto e o analista sustentam. O restante entra na lista de não-escopo, com a origem.

- Melhorar a experiência do usuário e deixar o fluxo mais ágil  
  > ❌ **ERRO 5 (Problema ausente e benefício vazio):** Não há dor observável. "Mais ágil" não diz para quem, em relação a quê.  
  > 🛠️ **Como corrigir:** Nomeie o problema de hoje (espera por ordem de chegada, desencontro entre recepção e triagem) e o benefício concreto que a funcionalidade entrega.

- Telemedicina internacional, porque é tendência de mercado  
  > ❌ **ERRO 6 (Sem origem no contexto nem no analista):** A funcionalidade foi inventada. Não há fato em `contexto/` nem pedido do analista. Também não está marcada como suposição.  
  > 🛠️ **Como corrigir:** Não inclua. Se for hipótese para discutir, marque `⚠️ [SUPOSIÇÃO]` e não a trate como decidida.

- Fila Dinâmica de Atendimento Médico Priorizada  
  > ❌ **ERRO 7 (Título fora do padrão ARO):** O nome é um rótulo. Não traz, nesta ordem, a ação (verbo no infinitivo), o resultado (efeito obtido) e o objeto sobre o qual o resultado incide.  
  > 🛠️ **Como corrigir:** Reescreva no formato `[Ação] [resultado] de/do/da [objeto]`, como em `funcionalidades-bom.md`: "Organizar fila priorizada do atendimento médico" — Organizar (ação), fila priorizada (resultado), atendimento médico (objeto).

---

## 2. Fora de escopo

- O sistema pode evoluir para fazer tudo o que a unidade precisar no futuro.  
  > ❌ **ERRO 8 (Não-escopo que não exclui nada):** A frase não vem do briefing e não impede nenhuma funcionalidade. Some com o limite que a tabela deveria respeitar.  
  > 🛠️ **Como corrigir:** Liste proibições fechadas, copiadas do contexto, no formato do exemplo bom: sem diagnóstico ou prescrição, sem substituir o profissional, sem gestão hospitalar externa, sem substituir o prontuário.
