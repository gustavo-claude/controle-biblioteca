# Wireflow: F028 Apresentar quantidades do painel

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F028` - Apresentar quantidades do painel
- **Passos de origem:** 1. Abrir a área de relatórios. 2. Abrir o painel. 3. Ver a quantidade de obras cadastradas, de leitores com empréstimo nos últimos 6 meses, de empréstimos ativos e de empréstimos atrasados.
- **Regras vinculadas:** `[RN-14]`
- **Rodadas com o operador:** 2 de 2, escolhas do orquestrador no papel de operador
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F028-apresentar-quantidades-do-painel.svg`

---

## 1. Wireflow em ASCII

Frame único. Sem seta: os passos exibem conteúdo nesta janela.

Frame A - Painel
Passo 1 - Abrir a área de relatórios
Passo 2 - Abrir o painel
Passo 3 - Ver a quantidade de obras cadastradas, de leitores com empréstimo nos últimos 6 meses, de empréstimos ativos e de empréstimos atrasados

```text
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| Acervo | Usuários | Empréstimos | [ Relatórios ]            |
|                                                              |
| +---------------------------+  +---------------------------+ |
| |           [ ]             |  |           [ ]             | |
| +---------------------------+  +---------------------------+ |
| Obras cadastradas              Leitores com empréstimo nos   |
|                                últimos 6 meses               |
| +---------------------------+  +---------------------------+ |
| |           [ ]             |  |           [ ]             | |
| +---------------------------+  +---------------------------+ |
| Empréstimos ativos             Empréstimos atrasados         |
+--------------------------------------------------------------+
```

Fora do retângulo:

Leitor com empréstimo nos últimos 6 meses tem ao menos um empréstimo cuja data de retirada está nos 6 meses anteriores à consulta.
Esse número não é a lista de leitores com empréstimo ativo.
[CONFIRMAR] Se obra removida entra na quantidade de obras cadastradas.
O painel não gera log e não mostra a mensagem de sucesso.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Fora do retângulo | Frame A - Painel | Título do frame | Acima da página, à esquerda | `F028` | Janela única dos passos 1 a 3 |
| Fora do retângulo | Passo 1 - Abrir a área de relatórios | Passo | Abaixo do título, fora da página | `F028` | O gestor abre a área de relatórios |
| Fora do retângulo | Passo 2 - Abrir o painel | Passo | Abaixo do passo 1, fora da página | `F028` | O painel abre nessa área |
| Fora do retângulo | Passo 3 - Ver a quantidade de obras cadastradas, de leitores com empréstimo nos últimos 6 meses, de empréstimos ativos e de empréstimos atrasados | Passo | Abaixo do passo 2, fora da página | `F028` | As quatro quantidades aparecem juntas |
| Frame A - Painel | Biblioteca Limoeiro | Barra | Topo da página | `F028` | Barra do gestor |
| Frame A - Painel | Acervo, Usuários, Empréstimos | Barra | Abaixo do nome | `F028` | Áreas sem destaque |
| Frame A - Painel | Relatórios | Barra em destaque | Na barra, à direita de Empréstimos | `F028` | Área de origem do painel. Realce funcional |
| Frame A - Painel | [ ] Obras cadastradas | Caixa de métrica | Primeira linha, à esquerda. Rótulo abaixo da caixa | `F028` | Valor só `[ ]`, sem quantidade desenhada |
| Frame A - Painel | [ ] Leitores com empréstimo nos últimos 6 meses | Caixa de métrica | Primeira linha, à direita. Rótulo abaixo da caixa | `F028` | Termo do glossário. Valor só `[ ]` |
| Frame A - Painel | [ ] Empréstimos ativos | Caixa de métrica | Segunda linha, à esquerda. Rótulo abaixo da caixa | `F028` | Status Empréstimo: Ativo. Valor só `[ ]` |
| Frame A - Painel | [ ] Empréstimos atrasados | Caixa de métrica | Segunda linha, à direita. Rótulo abaixo da caixa | `F028` | Status Empréstimo: Atrasado. Valor só `[ ]` |
| Fora do retângulo | Leitor com empréstimo nos últimos 6 meses tem ao menos um empréstimo cuja data de retirada está nos 6 meses anteriores à consulta | Texto | Abaixo da página | `F028` | Critério do termo oficial. O 6 é o termo, não uma quantidade na caixa |
| Fora do retângulo | Esse número não é a lista de leitores com empréstimo ativo | Texto | Abaixo da página | `F028` | A lista de leitores com empréstimo ativo é o recorte de `F025` |
| Fora do retângulo | [CONFIRMAR] Se obra removida entra na quantidade de obras cadastradas | Texto | Abaixo da página | `F028` | Lacuna da lista, HU-28 |
| Fora do retângulo | O painel não gera log e não mostra a mensagem de sucesso | Texto | Abaixo da página | `F028` | `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** As quatro caixas mostram `[ ]`, sem quantidade desenhada. `[CONFIRMAR]` Se quantidade zero tem outro arranjo.
- **Carregamento / atualização:** `[CONFIRMAR]` O passo e a regra não definem carregamento.
- **Bloqueios e restrições:** O painel não gera log e não mostra a mensagem de sucesso (`[RN-14]`). `[CONFIRMAR]` Se obra removida entra na quantidade de obras cadastradas.

---

## 4. Notas para o Operador

Escolhas do orquestrador no papel de operador. Rodada 1: barra do gestor, com Relatórios em destaque, porque o painel fica na área de relatórios. Rodada 2: quatro caixas vazias, rótulo abaixo, valor só `[ ]`. Sem seta e sem mensagem de sucesso.

> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Se obra removida entra na quantidade de obras cadastradas.
> - [ ] `[CONFIRMAR]` Estado vazio quando a quantidade é zero, e carregamento do painel.
