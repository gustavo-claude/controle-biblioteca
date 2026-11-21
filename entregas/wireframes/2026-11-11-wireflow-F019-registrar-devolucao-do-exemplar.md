# Wireflow: F019 Registrar devolução do exemplar

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F019` - Registrar devolução do exemplar
- **Passos de origem:** 1. Abrir a área de gestão de empréstimos. 2. Identificar o empréstimo ativo ou atrasado. 3. Se o empréstimo está atrasado e a chave de suspensão daquele empréstimo está ligada: 3a. Informar a duração da suspensão e seguir. Senão: 3b. Seguir sem duração. 4. Registrar a devolução do exemplar. 5. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-05]`, `[RN-07]`, `[RN-08]`, `[RN-14]`
- **Rodadas com o operador:** 6 de 6. Escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F019-registrar-devolucao-do-exemplar.svg`

No SVG, o título do frame, o passo e a seta ficam fora do retângulo. O retângulo é a página.

---

## 1. Wireflow em ASCII

Passo 1 - Abrir a área de gestão de empréstimos
Passo 2 - Identificar o empréstimo ativo ou atrasado

```text
+--------------------------------------------------------------+
| Frame A - Área de gestão de empréstimos                     |
|                                                              |
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Lista                                                        |
| Ativo              Atrasado                                  |
| ----------------------------------------------------------   |
|                                                              |
+--------------------------------------------------------------+
        |
        | reação: Registrar a devolução.
        v
Passo 3 - Se o empréstimo está atrasado e a chave daquele empréstimo está ligada, informar a duração. Senão, seguir sem duração.
Passo 4 - Registrar a devolução do exemplar
Passo 5 - Ver a mensagem operação feita com sucesso
+--------------------------------------------------------------+
| Frame B - Devolução                                          |
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
| [ Registrar a devolução ]                                    |
|                                                              |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+
```

Fora do retângulo, ao lado do campo Duração da suspensão:

- O campo só aparece se o empréstimo está atrasado e a chave daquele empréstimo está ligada.
- Se a chave está desligada, a devolução não pede duração.
- `[CONFIRMAR]` Se a devolução se conclui sem a duração quando a chave está ligada.

A seta só liga o frame A ao frame B. Os passos 3a e 3b não abrem outra página: mudam se o campo de duração aparece.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de empréstimos | Biblioteca Limoeiro | barra | Topo da página | `F019` | Página da área de gestão de empréstimos, aberta pela tela inicial. |
| Frame A - Área de gestão de empréstimos | Acervo, Usuários, Empréstimos, Relatórios | navegação | Barra, abaixo do nome | `F019` | As quatro áreas da tela inicial. Empréstimos é a área corrente. |
| Frame A - Área de gestão de empréstimos | Ativo | cabeçalho da lista | Lista, primeira coluna | `F019` | Passo 2. Empréstimo em aberto, dentro do prazo. Sem linha fictícia. |
| Frame A - Área de gestão de empréstimos | Atrasado | cabeçalho da lista | Lista, ao lado de Ativo | `F019` | Passo 2. A data prevista passou sem devolução. Sem linha fictícia. |
| Seta A para B | Registrar a devolução. | reação | Faixa entre os frames, fora dos retângulos | `F019` | Passo 4. Única seta. A ponta segue o trecho e não entra na página. |
| Frame B - Devolução | Identificação do empréstimo | campo vazio | Abaixo da barra | `F019` | Sem dado simulado. O gestor identifica o empréstimo ativo ou atrasado. |
| Frame B - Devolução | Devolvido | situação do empréstimo | Abaixo da identificação | `F019` | Resultado do passo 4, a partir de ativo ou atrasado. O empréstimo sai da conta do máximo. `[RN-05]` |
| Frame B - Devolução | Disponível | situação do exemplar | Abaixo de Devolvido | `F019` | A devolução devolve o exemplar a disponível. `[RN-07]` |
| Frame B - Devolução | Duração da suspensão | campo vazio | Abaixo das situações | `F019` | Passo 3a. Sem número e sem unidade. Só aparece se o empréstimo está atrasado e a chave daquele empréstimo está ligada. `[RN-08]` |
| Fora do retângulo | O campo só aparece se o empréstimo está atrasado e a chave daquele empréstimo está ligada. | texto | Ao lado do campo de duração | `F019` | A suspensão inicia nessa devolução. A passagem a atrasado não suspende o leitor. |
| Fora do retângulo | Se a chave está desligada, a devolução não pede duração. | texto | Ao lado do campo de duração | `F019` | Passo 3b. Essa devolução não suspende. |
| Fora do retângulo | [CONFIRMAR] Se a devolução se conclui sem a duração quando a chave está ligada. | texto | Ao lado do campo de duração | `F019` | Lacuna da lista, HU-19 e HU-20. |
| Frame B - Devolução | Registrar a devolução | botão | Abaixo do campo de duração | `F019` | Passo 4. Um log, com os dois resultados: empréstimo devolvido e exemplar disponível. `[RN-14]` |
| Frame B - Devolução | operação feita com sucesso | mensagem | Abaixo do botão | `F019` | Passo 5. A mensagem representa o log. Não há tela de log. |

---

## 3. Estados da Interface

- **Estado vazio:** A lista traz os cabeçalhos Ativo e Atrasado e não traz linhas. O campo de identificação e o campo de duração ficam vazios. `[CONFIRMAR]` O texto da página quando não há empréstimo ativo nem atrasado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** O campo de duração só entra na página se o empréstimo está atrasado e a chave daquele empréstimo está ligada. Com a chave desligada, a devolução não pede duração e não suspende. `[CONFIRMAR]` Se, com a chave ligada, a devolução se conclui sem a duração. Empréstimo devolvido não entra no máximo em paralelo. `[RN-05]`

---

## 4. Notas para o Operador

> Ajustes ainda abertos:
> - [ ] `[CONFIRMAR]` Se a devolução atrasada, com a chave ligada, se conclui sem a duração. F019 e F020.
> - [ ] `[CONFIRMAR]` O que a página mostra quando não há empréstimo ativo nem atrasado.
> - [ ] `[CONFIRMAR]` Carregamento e atualização da página.

Fechado neste wireflow, pelas escolhas do orquestrador no papel de operador:

- A página parte da área de gestão de empréstimos. A lista não usa linhas fictícias.
- A suspensão inicia na devolução do exemplar atrasado, se a chave daquele empréstimo estava ligada. A passagem automática a atrasado não suspende o leitor.
- Com a chave desligada, a devolução não pede duração e não suspende.
- O empréstimo fica devolvido e o exemplar volta a disponível. O histórico do exemplar permanece. Devolução não é suspensão nem extravio.
- A mensagem `operação feita com sucesso` fica na própria página. Um log, com os dois resultados. `[RN-14]`
- A lista prevalece sobre `[RN-08]` onde a regra trata ligar ou desligar como configuração da biblioteca. A chave é a daquele empréstimo.
