# Teoria da Computabilidade e Complexidade

Repositório gerado pelo **Academic Tutor Repo Builder V3**.
Compatível com **Claude Projects**, **ChatGPT Projects** e **Gemini Gems**.

## Como usar com uma LLM

1. Gere ou regenere os arquivos em `setup/`
2. Escolha a plataforma alvo:
   - `setup/INSTRUCOES_CLAUDE_PROJETO.md`
   - `setup/INSTRUCOES_GPT_PROJETO.md`
   - `setup/INSTRUCOES_GEMINI_PROJETO.md`
3. Cole o arquivo correspondente no campo de instruções da plataforma
4. Conecte este repositório GitHub ou carregue os arquivos conforme a plataforma escolhida
5. Inicie a conversa usando os artefatos gerados do app

## Estrutura
- `system/` — política do tutor, pedagogia, modos, templates
- `course/` — identidade, mapa, cronograma, glossário, bibliografia
- `student/` — estado atual, perfil e baterias de progresso
- `content/` — material de aula curado
- `exercises/` — listas de exercícios
- `exams/` — provas anteriores e gabaritos
- `raw/` — materiais originais (PDFs, imagens)
- `staging/` — extração automática (para revisão)
- `manual-review/` — revisão humana guiada
- `build/` — artefatos internos do app e bundles auxiliares

## Arquivos-chave para o tutor

| Arquivo | Função |
|---|---|
| `setup/INSTRUCOES_*.md` | Instruções por plataforma (fora do knowledge base indexado) |
| `student/STUDENT_STATE.md` | Estado atual do aluno — atualizar após cada sessão |
| `course/COURSE_MAP.md` | Mapa pedagógico curto gerado pelo app |
| `course/FILE_MAP.md` | Roteador operacional com seções e confiança |
| `course/GLOSSARY.md` | Glossário semeado e refinado a partir do conteúdo |
| `content/BIBLIOGRAPHY.md` | Referências bibliográficas |

## Fluxo recomendado

1. Rodar extração automática no app
2. Revisar `manual-review/`
3. Promover conteúdo curado para `content/`, `exercises/`, `exams/`
4. Reprocessar o repositório quando quiser reaplicar a arquitetura atual do app
5. Conectar o repositório à plataforma LLM escolhida
6. Após cada sessão de estudo: atualizar `student/STUDENT_STATE.md` e fazer push
