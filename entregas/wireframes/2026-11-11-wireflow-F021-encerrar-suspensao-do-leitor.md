# Wireflow: F021 Encerrar suspensão do leitor

- **Persona que executa os passos:** O sistema
- **Funcionalidade:** `F021` - Encerrar suspensão do leitor
- **Passos de origem:** 1. Encerrar a suspensão do leitor ao fim da duração informada. 2. Na pesquisa do leitor para novo empréstimo, distinguir esse leitor do leitor suspenso. 3. Permitir registrar o empréstimo para o leitor cuja suspensão encerrou.
- **Regras vinculadas:** `[RN-08]`, `[RN-14]`, `[DEC-03]`
- **Rodadas com o operador:** 2 de 2, escolhas do orquestrador no papel de operador: Pesquisa do leitor; Situação da suspensão.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F021-encerrar-suspensao-do-leitor.svg`

Escolhas do orquestrador no papel de operador. Um frame só. Sem seta: não há outra página. A tela é a pesquisa do leitor de `F017`.

---

## 1. Wireflow em ASCII

Sem seta: os passos exibem conteúdo nesta janela.

```text
Passo 1. Encerrar a suspensão do leitor ao fim da duração informada.
Passo 2. Na pesquisa do leitor, distinguir o suspenso de quem já encerrou a suspensão.
Passo 3. Permitir o empréstimo para o leitor cuja suspensão encerrou.
Frame A - Pesquisa do leitor
+------------------------------------------------------------------+
| Biblioteca Limoeiro | Acervo | Usuários | Empréstimos | Relatórios |
|                                                                  |
| Registrar empréstimo                                             |
|                                                                  |
| Leitor                                                           |
| [                          ]                                     |
| [ Suspenso (empréstimo não segue) ]                              |
| [ Suspensão encerrada (empréstimo pode seguir) ]                 |
+------------------------------------------------------------------+

Sem seta: não há outra página.
O sistema encerra a suspensão ao fim da duração, sem tela própria e sem log.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Pesquisa do leitor | Biblioteca Limoeiro, Acervo, Usuários, Empréstimos, Relatórios | barra | Topo da página | `F017` | A pesquisa do leitor fica na página de registrar o empréstimo. Área atual: Empréstimos. |
| Frame A - Pesquisa do leitor | Registrar empréstimo | título da página | Abaixo da barra | `F017` | Mesma tela de pesquisa do leitor de `F017`. Não é uma tela de fim da suspensão. |
| Frame A - Pesquisa do leitor | Leitor | campo | Abaixo do título, vazio | `F017` | Passo 2. O gestor pesquisa o leitor para um empréstimo novo. O campo fica sem texto neste esboço. |
| Frame A - Pesquisa do leitor | Suspenso (empréstimo não segue) | rótulo | Ao lado do campo Leitor | `F021` | Passo 2. O leitor suspenso se distingue do outro. O empréstimo não segue. `[RN-08]` |
| Frame A - Pesquisa do leitor | Suspensão encerrada (empréstimo pode seguir) | rótulo | Abaixo do rótulo Suspenso | `F021` | Passos 2 e 3. O leitor cuja suspensão encerrou se distingue do suspenso, e o empréstimo pode seguir. |
| Fora do frame | O sistema encerra a suspensão ao fim da duração, sem tela própria e sem log | texto | Abaixo da página | `F021` | Passo 1. Não há novo ato do gestor. Não gera log. `[RN-08]`, `[RN-14]`, `[DEC-03]` |

---

## 3. Estados da Interface

- **Estado vazio:** O campo Leitor fica sem texto. Os dois rótulos permanecem visíveis na pesquisa.
- **Carregamento / atualização:** `[CONFIRMAR]` O fim da suspensão não tem tela de atualização.
- **Bloqueios e restrições:** Enquanto a suspensão vale, o empréstimo não segue. Ao fim da duração, o sistema encerra a suspensão e o empréstimo pode seguir. Esse fim não gera log e não mostra operação feita com sucesso.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas neste frame.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Carregamento e atualização da pesquisa.
> - [ ] Quem executa o passo 1 é o sistema. O efeito visível é a pesquisa do leitor em `F017`.
> - [ ] A duração foi informada na devolução do exemplar atrasado, quando a chave daquele empréstimo estava ligada (`F016`, `F020`). O atraso automático não inicia a suspensão.
