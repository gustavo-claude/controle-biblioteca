# Pasta `exemplos/` — O Padrão Visual de Qualidade

> 💡 **PAPEL DESTA PASTA:**  
> Modelos de linguagem aprendem muito melhor por **exemplos concretos** (few-shot prompting) do que por descrições teóricas abstratas. Esta pasta guarda a "foto do prato pronto no cardápio": o modelo exato do que esperamos receber e o contra-exemplo do que nunca aceitaremos.

Cada tipo de artefato fica na própria subpasta, com o par bom e ruim.

```
exemplos/
├── prompts-uteis.md
├── RECEITA.md
├── especificacoes/
│   ├── especifcacao-boa.md
│   └── especificacao-ruim.md
└── funcionalidades/
    ├── funcionalidades-bom.md
    └── funcionalidades-ruim.md
```

---

## 1. Por que ter exemplos bons e ruins?

- **Especificação boa (`especificacoes/especifcacao-boa.md`):** Mostra à IA a profundidade, a formatação, o nível de detalhe dos critérios de aceitação e como vincular regras de negócio.
- **Especificação ruim (`especificacoes/especificacao-ruim.md`):** Ensina à IA os vícios mais comuns que ela deve evitar a todo custo (soluções técnicas prematuras, adjetivos vagos, falta de caminhos de erro).
- **Funcionalidades boas (`funcionalidades/funcionalidades-bom.md`):** Mostra a tabela de funcionalidades, com descrição, problema que resolve e benefícios, mais os limites e o não-escopo vindos do contexto e do analista.
- **Funcionalidades ruins (`funcionalidades/funcionalidades-ruim.md`):** Mostra a lista solta, sem problema nem benefício, com solução técnica, escopo inflado e não-escopo que não exclui nada.

---

## 2. Como usar os exemplos no dia a dia

Quando você for pedir para a IA redigir uma especificação ou auditar um requisito, referencie os arquivos da pasta:

```markdown
@escritor redija a especificação seguindo rigorosamente o padrão e o nível de detalhe de @exemplos/especificacoes/especifcacao-boa.md. Evite os vícios de @exemplos/especificacoes/especificacao-ruim.md.
```

Para a lista de funcionalidades de um sistema:

```markdown
@facilitador monte a lista de funcionalidades seguindo @exemplos/funcionalidades/funcionalidades-bom.md. Evite os vícios de @exemplos/funcionalidades/funcionalidades-ruim.md.
```

Prompts prontos para o dia a dia estão em `exemplos/prompts-uteis.md`.

---

## 3. Substituição por Casos Reais

Assim que o seu time produzir a primeira especificação real aprovada com louvor pelos desenvolvedores, **substitua o exemplo genérico pelo seu exemplo real**. Um exemplo do próprio domínio vale 10 vezes mais do que um exemplo neutro.

---

## 4. Como criar um novo par de exemplos

Para um tipo de artefato que ainda não tem modelo (parecer, comunicado, mapa, etc.), crie uma subpasta com o nome do tipo e, dentro dela, o par bom e ruim. Não apague os pares já existentes em `especificacoes/` e `funcionalidades/`.

> 📖 Siga `exemplos/RECEITA.md` (guia exclusivo do operador humano; nunca lido por IA).
