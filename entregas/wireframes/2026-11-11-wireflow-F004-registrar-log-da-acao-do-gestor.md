# Wireflow: F004 Registrar log da ação do gestor

- **Persona que executa os passos:** O sistema
- **Funcionalidade:** `F004` - Registrar log da ação do gestor
- **Passos de origem:** 1. Concluir uma ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório. 2. Se a ação é consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim da suspensão ou criação do primeiro gestor: 2a. Encerrar sem log e sem a mensagem. Senão: 2b. Registrar o log da ação, sem a senha. 3. Mostrar, na tela da ação, a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-14]`
- **Rodadas com o operador:** 2 de 2, escolhas do orquestrador no papel de operador
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F004-registrar-log-da-acao-do-gestor.svg`

---

## 1. Wireflow em ASCII

Não há tela de log. Frame único: a mensagem aparece na tela da ação. Sem seta.

Frame A - Ação concluída
Passo 1 - Concluir uma ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório
Passo 2b - Registrar o log da ação, sem a senha
Passo 3 - Mostrar, na tela da ação, a mensagem operação feita com sucesso

```text
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| Acervo | Usuários | Empréstimos | Relatórios                |
|                                                              |
| operação feita com sucesso                                   |
|                                                              |
| [ Concluir ]                                                 |
+--------------------------------------------------------------+
```

Fora do retângulo:

O log guarda data e hora, o gestor, a ação, o que mudou, a identificação, o valor anterior e o valor novo.
Na inclusão, o valor anterior fica vazio.
Na remoção, o valor novo é a remoção.
No relatório, guarda o recorte e não guarda valor anterior nem novo.
A senha não entra.
Uma ação que altera exemplar e empréstimo gera um log, com os dois resultados.
Sem esta mensagem: consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim da suspensão e criação do primeiro gestor.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Fora do retângulo | Frame A - Ação concluída | Título do frame | Acima da página, à esquerda | `F004` | Janela única. Não é tela de log |
| Fora do retângulo | Passo 1 - Concluir uma ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório | Passo | Abaixo do título, fora da página | `F004` | Ação que altera cadastro, configuração, status ou que emite relatório |
| Fora do retângulo | Passo 2b - Registrar o log da ação, sem a senha | Passo | Abaixo do passo 1, fora da página | `F004` | O sistema grava o log. A senha não entra |
| Fora do retângulo | Passo 3 - Mostrar, na tela da ação, a mensagem operação feita com sucesso | Passo | Abaixo do passo 2b, fora da página | `F004` | A mensagem fica na tela da ação |
| Frame A - Ação concluída | Biblioteca Limoeiro | Barra | Topo da página | `F004` | Barra do gestor autenticado |
| Frame A - Ação concluída | Acervo, Usuários, Empréstimos, Relatórios | Barra | Abaixo do nome, na mesma página | `F004` | As quatro áreas da tela inicial. Nenhuma em destaque: a conclusão não é a área de relatórios |
| Frame A - Ação concluída | operação feita com sucesso | Linha | Única linha de conteúdo, abaixo da barra | `F004` | Passo 3. Representa que os dados foram salvos no log. `[RN-14]` |
| Frame A - Ação concluída | Concluir | Botão primário | Abaixo da mensagem | `F004` | Botão de conclusão já usado na tela da ação |
| Fora do retângulo | O log guarda data e hora, o gestor, a ação, o que mudou, a identificação, o valor anterior e o valor novo | Texto | Abaixo da página | `F004` | Conteúdo do log. Não aparece como campo na página. `[RN-14]` |
| Fora do retângulo | Na inclusão, o valor anterior fica vazio | Texto | Abaixo da página | `F004` | `[RN-14]` |
| Fora do retângulo | Na remoção, o valor novo é a remoção | Texto | Abaixo da página | `F004` | `[RN-14]` |
| Fora do retângulo | No relatório, guarda o recorte e não guarda valor anterior nem novo | Texto | Abaixo da página | `F004` | `[RN-14]` |
| Fora do retângulo | A senha não entra | Texto | Abaixo da página | `F004` | `[RN-14]` |
| Fora do retângulo | Uma ação que altera exemplar e empréstimo gera um log, com os dois resultados | Texto | Abaixo da página | `F004` | `[RN-14]` |
| Fora do retângulo | Sem esta mensagem: consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim da suspensão e criação do primeiro gestor | Texto | Abaixo da página | `F004` | Passo 2a. Encerrar sem log e sem a mensagem |

---

## 3. Estados da Interface

- **Estado vazio:** Na inclusão, o valor anterior fica vazio. Isso é do log, fora da página. `[CONFIRMAR]` A página de conclusão não tem outro estado vazio definido.
- **Carregamento / atualização:** `[CONFIRMAR]` O passo e a regra não definem carregamento.
- **Bloqueios e restrições:** A ação listada não se conclui sem o log (`[RN-14]`). Consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim da suspensão e a criação do primeiro gestor não geram log e não mostram a mensagem.

---

## 4. Notas para o Operador

Escolhas do orquestrador no papel de operador. Rodada 1: barra do gestor, sem área em destaque. Rodada 2: página de conclusão com a linha operação feita com sucesso e o botão Concluir. Os campos do log ficam fora da página.

> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Para onde o botão Concluir leva. O passo não descreve outro destino.
> - [ ] `[CONFIRMAR]` Carregamento desta página.
