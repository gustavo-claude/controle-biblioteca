# Wireflow: F025 Consultar lista dos empréstimos

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F025` - Consultar lista dos empréstimos
- **Passos de origem:** 1. Se a consulta parte da área de gestão de empréstimos: 1a. Ver os empréstimos ativos, devolvidos, atrasados e encerrados por extravio. Senão: 1b. Abrir a área de relatórios e ver o recorte dos leitores com empréstimo ativo. 2. Se o sistema passou um empréstimo de ativo a atrasado: 2a. Ver esse empréstimo como atrasado na lista.
- **Regras vinculadas:** `[RN-14]`
- **Rodadas com o operador:** 3 de 3, escolhas do orquestrador no papel de operador: Barra da área; Lista na área de empréstimos; Recorte nos relatórios.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F025-consultar-lista-dos-emprestimos.svg`

Escolhas do orquestrador no papel de operador. As setas são alternativas. Não há sequência de um frame para o outro.

---

## 1. Wireflow em ASCII

```text
Passo 1a. Ver os empréstimos ativos, devolvidos, atrasados e encerrados por extravio.
Frame A - Área de gestão de empréstimos
                         ou
Passo 1b. Abrir a área de relatórios e ver o recorte dos leitores com empréstimo ativo.
Frame B - Recorte nos relatórios

        | Área de empréstimos          | Área de relatórios
        v                              v
+--------------------------------+   +--------------------------------+
| Biblioteca Limoeiro            |   | Biblioteca Limoeiro            |
| Acervo | Usuários | Empréstimos | Relatórios                      |
|                                |   | Acervo | Usuários | Empréstimos | Relatórios
| Empréstimos                    |   |                                |
| [ Registrar empréstimo ]       |   | Leitores com empréstimo ativo  |
|                                |   |                                |
| Ativo          | Devolvido     |   | Ativo                          |
| Atrasado       | Encerrado por |   |                                |
|                | extravio      |   |                                |
+--------------------------------+   +--------------------------------+

A consulta não gera log.
A lista não é o painel dos 6 meses.
Se o sistema passou um empréstimo de ativo a atrasado, a lista mostra o status atrasado.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Seta para o frame A | Área de empréstimos | seta | Fora, acima da página, alternativa | `F025` | Passo 1a. A consulta parte da área de gestão de empréstimos. Não é o passo seguinte ao frame B. |
| Seta para o frame B | Área de relatórios | seta | Fora, acima da outra página, alternativa | `F025` | Passo 1b. Senão, abre a área de relatórios. O texto entre as setas é "ou". |
| Frame A - Área de gestão de empréstimos | Biblioteca Limoeiro, Acervo, Usuários, Empréstimos, Relatórios | barra | Topo da página | `F025` | Área atual: Empréstimos. |
| Frame A - Área de gestão de empréstimos | Empréstimos | título da página | Abaixo da barra | `F025` | Título da lista base. |
| Frame A - Área de gestão de empréstimos | Registrar empréstimo | botão | À direita do título | `F017` | Ação da lista na área de empréstimos. Botão primário. |
| Frame A - Área de gestão de empréstimos | Ativo | cabeçalho de seção | Primeira seção, sem linha | `F025` | Status oficial do empréstimo em aberto, dentro do prazo. |
| Frame A - Área de gestão de empréstimos | Devolvido | cabeçalho de seção | Ao lado de Ativo, sem linha | `F025` | Status oficial. |
| Frame A - Área de gestão de empréstimos | Atrasado | cabeçalho de seção | Abaixo de Ativo, sem linha | `F025` | Status oficial. O passo 2a mostra aqui o empréstimo que `F018` passou de ativo a atrasado. |
| Frame A - Área de gestão de empréstimos | Encerrado por extravio | cabeçalho de seção | Ao lado de Atrasado, sem linha | `F025` | Status oficial. |
| Frame B - Recorte nos relatórios | Biblioteca Limoeiro, Acervo, Usuários, Empréstimos, Relatórios | barra | Topo da página | `F025` | Área atual: Relatórios. |
| Frame B - Recorte nos relatórios | Leitores com empréstimo ativo | título da página | Abaixo da barra | `F025` | Passo 1b. O recorte troca o título da lista. |
| Frame B - Recorte nos relatórios | Ativo | cabeçalho de seção | Abaixo do título, sem linha | `F025` | A mesma lista, só com a seção Ativo. |
| Fora dos frames | A consulta não gera log | texto | Abaixo das páginas | `F025` | Consulta não gera log e não mostra operação feita com sucesso. `[RN-14]` |
| Fora dos frames | A lista não é o painel dos 6 meses | texto | Abaixo das páginas | `F025` | Leitor com empréstimo nos últimos 6 meses é quantidade do painel (`F028`), não este recorte. |
| Fora dos frames | Se o sistema passou um empréstimo de ativo a atrasado, a lista mostra o status atrasado | texto | Abaixo das páginas | `F025` | Passo 2a. O antes e o depois dessa passagem estão em `F018`. Não há terceira página. |

---

## 3. Estados da Interface

- **Estado vazio:** As seções aparecem só com o cabeçalho. Não há linha de empréstimo neste esboço.
- **Carregamento / atualização:** `[CONFIRMAR]` A consulta não mostra mensagem de sucesso.
- **Bloqueios e restrições:** A consulta não gera log (`[RN-14]`). O recorte dos relatórios não substitui o painel dos 6 meses.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas nestes frames.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Carregamento e atualização da consulta.
> - [ ] O botão Registrar empréstimo fica na área de empréstimos. O recorte dos relatórios mostra o título novo e a seção Ativo.
> - [ ] O passo 2a não abre frame. A mudança de ativo para atrasado é o wireflow de `F018`, nesta mesma lista.
