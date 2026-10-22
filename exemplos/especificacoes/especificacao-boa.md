# HU-01 Abrir ficha nova da notificação

> Prevalece, nesta ordem: cenário, regra, anexo ilustrativo. A lista de atualizações não altera o corpo.

## 1. Descrição

O profissional da unidade notificadora abre uma nova ficha de notificação a partir da página inicial, para notificar um agravo ou doença registrado na unidade. A área de escolha do tipo de agravo aparece depois que a ficha nova está aberta.

## 2. Narrativa da História

- **Como** profissional da unidade notificadora
- **Quero** abrir uma nova ficha de notificação
- **Para que** possa realizar a notificação de um agravo ou doença registrado em minha unidade

## 3. Critérios de Aceite

### HU01-C01: [caminho-feliz] — Abrir a ficha a partir de Nova Notificação

- **Dado que** o profissional da unidade notificadora está na página inicial
- **Quando** o profissional da unidade notificadora aciona Nova Notificação
- **Então** a página de uma ficha nova abre
- **E** é exibida uma ferramenta de seleção do tipo de agravo

### HU01-C02: [caminho-feliz] — Selecionar agravo para listar campos da Nova Notificação

- **Dado que** o profissional da unidade notificadora está na página da nova ficha
- **Quando** o profissional seleciona o tipo de agravo
- **Então** são exibidos os campos da ficha escolhida
- **E**  é exibido uma ferramente de busca de pacientes junto a área de seleção de agravo

## 4. Regras de Negócio

### HU01-R01 — Nova Notificação abre uma ficha nova

As novas notificações devem obrigatoriamente ser de um agravo ou doença existentes no sistema, ou seja, cadastrado previamente conforme regra RN-18.

Demonstrada por: HU01-C02

## 5. Outras Informações Relevantes

### HU01-I01 — Abertura da ficha

- **Caráter:** Ilustrativo
- **Alvo:** desenho neste arquivo

```text
Frame D — Página inicial
[ Nova Notificação ]
        |
        v
Frame A — Ficha nova
área de escolha do tipo de agravo
[Selecionado tipo de agravo]
        |
        v
Frame A — Ficha nova
Carregados os campos da ficha escolhida
Exibida área de busca de paciente


```

O desenho repete a abertura aceita em HU01-C01.

## 6. O que esta História NÃO cobre

- Preencher os campos da ficha, manter a notificação em Em preenchimento quando a sessão termina antes da confirmação — `HU-02`
- Retomar o preenchimento da notificação em Em preenchimento — `HU-03`
- Descartar a notificação em Em preenchimento — `HU-04`
- Confirmar o encaminhamento e a reação do vínculo com o CNES da unidade — `HU-05`
- Nomear o agravo e definir os campos da ficha — `HU-10` e `HU-11`
- A exceção de `[RN-18]` para notificação já aberta que volta de Em análise para Em correção — `HU-07`

## 7. Suposições e Dúvidas Abertas

- Família erro: o insumo deste item não afirma falha ao abrir a ficha. Impacto: não há cenário de erro.
- Família estado-vazio: a ficha sem valor preenchido está no caminho feliz. O que a página inicial mostra quando não há notificação não é deste item. Impacto: não há cenário de estado vazio separado.
- Família permissao: o insumo deste item não afirma o que outra persona vê ao acionar Nova Notificação. Impacto: não há cenário de permissão.

## 8. Lista de atualizações

| Autor     | Data       | Descrição                                                                                                                             |
| --------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------- |
