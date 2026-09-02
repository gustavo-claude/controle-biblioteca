# Pasta `exemplos/` — O Padrão Visual de Qualidade

> 💡 **PAPEL DESTA PASTA:**  
> Modelos de linguagem aprendem muito melhor por **exemplos concretos** (few-shot prompting) do que por descrições teóricas abstratas. Esta pasta guarda a "foto do prato pronto no cardápio": o modelo exato do que esperamos receber e o contra-exemplo do que nunca aceitaremos.

---

## 1. Por que ter exemplos bons e ruins?

- **O Exemplo Bom (`historia-boa.md`):** Mostra à IA a profundidade, a formatação, o nível de detalhe dos critérios BDD e como vincular regras de negócio.
- **O Exemplo Ruim (`historia-ruim.md`):** Ensina à IA os vícios mais comuns que ela deve evitar a todo custo (soluções técnicas prematuras, adjetivos vagos, falta de caminhos de erro).

---

## 2. Como usar os exemplos no dia a dia

Quando você for pedir para a IA redigir uma história ou auditar um requisito, referencie os arquivos da pasta:

```markdown
@escritor redija a história para a funcionalidade de reabertura de chamados seguindo rigorosamente o padrão e nível de detalhe de @exemplos/historia-boa.md.
```

---

## 3. Substituição por Casos Reais

Assim que o seu time produzir a primeira história real aprovada com louvor pelos desenvolvedores, **substitua o exemplo genérico pelo seu exemplo real**. Um exemplo do próprio domínio vale 10 vezes mais do que um exemplo neutro.

---

## 4. Como criar um novo par de exemplos

Para um tipo de artefato que ainda não tem modelo (parecer, comunicado, mapa, etc.), crie o par `[tipo]-bom.md` + `[tipo]-ruim.md` sem apagar os exemplos de história já existentes.

> 📖 Siga `exemplos/RECEITA.md` (guia exclusivo do operador humano; nunca lido por IA).
