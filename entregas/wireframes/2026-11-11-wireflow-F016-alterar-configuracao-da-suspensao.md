# Wireflow: F016 Alterar configuração da suspensão

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F016` - Alterar configuração da suspensão
- **Passos de origem:** 1. Na tela de registrar o empréstimo, ver a chave de suspensão daquele empréstimo. 2. Se o gestor liga a chave: 2a. Ligar a suspensão para aquele empréstimo. Senão: 2b. Desligar a suspensão para aquele empréstimo.
- **Regras vinculadas:** `[RN-08]`, `[RN-14]`, `[DEC-03]`
- **Rodadas com o operador:** 2 de 2, escolhas do orquestrador no papel de operador: Tela de registrar empréstimo; Chave em destaque.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F016-alterar-configuracao-da-suspensao.svg`

Escolhas do orquestrador no papel de operador. Um frame só. Sem seta: os dois botões são alternativas nesta janela. A página é a mesma de `F017`.

---

## 1. Wireflow em ASCII

Sem seta: os passos exibem conteúdo nesta janela.

```text
Passo 1. Na tela de registrar o empréstimo, ver a chave de suspensão daquele empréstimo.
Passo 2. Ligar a suspensão para aquele empréstimo, ou desligar.
Frame A - Chave da suspensão
+------------------------------------------------------------------+
| Biblioteca Limoeiro | Acervo | Usuários | Empréstimos | Relatórios |
|                                                                  |
| Registrar empréstimo                                             |
|                                                                  |
| Leitor                                                           |
| [                          ]  [ Suspenso ]  [ Sem suspensão em vigor ]
|                                                                  |
| Código do exemplar                                               |
| [                          ]                                     |
|                                                                  |
| Chave de suspensão                                               |
| [ Ligar a suspensão ]  [ Desligar a suspensão ]                  |
|                                                                  |
| [ Registrar empréstimo ]                                         |
| operação feita com sucesso                                       |
+------------------------------------------------------------------+

Sem seta: os dois botões são alternativas nesta janela.
Ligada, a devolução atrasada pode suspender.
Desligada, não suspende.
A suspensão não começa no atraso automático.
Diverge de RN-08.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Chave da suspensão | Biblioteca Limoeiro, Acervo, Usuários, Empréstimos, Relatórios | barra | Topo da página | `F017` | Mesma página de registrar o empréstimo. Área atual: Empréstimos. |
| Frame A - Chave da suspensão | Registrar empréstimo | título da página | Abaixo da barra | `F017` | Passo 1. A chave não tem página própria de configuração da biblioteca. |
| Frame A - Chave da suspensão | Leitor | campo | Abaixo do título, vazio | `F017` | Permanece na página. A chave é daquele empréstimo. |
| Frame A - Chave da suspensão | Suspenso | rótulo | Ao lado do campo Leitor | `F017` | Rótulo da página de `F017`. Não é a chave. |
| Frame A - Chave da suspensão | Sem suspensão em vigor | rótulo | Ao lado de Suspenso | `F017` | Rótulo da página de `F017`. |
| Frame A - Chave da suspensão | Código do exemplar | campo | Abaixo de Leitor, vazio | `F017` | O exemplar daquele empréstimo. |
| Frame A - Chave da suspensão | Chave de suspensão | rótulo | Acima dos dois botões | `F016` | Passo 1. Nome da chave daquele empréstimo. |
| Frame A - Chave da suspensão | Ligar a suspensão | botão | Em destaque, à esquerda | `F016` | Passo 2a. Alternativa. Fundo em destaque. Ligada, a devolução do exemplar atrasado pode suspender o leitor pela duração informada nesse instante (`F020`). |
| Frame A - Chave da suspensão | Desligar a suspensão | botão | Em destaque, ao lado | `F016` | Passo 2b. Alternativa. Fundo em destaque. Desligada, essa devolução não pede duração nem suspende. |
| Frame A - Chave da suspensão | Registrar empréstimo | botão | Abaixo da chave | `F017` | Botão primário da página. A gravação da chave acompanha o empréstimo. |
| Frame A - Chave da suspensão | operação feita com sucesso | linha | Abaixo do botão primário | `F017` | A chave entra no log desse registro. `[RN-14]` |
| Fora do frame | Ligada, a devolução atrasada pode suspender | texto | Abaixo da página | `F016` | O instante é a devolução do exemplar atrasado, não a passagem a atrasado. `[DEC-03]` |
| Fora do frame | Desligada, não suspende | texto | Abaixo da página | `F016` | A devolução segue sem suspensão. |
| Fora do frame | A suspensão não começa no atraso automático | texto | Abaixo da página | `F016` | `F018` muda o empréstimo para atrasado e não suspende o leitor. |
| Fora do frame | Diverge de RN-08 | texto | Abaixo da página | `F016` | `[RN-08]` e `[RN-14]` tratam ligar ou desligar como configuração da biblioteca. A lista coloca a chave neste empréstimo. Vale a lista. |

---

## 3. Estados da Interface

- **Estado vazio:** A chave aparece com as duas alternativas visíveis. Os campos de leitor e de exemplar ficam sem texto neste esboço.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Desligada, a devolução do exemplar atrasado não suspende. Ligada, a suspensão só pode começar nessa devolução. A passagem automática a atrasado não suspende o leitor. A gravação da chave não se separa do log do empréstimo (`[RN-14]`).

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas neste frame.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] A página desenhada é a de `F017`. O destaque deste wireflow é a chave. Os dois botões não abrem outra página.
> - [ ] A divergência com `[RN-08]` fica explícita. O contexto não foi alterado.
