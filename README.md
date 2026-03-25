# Teoria da Computabilidade e Complexidade

Repositório gerado pelo **Academic Tutor Repo Builder V3**.
Plataforma alvo: **Claude Projects** (claude.ai)

## Como usar com Claude

1. Crie um **Projeto** no Claude.ai com o nome desta disciplina
2. Cole o conteúdo de `INSTRUCOES_CLAUDE_PROJETO.md` no campo **Instructions** do Projeto
3. Conecte este repositório GitHub ao Projeto (aba Settings → GitHub)
4. Inicie uma conversa — o Claude lerá os arquivos automaticamente

## Estrutura
- `system/` — política do tutor, pedagogia, modos, templates
- `course/` — identidade, mapa, cronograma, glossário, bibliografia
- `student/` — estado atual, perfil, schema de progresso
- `content/` — material de aula curado
- `exercises/` — listas de exercícios
- `exams/` — provas anteriores e gabaritos
- `raw/` — materiais originais (PDFs, imagens)
- `staging/` — extração automática (para revisão)
- `manual-review/` — revisão humana guiada
- `build/claude-knowledge/` — bundle para upload manual se necessário

## Arquivos-chave para o tutor

| Arquivo | Função |
|---|---|
| `INSTRUCOES_CLAUDE_PROJETO.md` | System prompt do Projeto |
| `student/STUDENT_STATE.md` | Estado atual do aluno — atualizar após cada sessão |
| `course/COURSE_MAP.md` | Preencher com os tópicos em ordem |
| `course/GLOSSARY.md` | Preencher com terminologia da disciplina |
| `content/BIBLIOGRAPHY.md` | Referências bibliográficas |

## Fluxo recomendado

1. Rodar extração automática no app
2. Revisar `manual-review/`
3. Promover conteúdo curado para `content/`, `exercises/`, `exams/`
4. Preencher `COURSE_MAP.md` e `GLOSSARY.md`
5. Conectar ao Projeto no Claude.ai
6. Após cada sessão de estudo: atualizar `student/STUDENT_STATE.md` e fazer push
