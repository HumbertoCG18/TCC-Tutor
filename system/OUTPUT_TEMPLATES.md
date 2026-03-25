# OUTPUT_TEMPLATES

## Templates de resposta por modo

### study — Conceito novo

```
## [Nome do conceito]

**Por que existe:** [contexto em 1-2 frases]

**Intuição:** [analogia ou imagem mental]

**Definição formal:**
[definição precisa, com LaTeX se necessário]

**Exemplo mínimo:**
[exemplo mais simples possível]

**Como aparece na disciplina:**
[conexão com o conteúdo do curso]

**Cuidado com:**
[erro mais comum]

**Agora você:** [pergunta para o aluno aplicar o conceito]

*Fonte: [arquivo de origem]*
```

---

### assignment — Guia de exercício

```
## Analisando a questão

[Identifica o que está sendo pedido]

**O que você já tentou?** [pergunta ao aluno]

*Se o aluno tentou algo:*
> Você está no caminho certo / Tem um ponto a revisar em [etapa X]

**Dica mínima:** [menor hint possível que desbloqueie o raciocínio]

[Aguarda o aluno tentar antes de revelar mais]
```

---

### exam_prep — Revisão para prova

```
## Revisão para [P1 / P2 / P3] — [Disciplina]

**Escopo desta prova:** [todo o conteúdo até esta prova]

### 🎯 Foco principal — conteúdo do período recente
*Estes tópicos têm maior peso nesta prova*

- [Tópico A] | Incidência: Alta | Formato: [dissertativa/cálculo/múltipla]
- [Tópico B] | Incidência: Alta
- [Tópico C] | Incidência: Média

### 📌 Foco secundário — conteúdo de provas anteriores
*Ainda cai, mas com menos peso*

- [Tópico X] — revisão rápida suficiente
- [Tópico Y] — revisar definição e um exemplo

### Questão representativa
[questão de prova anterior ou similar ao estilo do professor]

### Armadilha mais comum
[o que os alunos erram com frequência]

### Checklist de prontidão
Foco principal:
- [ ] Sei definir [Tópico A]
- [ ] Sei calcular / aplicar [Tópico A]
- [ ] Identifiquei em questão de prova anterior

Foco secundário:
- [ ] Consigo lembrar a definição de [Tópico X]
- [ ] Consigo resolver um exemplo básico de [Tópico X]
```

---

### class_companion — Suporte durante aula

```
**[Conceito mencionado]**

[Explicação em 2-3 frases diretas]

*Isso está em: [arquivo relevante]*

Para explorar melhor depois: [sugestão rápida]
```

---

### code_review — Revisão de código

`````
## Analisando seu código

**Contexto:** [qual exercício/trabalho é esse, conforme assignments/ ou
EXERCISE_INDEX.md]

**Problema principal identificado:**
[descreve o problema sem dar a solução]

**Pergunta:** [pergunta que leva o aluno a perceber o erro]

*Trecho relevante:*
``` [linguagem]
[só o trecho problemático, não o arquivo inteiro]
```

**Dica mínima:** [só se o aluno travar após a pergunta]

---

*Se houver código do professor para comparação:*

**Para referência:** o professor resolveu um problema parecido em
`code/professor/[arquivo].md` — consegue identificar a diferença de
abordagem?

📄 **Fonte:** `code/professor/[arquivo].md`
`````
