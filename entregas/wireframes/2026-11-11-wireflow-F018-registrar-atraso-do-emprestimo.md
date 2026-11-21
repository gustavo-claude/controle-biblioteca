# Wireflow: F018 Registrar atraso do empréstimo

- **Persona que executa os passos:** O sistema
- **Funcionalidade:** `F018` - Registrar atraso do empréstimo
- **Passos de origem:** 1. Passar o empréstimo de ativo a atrasado quando a data prevista chega sem devolução. 2. Mostrar o status atrasado na lista de empréstimos.
- **Regras vinculadas:** `[RN-08]`, `[RN-14]`, `[DEC-03]`
- **Rodadas com o operador:** 2 de 2, escolhas do orquestrador no papel de operador: Lista antes; Lista depois.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F018-registrar-atraso-do-emprestimo.svg`

Escolhas do orquestrador no papel de operador. Não há tela própria. Os dois frames são a lista de `F025`, antes e depois.

---

## 1. Wireflow em ASCII

```text
Passo 1. Passar o empréstimo de ativo a atrasado quando a data prevista chega sem devolução.
Frame A - Lista antes
+------------------------------------------------------------------+
| Biblioteca Limoeiro | Acervo | Usuários | Empréstimos | Relatórios |
|                                                                  |
| Empréstimos                          [ Registrar empréstimo ]    |
|                                                                  |
| Ativo                                                            |
| [ Empréstimo ]                                                   |
| Devolvido                                                        |
| Atrasado                                                         |
| Encerrado por extravio                                           |
+------------------------------------------------------------------+
        |
        | A data prevista chegou sem devolução.
        v
Passo 2. Mostrar o status atrasado na lista de empréstimos.
Frame B - Lista depois
+------------------------------------------------------------------+
| Biblioteca Limoeiro | Acervo | Usuários | Empréstimos | Relatórios |
|                                                                  |
| Empréstimos                          [ Registrar empréstimo ]    |
|                                                                  |
| Ativo                                                            |
| Devolvido                                                        |
| Atrasado                                                         |
| [ Empréstimo ]                                                   |
| Encerrado por extravio                                           |
+------------------------------------------------------------------+

O exemplar segue emprestado.
O empréstimo atrasado não volta a ativo.
Não suspende o leitor.
Não gera log.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Lista antes | Biblioteca Limoeiro, Acervo, Usuários, Empréstimos, Relatórios | barra | Topo da página | `F025` | Área atual: Empréstimos. A lista é a base de `F025`. |
| Frame A - Lista antes | Empréstimos | título da página | Abaixo da barra | `F025` | Título da lista base. |
| Frame A - Lista antes | Registrar empréstimo | botão | À direita do título | `F017` | Botão da lista base. Não é ação de atraso. |
| Frame A - Lista antes | Ativo | cabeçalho de seção | Primeira seção | `F025` | O empréstimo ainda está ativo. Status oficial. |
| Frame A - Lista antes | Empréstimo | marca da seção | Dentro de Ativo | `F018` | O mesmo empréstimo, sem nome, código nem data. Passo 1 ainda não ocorreu. |
| Frame A - Lista antes | Devolvido | cabeçalho de seção | Abaixo de Ativo | `F025` | Seção da lista base, sem linha. |
| Frame A - Lista antes | Atrasado | cabeçalho de seção | Abaixo de Devolvido, vazia | `F018` | Antes da data prevista, esta seção não mostra esse empréstimo. |
| Frame A - Lista antes | Encerrado por extravio | cabeçalho de seção | Última seção | `F025` | Seção da lista base, sem linha. |
| Seta A para B | A data prevista chegou sem devolução | seta | Fora, entre as páginas | `F018` | Passo 1. O sistema muda o empréstimo de ativo para atrasado. |
| Frame B - Lista depois | Biblioteca Limoeiro, Acervo, Usuários, Empréstimos, Relatórios | barra | Topo da página | `F025` | A mesma área de empréstimos. |
| Frame B - Lista depois | Empréstimos | título da página | Abaixo da barra | `F025` | A mesma lista. |
| Frame B - Lista depois | Registrar empréstimo | botão | À direita do título | `F017` | Permanece. Não há botão de atraso. |
| Frame B - Lista depois | Ativo | cabeçalho de seção | Primeira seção, sem a marca | `F018` | O empréstimo saiu de ativo. Não há volta de atrasado para ativo. |
| Frame B - Lista depois | Devolvido | cabeçalho de seção | Abaixo de Ativo | `F025` | Sem linha. |
| Frame B - Lista depois | Atrasado | cabeçalho de seção | Abaixo de Devolvido | `F018` | Passo 2. O status atrasado aparece aqui. |
| Frame B - Lista depois | Empréstimo | marca da seção | Dentro de Atrasado | `F018` | O mesmo empréstimo do frame A. |
| Frame B - Lista depois | Encerrado por extravio | cabeçalho de seção | Última seção | `F025` | Sem linha. |
| Fora dos frames | O exemplar segue emprestado | texto | Abaixo da segunda página | `F018` | A situação do exemplar continua emprestado. |
| Fora dos frames | O empréstimo atrasado não volta a ativo | texto | Abaixo da segunda página | `F018` | Não há essa passagem. |
| Fora dos frames | Não suspende o leitor | texto | Abaixo da segunda página | `F018` | Atraso não é suspensão. A suspensão, se a chave estiver ligada, inicia na devolução do exemplar atrasado. `[RN-08]`, `[DEC-03]` |
| Fora dos frames | Não gera log | texto | Abaixo da segunda página | `F018` | A passagem feita pelo sistema não gera log e não mostra operação feita com sucesso. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** No frame A, a seção Atrasado não tem o empréstimo. No frame B, a seção Ativo não tem esse empréstimo. Devolvido e Encerrado por extravio ficam só com o cabeçalho.
- **Carregamento / atualização:** A atualização é a própria passagem de ativo a atrasado, desenhada pela seta. Não há mensagem de sucesso.
- **Bloqueios e restrições:** O exemplar segue emprestado. O empréstimo atrasado não volta a ativo. O sistema não suspende o leitor neste passo. Não gera log.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas nestes frames.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Se a lista, no momento da passagem, mostra outros empréstimos além deste. Este esboço não desenha linhas fictícias.
> - [ ] A marca "Empréstimo" não é um leitor, um código nem uma data. Serve para mostrar o mesmo registro nas duas seções.
> - [ ] Quem executa os passos é o sistema, como na lista. O gestor só vê o efeito na lista de `F025`.
