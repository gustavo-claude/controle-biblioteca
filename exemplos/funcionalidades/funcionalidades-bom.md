# Modelo de leitura da lista de funcionalidades

> 📋 **Papel deste arquivo:**
> Modelo de disposição para leitura. O texto é o de `entregas/funcionalidades/2026-10-15-lista-funcionalidades.md`. Os identificadores foram alinhados a dois algarismos: `F01`, `F02`, até `F18`. O restante das frases permanece o da origem.
> Cada funcionalidade ocupa uma tabela. As cinco categorias que na origem são colunas — Funcionalidade, Descrição, Problema que Resolve, Benefícios que Traz e Passos — passam a ser linhas, para o texto usar a largura da página. O identificador fica no título da tabela, com dois algarismos. Módulos, personas, notas, limites, pendências e confirmações permanecem na mesma ordem.

---

# Lista de Funcionalidades do Produto: Notifica Belém

> 📋 **Contexto e Origem:**
> Documento elaborado pelo `@analista` com base nos arquivos de `contexto/` e no formato de `exemplos/funcionalidades/funcionalidades-bom.md`, com a coluna Passos desta skill.
> Onde `contexto/briefing.md` ou o marco ainda aberto em `contexto/produto.md` divergem de `contexto/regras-de-negocio.md`, a lista segue a regra. Uma ação sobre várias fichas do mesmo tipo é uma funcionalidade só.
> Esta é a única lista de funcionalidades. Em 15/10/2026, as listas de 09/10 e de 14/10 foram removidas e os IDs foram renumerados para seguir a ordem de leitura deste documento: módulo de `contexto/produto.md` e, dentro dele, a persona que executa, conforme `contexto/personas-usuario.md`. Dentro da persona, a ordem segue as transições de status. Cada funcionalidade aparece uma vez, na primeira persona dessa ordem que a executa. **F13** fica no módulo Investigação, à parte das personas: o ator é o sistema. `contexto/` não foi alterado.
> Validação dos passos: pendente do @analista. Confirmações pontuais do PO em 16/10/2026 não fecham a validação dos passos em bloco.

## Lista de Funcionalidades com Problemas, Benefícios e Passos

### Módulo Notificação

#### Profissional da unidade notificadora

##### **F01** — Confirmar preenchimento da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Confirmar preenchimento da notificação |
| **Descrição** | Na página inicial, o profissional da unidade notificadora aciona Nova Notificação e abre a ficha. Em seguida, preenche os campos da ficha daquele agravo indicados para a unidade e confirma. Preencher sem confirmar não é outra funcionalidade. Se a sessão termina antes da confirmação, a notificação permanece em Em preenchimento e o preenchimento continua numa sessão seguinte, retomado pelo profissional da unidade notificadora. Enquanto está em Em preenchimento, a ficha segue exibida na página inicial, na coluna de notificações salvas ainda não confirmadas. Somente o descarte exclui a ficha. Na confirmação, o vínculo é reconhecido pelo CPF ou pelo CNS na base do CNES da unidade de Belém em que o agravo foi registrado. O profissional vê uma de duas reações: a notificação fica disponível para a análise preliminar, ou vê o erro de ausência de vínculo e a notificação não segue. Depois da devolução para correção, a nova confirmação passa pela mesma reação. Em Em preenchimento, esse profissional pode descartar a notificação, que passa a Descartada. O descarte exclui todos os dados preenchidos e a ficha descartada é perdida. Permanecem somente o log de abertura da ficha pelo usuário e o log do descarte, para auditoria. O detalhe desses logs fica para a especificação funcional. A página inicial não lista a notificação Descartada. A confirmação não é o envio às bases estadual e federal. |
| **Problema que Resolve** | A notificação em papel se extravia antes de chegar ao DEVS da SESMA. Sem a confirmação, ela não entra na análise preliminar. Profissional sem vínculo com o CNES da unidade não deve seguir à SESMA. Hoje a notificação também chega por e-mail ou pedido presencial. |
| **Benefícios que Traz** | A notificação só fica disponível para a análise preliminar quando o preenchimento é confirmado e o vínculo é reconhecido. Sem o vínculo, o profissional vê o erro e a notificação não segue. Se a sessão termina antes da confirmação, ela permanece em Em preenchimento. |
| **Passos** | 1. Acionar Nova Notificação e abrir a ficha<br>2. Preencher os campos da ficha indicados para a unidade<br>3. Se descartar a notificação:<br>3a. Passar a notificação a Descartada, excluir os dados preenchidos e perder a ficha. Manter o log de abertura da ficha pelo usuário e o log do descarte, para auditoria, e encerre<br>Senão:<br>4. Se o preenchimento não for concluído nesta sessão:<br>4a. Manter a notificação em Em preenchimento, exibida na coluna de notificações salvas ainda não confirmadas<br>4b. Retomar o preenchimento na sessão seguinte, pelo profissional da unidade notificadora, e volte ao passo 2<br>Senão:<br>4c. Confirmar a notificação<br>5. Se o profissional não tiver vínculo com o CNES da unidade:<br>5a. Ver o erro de ausência de vínculo<br>5b. Permanecer no estado em que estava e retomar a edição da ficha nesse estado<br>Senão, com o vínculo reconhecido:<br>5c. Ver a notificação disponibilizada para a análise preliminar e encerre |

##### **F02** — Acompanhar movimento e desfecho da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Acompanhar movimento e desfecho da notificação |
| **Descrição** | O profissional da unidade notificadora acompanha os movimentos e o desfecho das notificações que confirmou, inclusive o encaminhamento ao grupo especializado, a devolução para correção, o retorno à análise preliminar e o indeferimento. Na notificação confidencial, vê somente o registro. A notificação em Em correção segue exibida na coluna de notificações abertas. A notificação em Em preenchimento segue na coluna de notificações salvas ainda não confirmadas. Somente Descartada sai da página inicial. |
| **Problema que Resolve** | O fechamento da notificação em papel não volta para a unidade, e a unidade deixa de acompanhá-la. |
| **Benefícios que Traz** | A unidade que confirmou vê os movimentos e o desfecho, salvo na notificação confidencial, em que vê somente o registro. |
| **Passos** | 1. Acompanhar a notificação confirmada<br>2. Se a notificação for confidencial:<br>2a. Ver somente o registro da notificação e encerre<br>Senão:<br>2b. Ver os movimentos e o desfecho da notificação |

##### **F03** — Corrigir ficha da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Corrigir ficha da notificação |
| **Descrição** | O profissional da unidade notificadora corrige a ficha em Em correção. A visualização e a edição equivalem às de Em preenchimento. Se a composição mudou depois da abertura, a correção abre na composição vigente, com os campos ausentes na versão anterior em branco. Se a sessão termina antes da conclusão, a notificação permanece em Em correção e a correção continua numa sessão seguinte, retomada pelo profissional da unidade notificadora. Enquanto está em Em correção, a ficha segue exibida na página inicial, na coluna de notificações abertas. Somente o descarte exclui a ficha. Ao concluir, ele confirma de novo pelo passo 4c de **F01**, ou descarta a notificação, que passa a Descartada. No descarte, os dados preenchidos são excluídos e a ficha descartada é perdida. Permanecem somente o log de abertura da ficha pelo usuário e o log do descarte, para auditoria. O detalhe desses logs fica para a especificação funcional. A página inicial não lista a notificação Descartada. A notificação só volta à análise preliminar se o vínculo for reconhecido na confirmação. |
| **Problema que Resolve** | A ficha devolvida permanece inconsistente até a correção da unidade. |
| **Benefícios que Traz** | A ficha corrigida fica pronta para a nova confirmação de **F01**, ou a notificação passa a Descartada. |
| **Passos** | 1. Se a composição da ficha tiver mudado depois da abertura da notificação:<br>1a. Ver a composição vigente, com os campos ausentes na versão anterior em branco<br>Senão:<br>1b. Ver a ficha na composição já em uso<br>2. Corrigir os campos da ficha em Em correção<br>3. Se a correção não for concluída nesta sessão:<br>3a. Manter a notificação em Em correção, exibida na coluna de notificações abertas<br>3b. Retomar a correção na sessão seguinte, pelo profissional da unidade notificadora, e volte ao passo 1<br>Senão:<br>4. Se descartar a notificação:<br>4a. Passar a notificação a Descartada, excluir os dados preenchidos e perder a ficha. Manter o log de abertura da ficha pelo usuário e o log do descarte, para auditoria, e encerre<br>Senão:<br>4b. Seguir para a nova confirmação no passo 4c de **F01** |

#### Responsável pela análise preliminar

A composição da ficha prepara o agravo antes do preenchimento. A persona que executa vem depois do profissional da unidade notificadora.

##### **F04** — Compor ficha do agravo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Compor ficha do agravo |
| **Descrição** | O responsável pela análise preliminar cria a ficha nomeando o agravo, indica os campos exibidos ao profissional da unidade notificadora e os campos exibidos aos investigadores, indica se o agravo exige discrição e associa o impresso oficial daquele agravo. A impressão da notificação reproduz esse impresso com os dados preenchidos. Vale para todo agravo, numa ação só. Notificação já aberta não muda de composição. Se ela volta de Em análise para Em correção depois dessa mudança, a correção abre na composição vigente, com os campos ausentes na versão anterior em branco. |
| **Problema que Resolve** | O impresso oficial muda conforme o agravo. Sem essa composição, a impressão usaria um formulário genérico no lugar do impresso oficial. |
| **Benefícios que Traz** | Agravo novo entra pela ficha e pelo impresso oficial daquele agravo. A unidade e os investigadores veem os campos indicados para cada um. |
| **Passos** | 1. Nomear o agravo da ficha<br>2. Indicar os campos exibidos ao profissional da unidade notificadora<br>3. Indicar os campos exibidos aos investigadores<br>4. Associar o impresso oficial do agravo<br>5. Indicar se o agravo exige discrição |

### Módulo Investigação

#### Responsável pela análise preliminar

##### **F05** — Incluir prazo de referência do agravo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Incluir prazo de referência do agravo |
| **Descrição** | O responsável pela análise preliminar inclui o prazo de referência do agravo, adiciona agravo novo e atualiza agravo já existente. O prazo de referência do agravo é esta funcionalidade. Enquanto o agravo não tiver prazo de referência gravado, o teto permanece 90 dias, da notificação ao desfecho. |
| **Problema que Resolve** | Sem prazo de referência, a notificação aberta só tem o teto de 90 dias. A meta do ciclo é o desfecho no prazo daquele agravo. |
| **Benefícios que Traz** | Quando o prazo de referência está gravado, a notificação aberta daquele agravo é contada nele. Sem valor gravado, segue o teto de 90 dias. |
| **Passos** | 1. Se o agravo ainda não existir:<br>1a. Adicionar o agravo<br>Senão:<br>1b. Atualizar o agravo já existente<br>2. Incluir o prazo de referência do agravo |

##### **F06** — Declarar confidencialidade da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Declarar confidencialidade da notificação |
| **Descrição** | O responsável pela análise preliminar declara a notificação confidencial quando o agravo exige discrição. Essa exigência é indicada por ele ao configurar o agravo, no passo 5 de **F04**. Não há lista fechada prévia. |
| **Problema que Resolve** | Quando o agravo exige discrição, a unidade notificadora não pode ver os movimentos nem o desfecho. |
| **Benefícios que Traz** | A unidade mantém o registro da notificação e deixa de ver os movimentos e o desfecho. |
| **Passos** | 1. Declarar a confidencialidade da notificação |

##### **F07** — Registrar transmissão interna da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar transmissão interna da notificação |
| **Descrição** | O responsável pela análise preliminar encaminha a notificação ao grupo especializado do perfil. Ela passa de Em análise para Sob investigação. Este é o primeiro repasse da transmissão interna e a orientação que o grupo recebe. |
| **Problema que Resolve** | A análise preliminar examina, uma a uma, notificações que chegam em papel, por e-mail e por pedido presencial, e precisa identificar o perfil. |
| **Benefícios que Traz** | A notificação sai da análise preliminar e fica com o grupo especializado daquele perfil. |
| **Passos** | 1. Identificar o perfil da notificação<br>2. Encaminhar a notificação ao grupo especializado desse perfil |

##### **F08** — Registrar devolução para correção da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar devolução para correção da notificação |
| **Descrição** | O responsável pela análise preliminar devolve a ficha ao profissional da unidade notificadora quando a inconsistência é imperícia, falta de clareza ou situação que tem remediação. A notificação passa de Em análise para Em correção. O prazo continua. Os movimentos ficam registrados. Este destino é distinto do indeferimento. |
| **Problema que Resolve** | Notificação inconsistente não deve seguir ao grupo especializado. |
| **Benefícios que Traz** | A ficha volta à unidade para correção e não segue ao grupo enquanto permanecer nesse destino. |
| **Passos** | 1. Devolver para correção quando a inconsistência for imperícia, falta de clareza ou situação que tem remediação<br>2. Devolver a ficha ao profissional da unidade notificadora |

##### **F09** — Registrar indeferimento da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar indeferimento da notificação |
| **Descrição** | O responsável pela análise preliminar indefere quando há fraude clara ou erro grosseiro de notificação. A notificação passa de Em análise para Indeferida e para nesse desfecho. O prazo não corre. Fica fora da correção e fora do grupo especializado. Não exige envio às bases estadual e federal. |
| **Problema que Resolve** | Nem toda inconsistência volta para correção. Sem este destino, a notificação ou voltaria à unidade ou seguiria ao grupo. |
| **Benefícios que Traz** | A notificação encerra o fluxo na análise preliminar, sem correção, sem grupo e sem envio às bases. |
| **Passos** | 1. Indeferir quando houver fraude clara ou erro grosseiro de notificação<br>2. Indeferir a notificação |

#### Investigador do grupo especializado

No caminho sem visita, o envio é **F18**, no módulo Encaminhamento externo, e o encerramento é **F12**. **F12** só fica habilitado em Enviado. No caminho com visita, o pedido é **F14**, no módulo Visitas presenciais; **F11** e **F12** também são do investigador da visita presencial.

##### **F10** — Atualizar investigação da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Atualizar investigação da notificação |
| **Descrição** | Enquanto a notificação está em Sob investigação, somente o usuário autorizado daquele grupo especializado a atualiza. O responsável pelo grupo, membro desse grupo com acesso mais amplo, pode movimentar e atualizar todas as notificações daquele grupo. Outro grupo não a altera enquanto ela permanece ali. Quando não há visita, o investigador conclui os campos pendentes da ficha e a notificação passa a Em envio. |
| **Problema que Resolve** | A investigação no meio analógico não fica registrada na notificação, com risco de perda da informação. |
| **Benefícios que Traz** | A investigação fica na notificação daquele grupo. Sem visita, os campos pendentes concluídos levam a notificação a Em envio. |
| **Passos** | 1. Atualizar a ficha da notificação em Sob investigação<br>2. Se a investigação não exigir visita presencial:<br>2a. Concluir os campos pendentes da ficha<br>2b. Passar a notificação a Em envio e encerre<br>Senão:<br>2c. Manter a notificação em Sob investigação |

##### **F11** — Registrar extensão do prazo de investigação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar extensão do prazo de investigação |
| **Descrição** | Membro do grupo especializado ou investigador da visita presencial registra a extensão. O número de dias é o que essa pessoa definir. A extensão soma esse número ao prazo daquela investigação e fica no histórico. |
| **Problema que Resolve** | Quem solicita a extensão precisa continuar a investigação porque ainda não há resultado conclusivo. |
| **Benefícios que Traz** | O prazo daquela investigação aumenta no número de dias informado, o registro fica no histórico e o alerta de 15 dias usa o prazo estendido. |
| **Passos** | 1. Definir o número de dias da extensão<br>2. Registrar a extensão no histórico da notificação |

##### **F12** — Encerrar investigação da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Encerrar investigação da notificação |
| **Descrição** | O encerramento é ato do investigador daquela notificação e só fica habilitado em Enviado. Sem visita, é o investigador do grupo especializado. Com visita, é o investigador da visita presencial. Ele inicia o encerramento manualmente, preenche um texto de conclusão e dá o desfecho Encerrada. Não há verificação dos dados na base externa. O envio não encerra a notificação. Encerrada não tem saída. |
| **Problema que Resolve** | O fechamento não volta no fluxo de papel, e a notificação investigada pode permanecer sem desfecho mesmo com a investigação concluída. |
| **Benefícios que Traz** | A notificação passa de Enviado para Encerrada quando o investigador inicia o encerramento, preenche o texto de conclusão e dá o desfecho. O envio não produz esse desfecho. |
| **Passos** | 1. Iniciar o encerramento da notificação em Enviado<br>2. Preencher o texto de conclusão<br>3. Dar o desfecho Encerrada da notificação |

#### O sistema

##### **F13** — Elevar prioridade de acompanhamento da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Elevar prioridade de acompanhamento da notificação |
| **Descrição** | O sistema aplica a prioridade de acompanhamento da notificação aberta. O alerta usa o prazo contado da confirmação. Se esse prazo é maior que 15 dias, a prioridade entra em alerta nos 15 dias anteriores ao fim. Se é menor que 15 dias, a notificação permanece em alerta desde a confirmação. No vencimento, a prioridade fica maior do que no alerta e permanece assim até o desfecho. A evolução continua permitida após o vencimento. Com extensão, o alerta passa a usar o prazo já estendido. Em Indeferida, o prazo não corre e a notificação sai da contagem. Quando a notificação sai de Em análise para Em correção, o prazo continua. Os movimentos da notificação ficam registrados. |
| **Problema que Resolve** | A notificação aberta pode chegar ao fim do prazo sem distinção das que estão nos dias finais ou já vencidas. |
| **Benefícios que Traz** | A notificação aberta fica em alerta antes do fim do prazo e com prioridade maior no vencimento, e a evolução segue permitida. |
| **Passos** | 1. Contar o alerta a partir da confirmação da notificação<br>2. Se o prazo contado da confirmação for maior que 15 dias:<br>2a. Entrar em alerta nos 15 dias anteriores ao fim<br>Senão:<br>2b. Manter a notificação em alerta desde a confirmação<br>3. Se houver extensão do prazo de investigação: usar o prazo já estendido e volte ao passo 2<br>Senão: siga para o passo 4<br>4. Se o prazo vencer: elevar a prioridade acima do alerta até o desfecho<br>5. Manter a evolução permitida após o vencimento<br>6. Se a notificação estiver Indeferida:<br>6a. Interromper a contagem do prazo<br>Senão:<br>6b. Manter a contagem do prazo, inclusive em Em correção<br>7. Registrar os movimentos da notificação |

### Módulo Visitas presenciais

#### Investigador do grupo especializado

##### **F14** — Solicitar visita presencial da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Solicitar visita presencial da notificação |
| **Descrição** | Quando a investigação exige visita presencial, o investigador do grupo especializado solicita o coordenador da equipe de visitas. A notificação passa de Sob investigação para Visita solicitada. Nesse caminho, o grupo não dá o desfecho. Este é o segundo repasse da transmissão interna. |
| **Problema que Resolve** | A visita presencial depende de um processo que já começa lento no meio analógico, fora de um fluxo único da notificação. |
| **Benefícios que Traz** | A notificação segue para a área de gestão de visitas presenciais antes do desfecho, e o grupo especializado não encerra esse caminho. |
| **Passos** | 1. Solicitar a visita presencial ao coordenador da equipe de visitas |

#### Coordenador da equipe de visitas

##### **F15** — Atribuir visita presencial da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Atribuir visita presencial da notificação |
| **Descrição** | O coordenador da equipe de visitas vincula a ficha a uma equipe, para uma ou mais notificações, e atribui a visita a um membro dessa equipe. Logo após essa atribuição, a notificação passa de Visita solicitada para Visita atribuída. A rota fica em **F16** e não é condição desse status. O coordenador não registra a evolução da visita e não dá o desfecho. |
| **Problema que Resolve** | O coordenador atribui a visita a um membro da equipe no meio analógico, fora de um fluxo único da notificação. |
| **Benefícios que Traz** | A visita fica atribuída a um membro da equipe de visitas e a notificação passa a Visita atribuída. O coordenador não substitui quem investiga nem quem dá o desfecho. |
| **Passos** | 1. Vincular a ficha a uma equipe, para uma ou mais notificações<br>2. Distribuir a visita a um membro da equipe de visitas<br>3. Passar a notificação a Visita atribuída |

##### **F16** — Definir rota de menor custo das visitas presenciais

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Definir rota de menor custo das visitas presenciais |
| **Descrição** | O coordenador da equipe de visitas indica os motoristas e os veículos disponíveis e combina os investigadores por veículo. O sistema compõe a rota a partir das visitas previstas para esses investigadores, pela rota de menor custo para alcançá-las. Esta funcionalidade ocorre depois da atribuição em **F15**, com a notificação já em Visita atribuída. Definir a rota não muda o status. O coordenador não registra a evolução da visita e não dá o desfecho. |
| **Problema que Resolve** | O coordenador define motorista, veículo e a combinação de investigadores por veículo no meio analógico, fora de um fluxo único da notificação. |
| **Benefícios que Traz** | As visitas previstas para esses investigadores ficam numa rota de menor custo para alcançá-las, com motorista, veículo e investigadores definidos. |
| **Passos** | 1. Indicar os motoristas e os veículos disponíveis<br>2. Combinar os investigadores por veículo<br>3. Ver a rota composta a partir das visitas previstas para esses investigadores, pela rota de menor custo para alcançá-las |

#### Investigador da visita presencial

Nesta persona, a linha própria deste módulo é **F17**. No caminho com visita, ela também executa **F11** e **F12**, no módulo Investigação, e **F18**, no módulo Encaminhamento externo.

##### **F17** — Registrar evolução da visita presencial

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar evolução da visita presencial |
| **Descrição** | O investigador da visita presencial, em Visita atribuída, atualiza a ficha e registra a evolução. Ao concluir, a notificação passa a Em envio. |
| **Problema que Resolve** | A evolução da visita depende de um processo que já começa lento e segue no meio analógico. |
| **Benefícios que Traz** | A evolução fica registrada na notificação, e a notificação chega a Em envio antes do desfecho. |
| **Passos** | 1. Atualizar a ficha em Visita atribuída<br>2. Registrar a evolução da visita presencial<br>3. Passar a notificação a Em envio |

### Módulo Encaminhamento externo

Quando o envio é automático, o ator é o sistema. Quando não é, o investigador do grupo especializado marca **Enviado** se não houver visita, e o investigador da visita presencial marca **Enviado** se houver visita.

##### **F18** — Enviar dados da notificação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Enviar dados da notificação |
| **Descrição** | Antes do desfecho dado pelo investigador, os dados da notificação são enviados às bases estadual e federal. Quando há integração e o envio é automático, o sistema envia e a notificação passa a Enviado. Quando o envio não é automático, o investigador desse caminho marca a notificação como Enviado: o do grupo, quando não há visita, ou o da visita, quando há visita. Sem meio de integração, ou com a conexão da base exterior indisponível, o investigador imprime a ficha no impresso oficial. A digitação nas bases pelo método anterior, descrita em `[RN-11]`, ocorre fora do Notifica Belém. A marcação como Enviado informa que essa digitação já foi concluída. Não há verificação dos dados na base externa. Enviado habilita o encerramento. O indeferimento não depende deste envio. |
| **Problema que Resolve** | Sem integração, ou com a base exterior indisponível, a digitação nas bases estadual e federal depende da ficha impressa. A ficha de papel se extravia. |
| **Benefícios que Traz** | A notificação passa a Enviado quando o envio automático conclui ou quando o investigador marca o envio. Enviado habilita o encerramento. Na falta de integração ou de conexão, a impressão no impresso oficial sustenta a digitação feita fora do Notifica Belém. |
| **Passos** | 1. Se houver integração e o envio for automático:<br>1a. Enviar os dados às bases estadual e federal e passar a notificação a Enviado e encerre<br>Senão:<br>1b. Imprimir a ficha no impresso oficial do agravo<br>2. Informar a conclusão da digitação feita fora do Notifica Belém, marcando a notificação como Enviado |

### Limites e Não-Escopo

- ❌ **Registro clínico:** O Notifica Belém não registra atendimento clínico e não é prontuário. Origem: `contexto/produto.md` e `[RN-14]`.
- ❌ **Bases estadual e federal:** O produto encaminha dados a essas bases e não as substitui. Origem: `contexto/produto.md`, `contexto/glossario.md` e `[RN-11]`.
- ❌ **Fora da notificação compulsória:** Não entra doença ou agravo que não seja de notificação compulsória. Origem: `contexto/produto.md` e `[RN-14]`.
- ❌ **Fora de Belém:** Não entra notificação de evento ocorrido fora do território de Belém. Origem: `contexto/produto.md` e `[RN-14]`.
- ❌ **Sem vínculo:** Não atende profissional de saúde sem vínculo com o CNES da unidade em que a doença ou o agravo foi registrado. Origem: `contexto/produto.md` e `[RN-01]`.
- ❌ **Outro município:** Não atende unidade de saúde de outro município. Origem: `contexto/produto.md` e `[RN-14]`.

### Pendências

- `[CONFIRMAR]` Onde entra o controle da agenda da visita. Faz parte de `[RN-09]`, e o módulo Visitas presenciais inclui agendar a visita. O PO não o colocou na atribuição, **F15**, nem na rota, **F16**. A notificação já passa a Visita atribuída em **F15**, antes da rota e antes da agenda.
- `[CONFIRMAR]` O que conta como custo na rota de menor custo de **F16**. O PO afirmou o critério de menor custo para alcançar as visitas previstas. A unidade desse custo não foi dita.

### Confirmado em 16/10/2026

- A notificação passa de Visita solicitada para Visita atribuída na atribuição ao membro da equipe, em **F15**. A rota de **F16** não é condição desse status. Origem: PO, 16/10/2026.
- Os dados das fichas da página inicial, e os de sinais e sintomas ou exames, serão detalhados na especificação funcional. Origem: PO, 16/10/2026.
- Somente o descarte exclui a ficha. A página inicial não lista a notificação Descartada. O descarte exclui todos os dados preenchidos e a ficha descartada é perdida. Permanecem somente o log de abertura da ficha pelo usuário e o log do descarte, para auditoria. O detalhe desses logs será definido na especificação funcional. Origem: PO, 16/10/2026. O descarte pode ocorrer a partir de **Em preenchimento** e de **Em correção**.
- Enquanto a notificação está em **Em preenchimento**, a ficha segue exibida na página inicial, na coluna de notificações salvas ainda não confirmadas. Enquanto está em **Em correção**, segue na coluna de notificações abertas. Origem: PO, 16/10/2026.
