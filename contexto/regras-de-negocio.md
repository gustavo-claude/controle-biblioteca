# Regras de Negócio Gerais e Invariantes

> 💡 **PAPEL DESTE ARQUIVO:**  
> Centraliza as regras invariantes e restrições lógicas que se aplicam a todo o produto. Toda história de usuário deve referenciar os códigos destas regras (ex: `[RN-01]`, `[RN-02]`).  
> 🔢 **REGRA DE OURO:** O identificador numérico (`RN-XX`) é **permanente**. Se uma regra for revogada, marque-a como `[REVOGADA]` mas nunca reutilize o mesmo número.

---

## 1. Catálogo de Regras de Negócio Gerais

### `[RN-01]` — [Nome Curto da Regra — Ex: Unicidade de Responsável]
- **Descrição:** [PREENCHER: Descrição detalhada e inequívoca da regra]  
  *Ex: Um chamado só pode ter 1 atendente atribuído como responsável principal por vez.*
- **Impacto:** Impede conflitos de atendimento e respostas duplicadas ao solicitante.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-02]` — [Nome Curto da Regra — Ex: Prazo Padrão de Primeira Resposta]
- **Descrição:** [PREENCHER: Descrição da regra com prazos ou limites]  
  *Ex: Todo chamado categorizado como 'Crítico' deve receber primeira resposta em até 2 horas úteis.*
- **Impacto:** Dispara alerta visual amarelo no painel quando faltar 30 minutos para o estouro.
- **Exceção autorizada:** Chamados abertos fora do horário comercial iniciam a contagem no próximo dia útil.

---

### `[RN-03]` — [Nome Curto da Regra — Ex: Bloqueio de Cancelamento com Histórico]
- **Descrição:** [PREENCHER: Regra de validação de ação]  
  *Ex: Não é permitido cancelar chamados que já estejam no status 'Em Atendimento' ou 'Resolvido' sem autorização expressa do Supervisor.*
- **Impacto:** Evita perda de horas trabalhadas pelos analistas.
- **Exceção autorizada:** Apenas usuários com o perfil 'Supervisor' possuem o botão de cancelamento forçado com justificativa obrigatória.

---

## 2. Tabela de Números e Parâmetros com Origem

> 📊 *Todo número, prazo, tamanho de arquivo ou limite que aparecer em uma história deve estar registrado nesta tabela com sua respectiva fonte/origem.*

| Parâmetro / Limite | Valor Oficial | Origem / Fonte da Definição | Onde se Aplica |
|---|:--:|---|---|
| **[Tamanho Máx. Anexo]** | 10 MB por arquivo | [Decisão de TI / Infraestrutura] | Abertura e resposta de chamados |
| **[Formatos de Anexo]** | PDF, PNG, JPG, TXT | [Política de Segurança da Informação] | Upload de arquivos |
| **[Tentativas de Login]** | 5 tentativas | [Norma de Segurança Corporativa] | Tela de autenticação |
| **[Inatividade de Sessão]**| 30 minutos | [Política de Privacidade / LGPD] | Sessão web do usuário |

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todas as regras possuem identificadores permanentes [RN-XX]?
[ ] Todos os números e prazos têm origem formal indicada na tabela?
[ ] As exceções autorizadas foram documentadas explicitamente?
-->
