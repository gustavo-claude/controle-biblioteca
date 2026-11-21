# Wireflow: F024 Encerrar empréstimo por extravio do exemplar

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F024` - Encerrar empréstimo por extravio do exemplar
- **Passos de origem:** 1. Abrir a área de gestão de empréstimos. 2. Identificar o empréstimo ativo ou atrasado. 3. Encerrar o empréstimo por extravio. 4. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-05]`, `[RN-12]`, `[RN-13]`, `[RN-14]`
- **Rodadas com o operador:** 6 de 6. Escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F024-encerrar-emprestimo-por-extravio-do-exemplar.svg`

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
        | reação: Encerrar o empréstimo por extravio.
        v
Passo 3 - Encerrar o empréstimo por extravio
Passo 4 - Ver a mensagem operação feita com sucesso
+--------------------------------------------------------------+
| Frame B - Extravio                                           |
|                                                              |
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Empréstimo                                                   |
| [ Encerrado por extravio ]                                   |
|                                                              |
| Exemplar                                                     |
| [ Indisponível ]                                             |
|                                                              |
| [ Encerrar por extravio ]                                    |
|                                                              |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+
```

Fora do retângulo, ao lado das situações:

- Não volta a ativo, atrasado ou devolvido.
- Deixa de contar no máximo em paralelo.
- A remoção da obra e a do exemplar podem seguir.

A seta só liga o frame A ao frame B. Este wireflow não desenha a remoção.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de empréstimos | Biblioteca Limoeiro | barra | Topo da página | `F024` | Página da área de gestão de empréstimos, aberta pela tela inicial. |
| Frame A - Área de gestão de empréstimos | Acervo, Usuários, Empréstimos, Relatórios | navegação | Barra, abaixo do nome | `F024` | As quatro áreas da tela inicial. Empréstimos é a área corrente. |
| Frame A - Área de gestão de empréstimos | Ativo | cabeçalho da lista | Lista, primeira coluna | `F024` | Passo 2. Origem do encerramento. Sem linha fictícia. `[RN-13]` |
| Frame A - Área de gestão de empréstimos | Atrasado | cabeçalho da lista | Lista, ao lado de Ativo | `F024` | Passo 2. O empréstimo atrasado também pode ser encerrado por extravio. Sem linha fictícia. |
| Seta A para B | Encerrar o empréstimo por extravio. | reação | Faixa entre os frames, fora dos retângulos | `F024` | Passo 3. Única seta. Não há seta de volta. |
| Frame B - Extravio | Encerrado por extravio | situação do empréstimo | Abaixo da barra | `F024` | Status do empréstimo. Extravio não é status do exemplar. `[RN-13]` |
| Frame B - Extravio | Indisponível | situação do exemplar | Abaixo do empréstimo | `F024` | O exemplar emprestado passa a indisponível. `[RN-13]` |
| Frame B - Extravio | Encerrar por extravio | botão | Abaixo das situações | `F024` | Passo 3. Um log, com os dois resultados: empréstimo e exemplar. `[RN-14]` |
| Frame B - Extravio | operação feita com sucesso | mensagem | Abaixo do botão | `F024` | Passo 4. A mensagem representa o log. Não há tela de log. |
| Fora do retângulo | Não volta a ativo, atrasado ou devolvido. | texto | Ao lado das situações | `F024` | Não há passagem de Encerrado por extravio para ativo, atrasado ou devolvido. O empréstimo atrasado também não volta a ativo. |
| Fora do retângulo | Deixa de contar no máximo em paralelo. | texto | Ao lado das situações | `F024` | Empréstimo Encerrado por extravio fica fora da conta. `[RN-05]` |
| Fora do retângulo | A remoção da obra e a do exemplar podem seguir. | texto | Ao lado das situações | `F024` | A remoção não se conclui enquanto o exemplar está emprestado. Depois deste encerramento, pode ser feita. Este frame não executa a remoção. `[RN-12]`, `[RN-13]` |

---

## 3. Estados da Interface

- **Estado vazio:** A lista traz os cabeçalhos Ativo e Atrasado e não traz linhas. `[CONFIRMAR]` O texto da página quando nenhum empréstimo ativo ou atrasado foi identificado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** O encerramento parte de empréstimo ativo ou atrasado. O resultado fica Encerrado por extravio e o exemplar fica indisponível. Não volta a ativo, atrasado ou devolvido. Deixa de contar no máximo em paralelo. `[CONFIRMAR]` A reação quando o empréstimo não está ativo nem atrasado.

---

## 4. Notas para o Operador

> Ajustes ainda abertos:
> - [ ] `[CONFIRMAR]` O que a página mostra quando nenhum empréstimo ativo ou atrasado foi identificado.
> - [ ] `[CONFIRMAR]` Carregamento e atualização da página.
> - [ ] `[CONFIRMAR]` A reação quando o empréstimo não está ativo nem atrasado.

Fechado neste wireflow, pelas escolhas do orquestrador no papel de operador:

- A página parte da área de gestão de empréstimos. A lista não usa linhas fictícias.
- O empréstimo fica Encerrado por extravio. O exemplar fica indisponível. Extravio não é status do exemplar.
- Não volta a ativo, atrasado ou devolvido. Não há seta de volta.
- Deixa de contar no máximo em paralelo.
- A remoção da obra e a do exemplar podem seguir. Este wireflow não desenha essas remoções.
- A mensagem `operação feita com sucesso` fica na própria página. Um log, com os dois resultados. `[RN-14]`
