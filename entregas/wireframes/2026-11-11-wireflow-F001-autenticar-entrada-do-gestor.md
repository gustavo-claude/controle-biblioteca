# Wireflow: F001 Autenticar entrada do gestor

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F001` - Autenticar entrada do gestor
- **Passos de origem:** 1. Informar o usuário. 2. Informar a senha. 3. Se a senha está errada: 3a. Ver a mensagem de senha errada e permanecer na tela de login. Senão, se o usuário não está cadastrado: 3b. Ver a mensagem de usuário não cadastrado e permanecer na tela de login. Senão: 3c. Abrir a tela inicial.
- **Regras vinculadas:** `RN-02`, `RN-14`
- **Rodadas com o operador:** Escolhas do orquestrador no papel de operador
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F001-autenticar-entrada-do-gestor.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Dentro dele fica só o que a pessoa vê. Título do frame, passo e texto da seta ficam fora. A seta corre na faixa entre as páginas e a ponta toca a borda do Frame B. Os passos 3a e 3b permanecem na tela de login e não têm seta.

Frame A - Tela de login
Passo 1 - Informar o usuário
Passo 2 - Informar a senha
Passo 3a - Ver a mensagem de senha errada e permanecer na tela de login
Passo 3b - Ver a mensagem de usuário não cadastrado e permanecer na tela de login

```text
+----------------------------------+
| Login                            |
|                                  |
| Usuário                          |
| [                              ] |
| Senha                            |
| [                              ] |
| [ Entrar ]                       |
| ______                           |
+----------------------------------+
                                        Senha errada.
                                        Usuário não cadastrado.
        |
        | Usuário e senha autorizam a entrada.
        v
Frame B - Tela inicial
Passo 3c - Abrir a tela inicial
+----------------------------------+
| Tela inicial                     |
|                                  |
| [ Acervo ]       [ Usuários ]    |
|                                  |
| [ Empréstimos ]  [ Relatórios ]  |
+----------------------------------+
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Tela de login | Login | Título da tela | Topo da página | `F001` | Rótulo que a pessoa vê. Sem barra de áreas |
| Frame A - Tela de login | Usuário | Campo vazio | Abaixo do título | `F001` | Passo 1. Sem valor no desenho. Usuário é a credencial |
| Frame A - Tela de login | Senha | Campo vazio | Abaixo de Usuário | `F001` | Passo 2. Sem valor no desenho |
| Frame A - Tela de login | Entrar | Botão | Abaixo de Senha | `F001` | Botão primário. Dispara a verificação dos passos 3a, 3b e 3c |
| Frame A - Tela de login | Linha de mensagem | Linha vazia | Sob o botão Entrar | `F001` | Reservada à mensagem. Vazia no desenho. A tela permanece no login |
| Fora do Frame A | Senha errada. | Anotação | Ao lado da página, primeira linha | `F001` | Passo 3a. O texto entra na linha sob Entrar. Sem seta. A recusa não gera log (`RN-14`) |
| Fora do Frame A | Usuário não cadastrado. | Anotação | Ao lado da página, segunda linha | `F001` | Passo 3b. O texto entra na mesma linha. Sem seta. ⚠️ [SUPOSIÇÃO] Ordem em relação à senha errada |
| Seta A para B | Usuário e senha autorizam a entrada. | Seta | Faixa entre as páginas. Ponta na borda superior do Frame B | `F001` | Passo 3c. Abre a tela inicial (`RN-02`) |
| Frame B - Tela inicial | Tela inicial | Título da tela | Topo da página | `F001` | Destino quando usuário e senha autorizam a entrada |
| Frame B - Tela inicial | Acervo | Botão | Grade, canto superior esquerdo | `F001` | Uma das quatro áreas reunidas na tela inicial |
| Frame B - Tela inicial | Usuários | Botão | Grade, canto superior direito | `F001` | Uma das quatro áreas reunidas na tela inicial |
| Frame B - Tela inicial | Empréstimos | Botão | Grade, canto inferior esquerdo | `F001` | Uma das quatro áreas reunidas na tela inicial |
| Frame B - Tela inicial | Relatórios | Botão | Grade, canto inferior direito | `F001` | Uma das quatro áreas reunidas na tela inicial |

---

## 3. Estados da Interface

- **Estado vazio:** Usuário e Senha ficam sem valor. A linha sob Entrar fica vazia neste desenho. `[CONFIRMAR]` Estado vazio da tela inicial.
- **Carregamento / atualização:** `[CONFIRMAR]` O passo e a regra não definem carregamento.
- **Bloqueios e restrições:** Senha errada mostra essa mensagem e a tela permanece no login (passo 3a). Usuário não cadastrado mostra essa mensagem e a tela permanece no login (passo 3b). A tela inicial abre quando usuário e senha autorizam a entrada (passo 3c, `RN-02`). A recusa não gera log (`RN-14`). A entrada não gera log (descrição de F001). A criação do primeiro gestor não é esta tela (`RN-14`).

---

## 4. Notas para o Operador

A recusa não gera log (`RN-14`). A entrada também não gera log, como está na descrição de F001. As duas mensagens estão fora da página: no desenho, a linha sob Entrar permanece vazia. A tela inicial reúne as quatro áreas e não descreve a entrada em cada uma.

> ✏️ **Ajustes ainda abertos:**
> - [ ] ⚠️ [SUPOSIÇÃO] A ordem entre senha errada e usuário não cadastrado. O desenho segue a ordem escrita na lista: senha errada, depois usuário não cadastrado. O step map também marca que a senha errada vale quando o usuário existe.
> - [ ] `[CONFIRMAR]` Estado vazio da tela inicial.
> - [ ] `[CONFIRMAR]` Carregamento.
