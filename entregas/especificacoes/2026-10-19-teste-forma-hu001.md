# HU001 Validar vínculo ativo do enfermeiro

> Prevalece, nesta ordem: cenário, regra, anexo ilustrativo. A lista de atualizações não altera o corpo.

> Teste de aplicação da skill `elaborar-especificacao`. O arquivo de origem não foi alterado: `2026-10-14-HU001-validar-vinculo-enfermeiro.md`. Status: Requer esclarecimento.

## 1. Descrição

Confere o vínculo ativo do enfermeiro no momento em que a agenda de classificação de risco é aberta, para que a falta de cadastro não apareça somente no encaminhamento médico.

## 2. Narrativa da História

- **Como** Enfermeiro de Triagem
- **Quero** ter o vínculo profissional ativo conferido ao abrir a agenda de classificação de risco
- **Para que** o encaminhamento médico não seja bloqueado por falta de cadastro

## 3. Critérios de Aceite

### Contexto compartilhado

Aplica-se a HU001-C01 e HU001-C02.

- **Dado que** a tela inicial está aberta
- **E** o botão "Abrir agenda de classificação de risco" está visível na faixa superior

### HU001-C01: [caminho-feliz] — Acesso liberado com vínculo ativo

- **Dado que** o Enfermeiro de Triagem possui vínculo ativo na unidade de saúde
- **Quando** o Enfermeiro de Triagem clica no botão "Abrir agenda de classificação de risco"
- **Então** o sistema exibe a agenda de classificação de risco na área principal `HU001-R01`
- **E** remove o botão "Abrir agenda de classificação de risco" da faixa superior

### HU001-C02: [permissao] — Bloqueio por vínculo inativo

- **Dado que** o profissional autenticado não possui vínculo ativo de enfermeiro na unidade
- **Quando** o profissional autenticado clica no botão "Abrir agenda de classificação de risco"
- **Então** o sistema não carrega a fila de pacientes `HU001-R01` `HU001-R02`
- **E** exibe a caixa de advertência: "Você não tem acesso à fila da classificação de risco. Solicite autorização para a equipe da unidade."
- **E** disponibiliza o botão "Ok" na caixa de advertência
- **E** registra a tentativa no log de auditoria

### HU001-C03: [alternativa] — Ciência do bloqueio

- **Dado que** a caixa de advertência de acesso não autorizado está visível
- **Quando** o Enfermeiro de Triagem clica no botão "Ok"
- **Então** o sistema fecha a caixa de advertência
- **E** mantém a área principal vazia
- **E** mantém o botão "Abrir agenda de classificação de risco" habilitado na faixa superior

### HU001-C04: [estado-vazio] — Tela inicial sem agenda aberta

- **Dado que** o Enfermeiro de Triagem acessou o módulo sem agenda aberta previamente
- **Quando** a tela inicial é carregada
- **Então** o sistema apresenta a área principal vazia
- **E** disponibiliza o botão "Abrir agenda de classificação de risco" habilitado na faixa superior

## 4. Regras de Negócio

### HU001-R01 — Habilitação profissional prévia

A abertura da agenda de classificação de risco é exclusiva de enfermeiro com vínculo ativo na unidade, e a conferência desse vínculo ocorre antes da abertura.

Demonstrada por: HU001-C01, HU001-C02

### HU001-R02 — Sigilo da fila

Profissional sem vínculo ativo de enfermeiro na unidade não visualiza a lista de pacientes aguardando classificação nem os dados de acolhimento.

Demonstrada por: HU001-C02

### HU001-R03 — Registro da tentativa de abertura

Toda tentativa de abertura da agenda registra a identificação do enfermeiro, a unidade, a data e a hora, e o resultado autorizado ou bloqueado.

Demonstrada por: cobertura incompleta. Ver seção 7.

## 5. Outras Informações Relevantes

### HU001-I01 — Wireflow de abertura da agenda

- **Caráter:** Ilustrativo
- **Alvo:** `[REFERÊNCIA INDISPONÍVEL: entregas/wireframes/2026-10-05-wireflow-F001-validar-vinculo-enfermeiro.md]`
- **Alvo:** `[REFERÊNCIA INDISPONÍVEL: entregas/wireframes/2026-10-05-wireflow-F001-validar-vinculo-enfermeiro.svg]`

O desenho abaixo repete só os resultados de HU001-C01, HU001-C02 e HU001-C04. Não define aceite.

```text
+--------------------------------------------------+
| FRAME 1 — Tela inicial                           |
| Faixa superior                                   |
|     [ Abrir agenda de classificação de risco ]   |
|              (área principal vazia)              |
+--------------------------------------------------+
        |                                  |
        | vínculo ativo                    | vínculo não ativo
        v                                  v
+----------------------------------+       +------------------------------------------+
| FRAME 2A — Agenda aberta         |       | FRAME 2B — Advertência                   |
| Faixa superior sem o botão       |       | Faixa superior com o botão de abrir      |
| Agenda de classificação de risco |       | "Você não tem acesso à fila da           |
|                                  |       | classificação de risco. Solicite         |
|                                  |       | autorização para a equipe da unidade."  |
|                                  |       |              [ Ok ]                     |
+----------------------------------+       +------------------------------------------+
```

## 6. O que esta História NÃO cobre

- Exibição e ordenação de pacientes na fila de espera. `[FORA DESTE PACOTE: HU002]`
- Disparo de chamada sonora e visual no painel da recepção. `[FORA DESTE PACOTE: HU003]`
- Assunção de atendimento e transição para o status Em Triagem. `[FORA DESTE PACOTE: HU004]`
- Gestão cadastral de vínculos e lotações de profissionais no módulo administrativo externo.

## 7. Suposições e Dúvidas Abertas

- `[CONFLITO]` HU001-R03 exige registro da tentativa autorizada e da bloqueada. HU001-C02 registra a tentativa bloqueada. HU001-C01 não mostra registro. Impacto: o desenvolvedor teria de decidir se o acesso liberado também gera registro, e quais dados entram nele.
- `[CONFLITO]` A narrativa usa Enfermeiro de Triagem. HU001-C02 usa "profissional autenticado" e não diz quem clica. Impacto: o aceite de permissão pode valer para outra persona além do enfermeiro.
- `[CONFIRMAR]` HU001-C01 diz que o sistema exibe a agenda. HU001-C02 diz que o sistema não carrega a fila. HU001-C03 diz que a área principal permanece vazia. Impacto: o resultado observável do bloqueio pode ser lido como agenda fechada, fila oculta ou área vazia.
- `[CONFIRMAR]` Enfermeiro de Triagem não está em `contexto/personas-usuario.md`. Impacto: a persona da história não está cadastrada no kit.
- `[CONFIRMAR]` Os termos do insumo não estão no glossário do kit. Impacto: não há vocabulário oficial deste produto para validar status, botão e papel. O texto do insumo foi mantido, sem troca pelo vocabulário de outro domínio.
- `[CONFIRMAR]` A família `erro` da regra 02 não tem fato neste insumo. Impacto: falha de comunicação, dado inválido ou indisponibilidade continuam sem aceite.
- `[CONFIRMAR]` O desenho de origem descrevia as setas como "seguir o atendimento" e "encerrar sem iniciar a triagem". A seção 6 deixa a triagem fora. Impacto: o desenho de origem alargava o escopo. Nesta reescrita o desenho para nos resultados dos cenários. Falta confirmação de que esse corte está correto.
- ⚠️ `[SUPOSIÇÃO]` Nenhuma. Não foi criada hipótese para fechar aceite.

## 8. Lista de atualizações

| Autor | Data | Descrição |
| --- | --- | --- |
| Angela Maria Amador | 2026-10-14 | Criação do documento de origem, com cenários e regras. |
| Angela Maria Amador | 2026-10-16 | Revisão do documento de origem. Aquela linha afirmava alinhamento à HU005, expurgo de interface nas regras e rastreabilidade bidirecional. Este arquivo não adota essas três afirmações como vigentes. |
| Teste da skill elaborar-especificacao | 2026-10-19 | Reescrita de forma, em arquivo novo. Origem preservada. Conflitos e ausências foram para a seção 7. Identificadores receberam o prefixo HU001. O desenho deixou de apontar para a triagem. |
