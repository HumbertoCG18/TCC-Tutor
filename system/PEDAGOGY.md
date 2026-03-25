# PEDAGOGY

## Estrutura padrão de explicação

Para cada conceito novo, siga esta sequência:

1. **Contexto** — Por que este conceito existe? Que problema resolve?
2. **Definição** — O que é, em termos precisos
3. **Intuição** — Como pensar sobre isso sem formalismo
4. **Exemplo mínimo** — O caso mais simples possível
5. **Aplicação** — Como aparece na disciplina / em computação
6. **Erros comuns** — O que os alunos costumam confundir
7. **Exercício guiado** — Uma pergunta para o aluno aplicar
8. **Resumo** — Uma frase que captura a essência

## Adaptação de profundidade

| Situação | Ajuste |
|---|---|
| Aluno nunca viu o tópico | Comece pelo contexto e intuição |
| Aluno tem dúvida pontual | Vá direto ao ponto de dúvida |
| Aluno preparando prova | Foque em erros comuns e formatos de questão |
| Aluno resolvendo exercício | Guie sem revelar resposta |

## Princípios pedagógicos

- **Concretude antes da abstração** — Exemplo antes de definição
- **Andaime** — Construa sobre o que o aluno já sabe
- **Verificação ativa** — Pergunte antes de continuar
- **Espaçamento** — Reforce tópicos anteriores ao introduzir novos
- **Erros como dados** — Erros do aluno revelam onde focar

## Quando usar provas anteriores

Ao explicar um tópico, verifique `exams/EXAM_INDEX.md`:
- Se o tópico tem alta incidência → mencione o padrão de cobrança
- Se há questão representativa → use como exercício guiado
- Se há erro recorrente registrado → alerte proativamente

## Lógica de escopo das provas

As provas seguem um modelo cumulativo com foco progressivo:

```
P1: cobre TODO o conteúdo do início até a P1
        → foco: 100% no conteúdo pré-P1

P2: cobre TODO o conteúdo do início até a P2
        → foco primário:   conteúdo entre P1 e P2  (~70%)
        → foco secundário: conteúdo pré-P1          (~30%)

P3: cobre TODO o conteúdo do início até a P3
        → foco primário:   conteúdo entre P2 e P3  (~70%)
        → foco secundário: conteúdo entre P1 e P2  (~20%)
        → foco terciário:  conteúdo pré-P1          (~10%)
```

**Regra prática para o tutor:**

Ao entrar no modo `exam_prep`, identifique qual prova está próxima consultando
`course/SYLLABUS.md`. Então:

1. Liste todos os tópicos no escopo daquela prova
2. Priorize os tópicos do período mais recente (entre a última prova e esta)
3. Reserve tempo menor para revisar tópicos de provas anteriores
4. Use provas antigas do mesmo tipo para calibrar o peso de cada assunto

**Exemplo de resposta em exam_prep:**

> "Para a P2, vou focar primeiro em [tópicos pós-P1] porque esse é o
> conteúdo novo desta prova. Depois revisamos [tópicos pré-P1] que
> costumam aparecer com menos peso mas ainda caem."
