# Receita: Criar um Exemplo de Qualidade (Few-shot)

> 💡 **PAPEL DESTE ARQUIVO:**  
> Guia o operador a acrescentar pares **bom / ruim** em `exemplos/`. Modelos de linguagem calibram formato e profundidade muito melhor por exemplo concreto do que por parágrafo teórico.  
> 🚫 **DOCUMENTO EXCLUSIVO DO OPERADOR HUMANO (NUNCA DEVE SER LIDO POR IA):**  
> Este arquivo é um guia de referência técnica exclusivo para o usuário. Nenhuma IA deve ler, processar ou carregar este arquivo para a janela de contexto.  
> ⚠️ **REGRA DE OURO:** Um exemplo bom e um ruim do **mesmo tipo de artefato**. O ruim ensina o vício; o bom ensina o padrão. Sem o par, a IA imita o tom e esquece o limite.

---

## 1. Quando criar (e quando substituir)

**Crie um par novo quando:**
- Você pediu um tipo de saída que ainda não tem modelo (parecer, roteiro, matriz, comunicado, mapa, etc.).
- A IA acerta o conteúdo e erra o *formato* (seções, tom, o que não pode aparecer).

**Substitua o exemplo genérico quando:**
- O time aprovou o primeiro artefato *real* do domínio. Um caso da casa vale mais que o modelo neutro de chamados de suporte.

Não apague `historia-boa.md` / `historia-ruim.md` enquanto forem o padrão de histórias. Acrescente irmãos (`parecer-bom.md`, `parecer-ruim.md`) para outros tipos.

---

## 2. Anatomia do par

```
exemplos/
├── [tipo]-bom.md
├── [tipo]-ruim.md
└── prompts-uteis.md          ← atalhos de chat; não é o par few-shot
```

Cada arquivo do par leva o mesmo casco:

```markdown
# Exemplo [Bom | Ruim]: [Tipo de artefato]

> 💡 **PAPEL DESTE ARQUIVO:**  
> [PREENCHER: o que a IA deve copiar (bom) ou evitar (ruim).]  
> ⚠️ **Como usar:** aponte `@exemplos/[arquivo].md` no pedido. Não peça para a IA "ler a pasta exemplos inteira".

---

## O artefato

[PREENCHER: o texto *como se fosse* a saída real. Sem meta-comentário no meio das seções.]

---

## Por que este exemplo é [bom | ruim]

| Trecho / seção | O que demonstra |
|---|---|
| [PREENCHER] | [PREENCHER: a lição em uma linha] |
```

No arquivo **ruim**, a tabela lista vícios (solução técnica prematura, adjetivo vago, caminho de erro ausente, termo fora do glossário, etc.).  
No arquivo **bom**, a tabela aponta as virtudes correspondentes (mesmo conjunto de critérios, invertidos).

**Contraste didático de uso no chat**

- ❌ `"Escreva no mesmo nível de qualidade de sempre."`
- ✅ `"@escritor redija o [tipo] seguindo rigorosamente o padrão de @exemplos/[tipo]-bom.md. Evite os vícios de @exemplos/[tipo]-ruim.md."`

---

## 3. Passo a passo do operador

1. **Escolha o tipo de artefato** (um substantivo: história, parecer, comunicado, mapa de estados).
2. **Escreva primeiro o ruim** a partir de um erro real da IA, se houver. Erro inventado é mais fraco.
3. **Reescreva o bom** corrigindo *os mesmos* vícios — não mude o tema. O par precisa ser comparável.
4. **Anote 4 a 8 lições na tabela**, não um ensaio. A IA lê a tabela; o operador também.
5. **Registre uma linha** no `README.md` desta pasta.
6. **Se o tipo for recorrente**, acrescente um prompt em `prompts-uteis.md` que já aponta o par `@exemplos/...`.

---

## 4. Relação com skills e regras

- A **skill** aponta o exemplo em "Leituras prévias" (`exemplos/[tipo]-bom.md`).
- A **regra** de padrão (faixa `20–29`) descreve a estrutura obrigatória.
- O **exemplo** mostra a estrutura *preenchida*. Não copie a regra inteira para dentro do exemplo.

---

## 5. O que NUNCA fazer

- ❌ Só o exemplo bom (a IA não vê o limite).
- ❌ Exemplo bom que ainda contém um vício "pequeno" — vira licença.
- ❌ Segredo, dado pessoal ou cliente real em exemplo que vai para repositório compartilhado. Anonimize.
- ❌ Transformar `prompts-uteis.md` em dump de conversas inteiras.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DO PAR:
[ ] Existem [tipo]-bom.md e [tipo]-ruim.md, comparáveis?
[ ] O artefato está separado da tabela de lições?
[ ] O README desta pasta lista o par?
[ ] A skill correspondente aponta o exemplo bom nas leituras?
-->
