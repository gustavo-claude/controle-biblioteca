# Wireflow: F020 Informar duração da suspensão do leitor

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F020` - Informar duração da suspensão do leitor
- **Passos de origem:** 1. Receber o exemplar do empréstimo atrasado, na devolução. 2. Se a chave de suspensão daquele empréstimo está desligada: 2a. Encerrar sem suspensão. Senão: 2b. Informar a duração da suspensão. 3. Ver o leitor suspenso por essa duração. 4. Ver a mensagem operação feita com sucesso, quando a duração é informada.
- **Regras vinculadas:** `[RN-07]`, `[RN-08]`, `[RN-14]`, `[DEC-03]`
- **Rodadas com o operador:** 5 de 5. Escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F020-informar-duracao-da-suspensao-do-leitor.svg`

No SVG, o título do frame, o passo e a seta ficam fora do retângulo. O retângulo é a mesma página de devolução. Não há tela própria.

---

## 1. Wireflow em ASCII

A seta não liga duas telas. Nomeia a entrada nesta página.

```text
        |
        | reação: Receber o exemplar atrasado com a chave ligada.
        v
Passo 1 - Receber o exemplar do empréstimo atrasado, na devolução
Passo 2a - Se a chave está desligada, encerrar sem suspensão. Esta funcionalidade não ocorre.
Passo 2b - Informar a duração da suspensão
Passo 3 - Ver o leitor suspenso por essa duração
Passo 4 - Ver a mensagem operação feita com sucesso, quando a duração é informada
+--------------------------------------------------------------+
| Frame A - Devolução                                          |
|                                                              |
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Identificação do empréstimo                                  |
| [                                                            ] |
|                                                              |
| Empréstimo                                                   |
| [ Devolvido ]                                                |
|                                                              |
| Exemplar                                                     |
| [ Disponível ]                                               |
|                                                              |
| Duração da suspensão                                         |
| [                                                            ] |
|                                                              |
| Leitor suspenso                                              |
|                                                              |
| [ Registrar a devolução ]                                    |
|                                                              |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+
```

Fora do retângulo, ao lado do campo Duração da suspensão:

- Não há quantidade fixa de dias.
- O leitor fica suspenso.
- Nenhum gestor registra novo empréstimo enquanto a suspensão vale.
- Não há tela própria.

O campo não traz número nem unidade. O passo 2a não abre outra página.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Seta de entrada | Receber o exemplar atrasado com a chave ligada. | reação | Fora, acima do frame | `F020` | Passo 1. A suspensão inicia nessa devolução, se a chave daquele empréstimo estava ligada. Não há segunda tela. |
| Frame A - Devolução | Biblioteca Limoeiro | barra | Topo da página | `F020` | A mesma página de devolução de F019, na área de gestão de empréstimos. |
| Frame A - Devolução | Acervo, Usuários, Empréstimos, Relatórios | navegação | Barra, abaixo do nome | `F020` | Empréstimos é a área corrente. |
| Frame A - Devolução | Identificação do empréstimo | campo vazio | Abaixo da barra | `F020` | Sem dado simulado. O recebimento é o do exemplar atrasado. |
| Frame A - Devolução | Devolvido | situação do empréstimo | Abaixo da identificação | `F020` | A duração é informada na devolução. O empréstimo fica devolvido. |
| Frame A - Devolução | Disponível | situação do exemplar | Abaixo de Devolvido | `F020` | O exemplar volta a disponível na mesma página. `[RN-07]` |
| Frame A - Devolução | Duração da suspensão | campo vazio em destaque | Abaixo das situações | `F020` | Passo 2b. Sem quantidade fixa de dias e sem unidade. `[RN-08]`, `[DEC-03]` |
| Frame A - Devolução | Leitor suspenso | condição do leitor | Abaixo do campo de duração | `F020` | Passo 3. Suspensão é condição do leitor, não status do exemplar nem do empréstimo. |
| Frame A - Devolução | Registrar a devolução | botão | Abaixo da condição do leitor | `F020` | A ação é a da página de devolução. Informar a duração gera log. `[RN-14]` |
| Frame A - Devolução | operação feita com sucesso | mensagem | Abaixo do botão | `F020` | Passo 4. Só quando a duração é informada. A mensagem representa o log. |
| Fora do retângulo | Não há quantidade fixa de dias. | texto | Ao lado do campo de duração | `F020` | O campo não mostra número. `[RN-08]`, `[DEC-03]` |
| Fora do retângulo | O leitor fica suspenso. | texto | Ao lado do campo de duração | `F020` | Passo 3. A suspensão encerra sozinha ao fim da duração. Esse fim é F021 e não gera log. |
| Fora do retângulo | Nenhum gestor registra novo empréstimo enquanto a suspensão vale. | texto | Ao lado do campo de duração | `F020` | Enquanto a suspensão vale, F017 não se conclui para esse leitor. `[RN-08]` |
| Fora do retângulo | Não há tela própria. | texto | Ao lado do campo de duração | `F020` | F020 não ganha frame isolado. O efeito fica na devolução. |

---

## 3. Estados da Interface

- **Estado vazio:** O campo Duração da suspensão aparece sem número e sem unidade. A identificação do empréstimo fica vazia.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Se a chave daquele empréstimo está desligada, esta funcionalidade não ocorre e a devolução não pede duração. Com a chave ligada, o gestor informa a duração na devolução do exemplar atrasado. Enquanto a suspensão vale, nenhum gestor registra novo empréstimo para esse leitor. `[CONFIRMAR]` Se a devolução atrasada, com a chave ligada, se conclui sem a duração.

---

## 4. Notas para o Operador

> Ajustes ainda abertos:
> - [ ] `[CONFIRMAR]` Se a devolução atrasada, com a chave ligada, se conclui sem a duração. F019 e F020.
> - [ ] `[CONFIRMAR]` Carregamento e atualização da página.

Fechado neste wireflow, pelas escolhas do orquestrador no papel de operador:

- Não há tela própria. A duração fica na mesma página de devolução.
- A suspensão inicia na devolução do exemplar atrasado, se a chave daquele empréstimo estava ligada. Não inicia na passagem automática a atrasado.
- Não há quantidade fixa de dias. O leitor fica suspenso pela duração informada.
- Nenhum gestor registra novo empréstimo enquanto a suspensão vale.
- Informar a duração gera log. O fim automático da suspensão não gera log e não mostra a mensagem. `[RN-14]`
- A lista prevalece sobre `[RN-08]` e `[DEC-03]` onde a chave é tratada como configuração da biblioteca. A chave é a daquele empréstimo.
