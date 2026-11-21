# Wireflow: F023 Registrar retorno a disponibilidade do exemplar

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F023` - Registrar retorno a disponibilidade do exemplar
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Identificar o exemplar indisponível. 3. Se o exemplar não está indisponível: 3a. Recusar o retorno e permanecer na área. Senão: 3b. Registrar o retorno a disponibilidade. 4. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-13]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador: Área de acervo; Identificação e situação; Ação; Mensagem de sucesso.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F023-registrar-retorno-a-disponibilidade-do-exemplar.svg`

---

## 1. Wireflow em ASCII

Passo 1 - Abrir a área de gestão do acervo

```text
+----------------------------------------------------------+
| Frame A - Área de gestão do acervo                       |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Acervo                                                   |
| Tipo              Título ou nome                         |
| -------------------------------------------------------- |
|                                                          |
+----------------------------------------------------------+
        |
        | Registrar o retorno a disponibilidade
        v
```

Passo 2 - Identificar o exemplar indisponível
Passo 3b - Registrar o retorno a disponibilidade
Passo 4 - Ver a mensagem operação feita com sucesso

```text
+----------------------------------------------------------+
| Frame B - Retorno a disponibilidade                      |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Retorno a disponibilidade                                |
| Código do exemplar      [                              ] |
| Situação                                                 |
| Indisponível                                             |
| [Registrar o retorno a disponibilidade]                  |
| operação feita com sucesso                               |
+----------------------------------------------------------+
```

O passo 3a não abre outro frame. A devolução de exemplar emprestado não é este retorno.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro | barra | Topo da página | `F023` | Barra do gestor. A área atual é Acervo. |
| Frame A - Área de gestão do acervo | Acervo | título da página | Abaixo da barra | `F023` | Passo 1. Área de gestão do acervo. |
| Frame A - Área de gestão do acervo | Tipo | cabeçalho | Lista, coluna esquerda | `F023` | Cabeçalho da lista. Sem dado simulado. |
| Frame A - Área de gestão do acervo | Título ou nome | cabeçalho | Lista, ao lado de Tipo | `F023` | Cabeçalho da lista. Sem dado simulado. |
| Seta A para B | Registrar o retorno a disponibilidade | seta | Faixa entre A e B | `F023` | Reação do passo 3b. A volta do indisponível a disponível. `[RN-13]` |
| Frame B - Retorno a disponibilidade | Código do exemplar | campo | Abaixo do título, vazio | `F023` | Passo 2. Identifica o exemplar indisponível. Sem valor neste esboço. |
| Frame B - Retorno a disponibilidade | Indisponível | situação | Abaixo do código | `F023` | Situação de partida. O retorno parte do indisponível. `[RN-13]` |
| Frame B - Retorno a disponibilidade | Registrar o retorno a disponibilidade | botão | Abaixo da situação | `F023` | Passo 3b. O exemplar volta a disponível por este gesto. `[RN-13]` |
| Frame B - Retorno a disponibilidade | operação feita com sucesso | mensagem | Abaixo do botão | `F023` | Passo 4. A ação concluída gera log. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** `[CONFIRMAR]` O que a página mostra quando nenhum exemplar foi identificado. O código deste esboço fica vazio porque não há dado simulado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Se o exemplar não está indisponível, o retorno não se conclui e não há mensagem. A recusa não gera log. `[RN-14]` A devolução de exemplar emprestado não é este retorno: é `F019`. A volta do indisponível a disponível é este gesto. `[RN-13]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas nos frames acima.
>
> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` O que a página mostra quando nenhum exemplar foi identificado.
> - [ ] `[CONFIRMAR]` O que a página mostra quando o código não corresponde a um exemplar.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] A devolução de emprestado não é este retorno.
