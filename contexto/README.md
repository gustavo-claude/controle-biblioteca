# Pasta `contexto/` — O Cérebro do Workspace

> 💡 **PAPEL DESTA PASTA:**  
> A pasta `contexto/` guarda a verdade oficial sobre o produto, o domínio, os usuários e as regras de negócio. É o conjunto de documentos que alimenta a inteligência da IA para que as respostas sejam precisas e alinhadas.

---

## 1. A Régua de Ouro do Contexto

> 📏 **A Régua: "Se eu apagar esta linha, a IA erra a resposta?"**  
> - Se a resposta for **SIM**: A informação DEVE estar no contexto.
> - Se a resposta for **NÃO**: É texto decorativo, marketês ou detalhe irrelevante. **Apague.**

---

## 2. Mapa dos Arquivos de Contexto

| Arquivo | Para que serve | Tamanho Ideal | Quando Atualizar |
|---|---|:--:|---|
| `briefing.md` | O resumo essencial de 6 a 15 linhas | 15–20 linhas | Na criação do produto ou mudança de foco |
| `produto.md` | Ficha técnica: o que é, para quem, e **o que NÃO é** | 1 página | Na definição ou revisão de escopo |
| `personas-usuario.md` | Quem são as pessoas reais e seus workarounds de hoje | 1–2 páginas | Ao descobrir novos perfis ou dores |
| `glossario.md` | Termos canônicos, termos proibidos e lista de status | 1–2 páginas | A cada novo conceito ou dúvida de vocabulário |
| `regras-de-negocio.md` | Regras invariantes numeradas (`RN-01`, `RN-02`) e exceções | 1–3 páginas | A cada nova regra ou restrição acordada |
| `decisoes.md` | Diário de decisões (ADRs), opções descartadas e "Revisitar se" | Crescimento contínuo | A cada decisão de produto tomada |

---

## 3. O que NUNCA deve entrar nesta pasta

- ❌ Textos promocionais ou de marketing ("O melhor sistema do mercado");
- ❌ Manuais técnicos de infraestrutura ou diagramas de banco de dados;
- ❌ Atas de reunião completas não processadas (essas ficam em `fontes/`).

---

## 4. Como criar um documento novo nesta pasta

Os arquivos da tabela acima já vêm com instruções de preenchimento, seções e checklist. Para **acrescentar** um tipo de fato que ainda não tem casa (sem apagar os existentes):

> 📖 Siga `contexto/RECEITA-novo-documento.md` (guia exclusivo do operador humano; nunca lido por IA) e depois registre o arquivo novo na tabela da seção 2.
