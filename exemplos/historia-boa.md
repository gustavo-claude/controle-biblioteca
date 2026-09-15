


# [US-01] Abertura de Chamado Técnico com Anexo de Evidência

> 🌟 **EXEMPLO PADRÃO OURO:**  
> Use este arquivo como modelo de referência para o nível de detalhe, estrutura e precisão esperados de uma história de usuário neste workspace.

---

## 1. Narrativa da História

- **Como** Rodrigo (Coordenador de Vendas — Solicitante Interno)
- **Quero** abrir um chamado técnico descrevendo o problema do meu computador e anexando capturas de tela do erro
- **Para que** a equipe de suporte receba as informações completas de primeira, evitando trocas de mensagens desnecessárias e agilizando meu atendimento.

---

## 2. Regras de Negócio Aplicadas

- `[RN-01]` — Todo chamado criado deve iniciar compulsoriamente no status 'Aberto'.
- `[RN-02]` — O solicitante só pode enviar anexos nos formatos permitidos (PDF, PNG, JPG) com limite máximo de 10 MB por arquivo.

---

## 3. Critérios de Aceite (Testáveis)

### Cenário 1: Abertura de chamado com anexo válido (Caminho Feliz)
- **Dado que** Rodrigo está autenticado no sistema e acessa o formulário de abertura de chamado
- **E** preenche o 'Título' com *"Erro ao exportar relatório de vendas"*
- **E** preenche a 'Descrição' com *"O sistema fecha sozinho ao clicar em exportar"*
- **E** anexa um arquivo PNG de 2 MB contendo o print da tela de erro
- **Quando** Rodrigo clica no botão "Enviar Chamado"
- **Então** o sistema grava a solicitação, define o status como 'Aberto' `[RN-01]`
- **E** gera um número de protocolo sequencial (ex: `#2026-0891`)
- **E** exibe a mensagem de sucesso: *"Chamado #2026-0891 registrado com sucesso! Nossa equipe entrará em contato em até 2 horas úteis."*
- **E** redireciona o usuário para a tela de acompanhamento do chamado.

---

### Cenário 2: Tentativa de upload de arquivo acima do limite (Validação de Erro)
- **Dado que** Rodrigo tenta anexar um vídeo no formato MP4 de 25 MB
- **Quando** o arquivo é selecionado no campo de upload
- **Então** o sistema não realiza o upload
- **E** exibe imediatamente o alerta em vermelho: *"Arquivo não permitido. Envie apenas imagens (PNG, JPG) ou PDF com tamanho máximo de 10 MB [RN-02]."*
- **E** mantém o botão "Enviar Chamado" desabilitado até a correção.

---

### Cenário 3: Tentativa de envio com campo obrigatório vazio (Validação de Entrada)
- **Dado que** Rodrigo deixa o campo 'Descrição' em branco
- **Quando** clica no botão "Enviar Chamado"
- **Então** o sistema impede o envio
- **E** destaca o campo 'Descrição' com borda vermelha e a mensagem: *"Por favor, detalhe o problema para que possamos ajudá-lo."*

---

### Cenário 4: Primeiro acesso à tela de abertura (Estado Vazio / Inicial)
- **Dado que** Rodrigo acessa a página de abertura de chamados
- **Quando** a interface é carregada
- **Então** o formulário é exibido limpo, com o cursor posicionado no campo 'Título'
- **E** exibe uma caixa informativa de ajuda: *"Dica: Incluir capturas de tela do erro reduz o tempo de atendimento pela metade."*

---

## 4. O que esta História NÃO Cobre (Fora de Escopo)

- Não inclui gravação de vídeo direto pela webcam/tela (fica para a US-08);
- Não inclui classificação automática de categoria por IA (fica para a US-12);
- Não envia notificações por SMS ou WhatsApp (apenas e-mail padrão do sistema).

---

## 5. Suposições e Riscos

- ⚠️ `[SUPOSIÇÃO]` Consideramos que o serviço corporativo de e-mail está disponível para disparar a confirmação de abertura sem atrasos.
