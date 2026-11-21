# Wireflow: F017 Registrar empréstimo do exemplar

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F017` - Registrar empréstimo do exemplar
- **Passos de origem:** 1. Abrir a área de gestão de empréstimos. 2. Pesquisar o leitor. 3. Se o leitor está suspenso: 3a. Ver o leitor suspenso, recusar o empréstimo e encerre. Senão: 3b. Ver que a suspensão não está em vigor e seguir. 4. Identificar o exemplar. 5. Informar a chave de suspensão daquele empréstimo, ligada ou desligada. 6. Se o exemplar não está disponível: 6a. Se a obra tem exemplar emprestado, recusar o empréstimo e ver a data prevista mais próxima. 6b. Se o exemplar está indisponível e não há empréstimo, recusar o empréstimo e ver a mensagem sem data. Senão, se o empréstimo ultrapassa o máximo em paralelo em vigor: 6c. Recusar o empréstimo e encerre. Senão, se o leitor já tem empréstimo em paralelo da mesma obra: 6d. Recusar o empréstimo e encerre. Senão: 6e. Registrar o empréstimo. 7. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-03]`, `[RN-04]`, `[RN-05]`, `[RN-06]`, `[RN-08]`, `[RN-09]`, `[RN-10]`, `[RN-14]`, `[DEC-04]`, `[DEC-05]`
- **Rodadas com o operador:** 5 de 5, escolhas do orquestrador no papel de operador: Barra Empréstimos; Leitor; Código do exemplar; Chave de suspensão; Conclusão.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F017-registrar-emprestimo-do-exemplar.svg`

Escolhas do orquestrador no papel de operador. Um frame só. Sem seta: os passos exibem conteúdo nesta janela. As recusas ficam fora do frame.

---

## 1. Wireflow em ASCII

Sem seta: os passos exibem conteúdo nesta janela.

```text
Passos 1 a 5. Abrir a área, pesquisar o leitor, identificar o exemplar e informar a chave.
Passos 6e e 7. Registrar o empréstimo e ver a mensagem operação feita com sucesso.
Frame A - Registrar empréstimo
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

Não se conclui:
Exemplar não disponível.
Máximo em paralelo.
Segundo exemplar da mesma obra.
Leitor suspenso.
A data de retirada é a do momento.
A data prevista sai do prazo do leitor.
O título não identifica a obra.
A faixa etária indicada não impede.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Registrar empréstimo | Biblioteca Limoeiro, Acervo, Usuários, Empréstimos, Relatórios | barra | Topo da página | `F017` | Área atual: Empréstimos. As quatro áreas vêm da tela inicial. |
| Frame A - Registrar empréstimo | Registrar empréstimo | título da página | Abaixo da barra | `F017` | Passo 1. A página é a de registrar o empréstimo. |
| Frame A - Registrar empréstimo | Leitor | campo | Abaixo do título, vazio | `F017` | Passo 2. O gestor pesquisa o leitor. Sem leitor, o empréstimo não se conclui. `[RN-03]` |
| Frame A - Registrar empréstimo | Suspenso | rótulo | Ao lado do campo Leitor | `F017` | Passo 3a. Leitor suspenso: o empréstimo é recusado. A suspensão vale enquanto a duração informada na devolução atrasada não termina. `[RN-08]` |
| Frame A - Registrar empréstimo | Sem suspensão em vigor | rótulo | Ao lado de Suspenso | `F017` | Passo 3b. A suspensão não está em vigor e o registro pode seguir. Os dois rótulos são da própria tela. |
| Frame A - Registrar empréstimo | Código do exemplar | campo | Abaixo de Leitor, vazio | `F017` | Passo 4. Identifica o exemplar. O código não deriva de ISBN nem de outro dado externo. `[RN-09]` |
| Frame A - Registrar empréstimo | Ligar a suspensão | botão | Grupo Chave de suspensão, à esquerda | `F016` | Passo 5. Alternativa à outra chave. Fundo branco nesta página. Ligada, a devolução atrasada pode suspender. |
| Frame A - Registrar empréstimo | Desligar a suspensão | botão | Ao lado de Ligar a suspensão | `F016` | Passo 5. Alternativa. Fundo branco. Desligada, a devolução não suspende. A suspensão não começa quando o empréstimo passa a atrasado. |
| Frame A - Registrar empréstimo | Registrar empréstimo | botão | Abaixo da chave | `F017` | Passo 6e. Botão primário. O exemplar passa a emprestado e o empréstimo nasce ativo. |
| Frame A - Registrar empréstimo | operação feita com sucesso | linha | Abaixo do botão primário | `F017` | Passo 7. A conclusão grava o empréstimo e a chave e gera um log, com os dois resultados. `[RN-14]` |
| Fora do frame | Exemplar não disponível | texto | Abaixo da página | `F017` | Passos 6a e 6b. A retirada não se conclui. `[RN-04]` |
| Fora do frame | Máximo em paralelo | texto | Abaixo da página | `F017` | Passo 6c. Acima do máximo em vigor, não se conclui. Devolvido e Encerrado por extravio não entram. Ativo e atrasado entram. `[RN-05]` |
| Fora do frame | Segundo exemplar da mesma obra | texto | Abaixo da página | `F017` | Passo 6d. Não se conclui enquanto houver empréstimo em paralelo da mesma obra. `[RN-10]`, `[DEC-04]` |
| Fora do frame | Leitor suspenso | texto | Abaixo da página | `F017` | Passo 3a. O leitor suspenso não recebe empréstimo. `[RN-08]` |
| Fora do frame | A data de retirada é a do momento | texto | Abaixo da página | `F017` | A data de retirada é a do registro. `[RN-06]` |
| Fora do frame | A data prevista sai do prazo do leitor | texto | Abaixo da página | `F017` | A data prevista usa o prazo daquele leitor, conforme a lista e `F015`. `[RN-06]` descreve o prazo como configuração da biblioteca. Vale a lista. |
| Fora do frame | O título não identifica a obra | texto | Abaixo da página | `F017` | Duas obras podem ter o mesmo título. Isso não bloqueia a retirada. `[RN-10]`, `[DEC-04]` |
| Fora do frame | A faixa etária indicada não impede | texto | Abaixo da página | `F017` | A faixa etária indicada do brinquedo não bloqueia o empréstimo. `[DEC-05]` |

---

## 3. Estados da Interface

- **Estado vazio:** Os campos Leitor e Código do exemplar ficam sem texto neste esboço. Não há nome, CPF nem código simulado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Sem leitor e sem exemplar, o empréstimo não se conclui (`[RN-03]`). Leitor suspenso não recebe empréstimo (`[RN-08]`). Exemplar que não está disponível não sai (`[RN-04]`). Acima do máximo em vigor, não se conclui (`[RN-05]`). O segundo exemplar da mesma obra não sai (`[RN-10]`). A recusa sem gravação não gera log nem a mensagem de sucesso (`[RN-14]`). No passo 6a, a pessoa vê a data prevista mais próxima. No passo 6b, vê a mensagem de que o exemplar não está disponível para empréstimo, sem data. Esses dois textos não têm quadro nesta página.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas neste frame.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] A ordem em que as recusas são avaliadas está nos passos da lista. A lista fora do frame nomeia o conjunto, sem desenhar uma segunda página para cada recusa.
> - [ ] A chave é a de `F016`, nesta mesma página. A suspensão, quando a chave está ligada, inicia na devolução do exemplar atrasado (`F020`), não quando o status passa a atrasado (`F018`).
> - [ ] A data prevista pelo prazo do leitor segue a lista. `[RN-06]` ainda descreve o prazo como configuração da biblioteca.
