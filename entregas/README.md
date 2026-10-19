# Pasta `entregas/` — Artefatos Formais de Saída

> 💡 **PAPEL DESTA PASTA:**  
> Aqui ficam os artefatos produzidos durante o projeto. Cada tipo tem a própria subpasta, no mesmo desenho de `exemplos/`: funcionalidades, wireframes e especificações. Os pares bom/ruim em `exemplos/` calibram a redação; os arquivos desta pasta são o trabalho real do projeto.

```
entregas/
├── funcionalidades/    <- Lista de funcionalidades do sistema a ser criado
├── wireframes/         <- Estruturas visuais do fluxo de uso
└── especificacoes/     <- Especificações funcionais para a equipe de desenvolvimento
```

---

## 1. O que vai em cada subpasta

### `funcionalidades/`

Lista de funcionalidades do sistema a ser criado. Cada arquivo registra o que o sistema faz, o problema que resolve e o benefício para quem usa. O identificador de cada item tem dois algarismos: `F01`, `F02`, até `F99`. Não use `F001`.

Ao redigir ou revisar, siga `@exemplos/funcionalidades/funcionalidades-bom.md` e evite os vícios de `@exemplos/funcionalidades/funcionalidades-ruim.md`.

### `wireframes/`

Estruturas visuais de baixa complexidade que ajudam os usuários a compreender como será o fluxo de uso do sistema. Use esta pasta para o desenho da jornada antes de detalhar a especificação.

### `especificacoes/`

Documentos de especificação funcional apresentados à equipe de desenvolvimento. Cada arquivo cobre uma funcionalidade da lista mais recente em `entregas/funcionalidades/`. O identificador é `HU-XX`, com os mesmos dois algarismos da funcionalidade: `F01` gera `HU-01`. Não use `HU-001` nem `US-XX`.

A skill `elaborar-especificacao` confirma com o operador qual funcionalidade documentar antes de gravar. O documento se chama `HU-01`. Cenários, regras locais e anexos colam o número: `HU01-C01`, `HU01-R01`, `HU01-I01`.

Ao redigir ou revisar, siga `@exemplos/especificacoes/especifcacao-boa.md` e evite os vícios de `@exemplos/especificacoes/especificacao-ruim.md`. O formato da lista de origem está em `@exemplos/funcionalidades/funcionalidades-bom.md`.

---

## 2. Padrão obrigatório de nomenclatura

Todo arquivo salvo em uma subpasta leva a data ISO e um assunto curto, em kebab-case:

```
entregas/funcionalidades/AAAA-MM-DD-assunto.md
entregas/wireframes/AAAA-MM-DD-assunto.md
entregas/especificacoes/AAAA-MM-DD-assunto.md
```

Exemplos:

```
entregas/funcionalidades/2026-09-30-lista-funcionalidades.md
entregas/wireframes/2026-09-30-fluxo-abertura-chamado.md
entregas/especificacoes/2026-09-30-HU-01-abertura-chamado.md
```

Se já existir um arquivo com a mesma data e o mesmo assunto, acrescente um sufixo curto ao nome. Não grave artefatos na raiz de `entregas/` nem em `contexto/`.

---

## 3. Ciclo de vida de uma entrega

```
[Rascunho no Chat]
       │
       ▼ (Skills e personas do fluxo)
[Geração do artefato]
       │
       ▼ (Revisão, quando o tipo exigir)
[Auditoria e correções]
       │
       ▼ (Aprovação do PO)
[Arquivo final na subpasta correspondente, com data e assunto]
```

---

## 4. Regras de manutenção

- Grave cada artefato na subpasta do seu tipo: lista em `funcionalidades/`, fluxo visual em `wireframes/`, especificação em `especificacoes/`.
- Nunca edite uma entrega formal sem registrar a data da alteração ou gerar uma nova versão revisada.
- Arquivos desta pasta são os insumos diretos para o refinamento com a equipe de desenvolvimento.
