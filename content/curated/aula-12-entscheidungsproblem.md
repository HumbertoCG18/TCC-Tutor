<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **O Programa de Hilbert**
  - David Hilbert (1862–1943)
  - Citação Famosa (1930)
- **Os Três Problemas de Hilbert**
- **Fundamentos da Matemática**
  - O Sonho
- **O Problema de Decisão**
  - Definição (Hilbert e Ackermann, 1928)
  - Exemplo
  - Por que “Entscheidungsproblem”?
  - O Nome Alemão
  - Tradução
- **Lógica de Primeira Ordem (de Predicados)**
  - Componentes
  - Exemplos de Fórmulas
  - Validade e Satisfatibilidade
  - Definições
  - Relação
  - Formulação Precisa do Entscheidungsproblem
  - O Problema
  - Questão Central
  - Observação Importante
  - O Que é um “Procedimento Efetivo”?
  - Antes de 1936
  - Problema
  - Em 1936
- **Alan Turing (1912–1954)**
  - Insight de Turing
  - Alonzo Church (1903–1995)
- **Cálculo Lambda**
  - A Tese de Church-Turing
  - Tese de Church-Turing
  - Cálculo Lambda: Breve Introdução
  - Sintaxe
  - Exemplos
  - Regra de Redução ( $\beta$ -redução)
  - Equivalência dos Modelos
  - Teorema
  - Implicação
  - Funções Recursivas
  - Funções $\mu$ -Recursivas
  - Resultado
- **O Teorema de Church-Turing**
  - Teorema (Church 1936, Turing 1936)
  - Consequência Histórica
  - Estratégia da Prova de Turing
  - Ideia Geral
- **Codificando MTs em Lógica**
  - Idea da Codificação
  - Elementos da Codificação
  - Esboço da Fórmula
  - Estrutura de $\phi_{M,w}$
  - Exemplo de Axioma de Transição
  - Completude da Redução
  - Teorema
  - A Prova de Church
  - Abordagem de Church
  - Problema Indecidível em $\lambda$ -calculus
- **Semi-decidibilidade**
  - O Problema de Decisão é Semi-decidível
  - Procedimento (Enumeração de Provas)
  - Problema
  - Teorema da Completude (Gödel, 1930)
- **Fragmentos Decidíveis**
  - Nem Tudo é Indecidível
  - Exemplos Decidíveis
  - Fragmentos Indecidíveis
  - Outros Desenvolvimentos
- **O Programa de Hilbert**
  - Consequências
  - Paradoxo
- **Resumo**
- **Pontos Principais**
- **Exercício 1: Conceitos Básicos**
  - Exercício 2: Lógica de Primeira Ordem
  - Exercício 3: Cálculo Lambda
- **Exercício 4: Codificação em Lógica**
  - Exercício 5: Fragmentos Decidíveis
  - Exercício 6: Consequências
  - Exercício 7: Reflexão Histórica
- **Desafio**
  - Teorema de Trakhtenbrot (1950)
- **Contraste**
- **Referências I**
- **Referências II**
- **Referências III**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# O Problema de Decisão

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 12  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

17 de abril de 2026

The logo of the Pontifical Catholic University of Rio Grande do Sul (PUCRS) Escola Politécnica. It features a crest with a shield, a cross, and a sun, with the text "PUCRS" below it. To the right of the crest, the words "ESCOLA POLITÉCNICA" are written in a bold, blue, sans-serif font.

Logo of PUCRS Escola Politécnica

{1}------------------------------------------------
## Sumário

- 1** Contexto Histórico
- 2** Formalização da Computação
- 3** Solução Negativa
- 4** Exercícios

A faint, grayscale watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two smaller shields with a repeating pattern of stylized trees. The motto 'AD VERVM DVOCIT' is inscribed on a ribbon at the bottom of the shield. The entire emblem is set against a background of ornate, classical-style flourishes.

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8c378a184b5ae4d1605cb74d7b7a7e3f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-66e8a5ee8999de53e962b143d5cf86ad_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
## O Programa de Hilbert
### David Hilbert (1862–1943)

Matemático alemão que buscava estabelecer fundamentos sólidos para toda a matemática.

- **1900:** Apresenta 23 problemas no Congresso Internacional de Matemáticos
- O segundo problema perguntava sobre a **consistência** da aritmética
- Hilbert acreditava que todo problema matemático tem solução
### Citação Famosa (1930)

“Wir müssen wissen. Wir werden wissen.”  
“Devemos saber. Saberemos.”

{3}------------------------------------------------
## Os Três Problemas de Hilbert
## Fundamentos da Matemática

Hilbert propôs que a matemática deveria ser:

**1 Completa:** Toda afirmação verdadeira pode ser provada

$$\forall \phi : \phi \text{ verdadeiro} \Rightarrow \vdash \phi$$

**2 Consistente:** Não existem contradições

$$\nexists \phi : \vdash \phi \wedge \vdash \neg \phi$$

**3 Decidível:** Existe um procedimento mecânico para determinar se qualquer afirmação é verdadeira ou falsa
### O Sonho

Reduzir toda a matemática a manipulação de símbolos seguindo regras precisas: um “algoritmo universal” para a verdade matemática.

{4}------------------------------------------------
## O Problema de Decisão
### Definição (Hilbert e Ackermann, 1928)

**Problema de Decisão** (Problema da Decisão):

Dado um sistema formal  $S$  e uma fórmula  $\phi$  em  $S$ , existe um procedimento **efetivo** (algoritmo) que determina se  $\phi$  é um teorema de  $S$ ?

- “Entscheidung” = decisão em alemão
- Hilbert esperava uma resposta **positiva**
- Isso significaria que a matemática poderia ser “mecanizada”
### Exemplo

Dada a fórmula  $\forall x \forall y (x + y = y + x)$ , um algoritmo deveria poder determinar se ela é provável nos axiomas da aritmética.

{5}------------------------------------------------
### Por que “Entscheidungsproblem”?
### O Nome Alemão

O problema ficou conhecido pelo nome alemão por razões históricas:

- Formulado por matemáticos alemães (Hilbert, Ackermann)
- A escola de lógica de Göttingen era predominante
- O termo já era estabelecido quando Turing o resolveu
### Tradução

- **Entscheidung** = decisão
- **Problem** = problema
- Em português: **Problema da Decisão**

{6}------------------------------------------------
## Lógica de Primeira Ordem (de Predicados)
### Componentes

- **Constantes:**  $a, b, c, \dots$
- **Variáveis:**  $x, y, z, \dots$
- **Funções:**  $f, g, h, \dots$
- **Predicados:**  $P, Q, R, \dots$
- **Conectivos:**  $\wedge, \vee, \neg, \rightarrow, \leftrightarrow$
- **Quantificadores:**  $\forall$  (para todo),  $\exists$  (existe)
### Exemplos de Fórmulas

- $\forall x(P(x) \rightarrow Q(x))$  — “Todo  $P$  é  $Q$ ”
- $\exists x(P(x) \wedge Q(x))$  — “Existe algo que é  $P$  e  $Q$ ”
- $\forall x \exists y(R(x, y))$  — “Para todo  $x$ , existe  $y$  tal que  $R(x, y)$ ”

{7}------------------------------------------------
### Validade e Satisfatibilidade
### Definições

**Válida** Uma fórmula é **válida** se é verdadeira em **toda** interpretação.

$$\models \phi$$

**Satisfatível** Uma fórmula é **satisfatível** se é verdadeira em **alguma** interpretação.

**Insatisfatível** Uma fórmula é **insatisfatível** se é falsa em **toda** interpretação.
### Relação

$\phi$  é válida  $\iff \neg\phi$  é insatisfatível
#### Exemplo

$\forall x(P(x) \vee \neg P(x))$  é **válida** (lei do terceiro excluído)

{8}------------------------------------------------
### Formulação Precisa do Entscheidungsproblem
### O Problema

**Entrada:** Uma fórmula  $\phi$  da lógica de primeira ordem.

**Pergunta:**  $\phi$  é válida?

Equivalentemente:  $\neg\phi$  é insatisfatível?
### Questão Central

Existe um **algoritmo** que, dada qualquer fórmula  $\phi$ , sempre para e responde corretamente se  $\phi$  é válida ou não?
### Observação Importante

Note que “algoritmo” não estava formalmente definido em 1928. A resolução do Entscheidungsproblem exigiu primeiro **definir** o que é computação.

{9}------------------------------------------------
### O Que é um “Procedimento Efetivo”?
### Antes de 1936

O conceito de “algoritmo” era intuitivo:

- Sequência finita de instruções
- Cada passo é “simples” e determinístico
- Executável mecanicamente, sem criatividade
### Problema

Para provar que algo é **impossível** de computar, precisamos de uma definição **formal** e **precisa** do que significa “computar”.
### Em 1936

Três formalizações independentes, todas equivalentes:

- **Alan Turing**: Máquinas de Turing
- **Alonzo Church**: Cálculo Lambda
- **Kurt Gödel**: Funções Recursivas

{10}------------------------------------------------
## Alan Turing (1912–1954)

- Matemático e lógico britânico
- “On Computable Numbers” (1936)
- Introduziu as **Máquinas de Turing**
- Provou a indecidibilidade do Entscheidungsproblem
- Trabalhou em criptografia (Enigma) na WWII
- Pioneiro da Inteligência Artificial
- Considerado o “pai da computação”
### Insight de Turing

Modelar o processo de um matemático fazendo cálculos com papel e lápis.

{11}------------------------------------------------
### Alonzo Church (1903–1995)

- Matemático e lógico americano
- Professor em Princeton
- Orientador de Turing no doutorado
- Criou o **Cálculo Lambda** ( $\lambda$ -calculus)
- Provou independentemente a indecidibilidade
- Sua prova foi publicada meses antes de Turing
## Cálculo Lambda

Formalismo baseado em funções:

$$\lambda x.x + 1$$

representa  $f(x) = x + 1$

{12}------------------------------------------------
### A Tese de Church-Turing
### Tese de Church-Turing

**Todo** procedimento efetivo (algoritmo) pode ser realizado por uma Máquina de Turing.

Equivalentemente: Máquinas de Turing capturam precisamente a noção intuitiva de “computabilidade”.
#### Nota Importante

Isso é uma **tese**, não um teorema:

- Não pode ser provada (relaciona conceito informal com formal)
- Mas tem forte evidência a favor
- Os modelos de computação conhecidos equivalem a MTs
#### Evidência

MT  $\equiv$   $\lambda$ -calculus  $\equiv$  Funções Recursivas  $\equiv$  Máquinas de Post  $\equiv$  Linguagens de programação modernas

A faint, stylized watermark in the background on the right side of the slide. It features a silhouette of a Turing machine and the letters 'OVCI' arranged vertically.

Faint background watermark of a Turing machine and the text 'OVCI'.

{13}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-f38515370322934490a456fa51195cdf_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of a Turing machine and the text 'OVCI'.
<!-- /IMAGE_DESCRIPTION -->
### Cálculo Lambda: Breve Introdução
### Sintaxe

Termos do  $\lambda$ -calculus:

- **Variáveis:**  $x, y, z, \dots$
- **Abstração:**  $\lambda x.M$  (função que mapeia  $x$  para  $M$ )
- **Aplicação:**  $(M N)$  (aplicar  $M$  a  $N$ )
### Exemplos

- Identidade:  $\lambda x.x$
- Constante:  $\lambda x.\lambda y.x$
- Aplicação:  $(\lambda x.x + 1) 5 = 6$
### Regra de Redução ( $\beta$ -redução)

$$(\lambda x.M) N \rightarrow_{\beta} M[x := N]$$

A faint, stylized illustration of a historical figure, possibly a mathematician or philosopher, is visible in the background on the right side of the slide. The figure is depicted in a classical style, holding a staff or rod, and standing next to what appears to be a scale or a similar scientific instrument. The illustration is rendered in a light, semi-transparent manner, allowing the text of the slide to remain legible.

Faint background illustration of a historical figure, possibly a mathematician or philosopher, holding a staff and standing next to a scale.

{14}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-af876fec8a4c488aa2ef84e6724c1375_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background illustration of a historical figure, possibly a mathematician or philosopher, holding a staff and standing next to a scale.
<!-- /IMAGE_DESCRIPTION -->
### Equivalência dos Modelos
### Teorema

Os seguintes modelos computacionais são **equivalentes**:

- 1 Máquinas de Turing
- 2 Cálculo Lambda
- 3 Funções  $\mu$ -recursivas
- 4 Máquinas de registradores
- 5 Gramáticas irregulares

Uma função é computável em um modelo  $\iff$  é computável em todos.
### Implicação

Podemos usar qualquer modelo para provar resultados sobre computabilidade. Resultados negativos (indecidibilidade) valem para **todos** os modelos.

{15}------------------------------------------------
### Funções Recursivas
#### Funções Primitivas Recursivas

Construídas a partir de:

- **Zero:**  $Z(n) = 0$
- **Sucessor:**  $S(n) = n + 1$
- **Projeção:**  $P_i^k(x_1, \dots, x_k) = x_i$
- **Composição:**  $h = f \circ (g_1, \dots, g_k)$
- **Recursão Primitiva**
### Funções $\mu$ -Recursivas

Primitivas recursivas + **Minimização:**

$$\mu y[f(x, y) = 0] = \text{menor } y \text{ tal que } f(x, y) = 0$$
### Resultado

Funções  $\mu$ -recursivas = Funções Turing-computáveis

{16}------------------------------------------------
## O Teorema de Church-Turing
### Teorema (Church 1936, Turing 1936)

O **Entscheidungsproblem** é **indecidível**.

Não existe algoritmo que, dada uma fórmula  $\phi$  da lógica de primeira ordem, sempre para e decide corretamente se  $\phi$  é válida.
### Consequência Histórica

O sonho de Hilbert de mecanizar a matemática é **impossível**.

Existem verdades matemáticas que nenhum procedimento mecânico pode descobrir sistematicamente.

{17}------------------------------------------------
### Estratégia da Prova de Turing
### Ideia Geral

- 1 Mostrar que o Problema da Parada pode ser **codificado** como um problema de lógica de primeira ordem
  - 2 Se o Entscheidungsproblem fosse decidível, o Problema da Parada seria decidível
  - 3 Mas o Problema da Parada é indecidível
  - 4 Logo, o Entscheidungsproblem é indecidível

Diagram illustrating a reduction from the Halting Problem to a Decision Problem:

Problema da Parada  $\xrightarrow{\text{redução}}$  Entscheidungsproblem

indecidível  $\Rightarrow$  indecidível

Diagram showing a reduction from the Halting Problem to a Decision Problem. The Halting Problem is labeled as undecidable, and the reduction implies the Decision Problem is also undecidable.

{18}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-51db757d054ce1ce83c436a3578b56ca_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram showing a reduction from the Halting Problem to a Decision Problem.
<!-- /IMAGE_DESCRIPTION -->
## Codificando MTs em Lógica
### Idea da Codificação

Dada uma MT  $M$  e entrada  $w$ , construir uma fórmula  $\phi_{M,w}$  tal que:

$$M \text{ para em } w \iff \phi_{M,w} \text{ é válida}$$
### Elementos da Codificação

- **Predicados de estado:**  $Q_i(t)$  — “no tempo  $t$ , está no estado  $q_i$ ”
- **Predicados de posição:**  $H(p, t)$  — “no tempo  $t$ , cabeça está em  $p$ ”
- **Predicados de símbolo:**  $T_a(p, t)$  — “no tempo  $t$ , posição  $p$  tem símbolo  $a$ ”
- **Axiomas de transição:** codificam  $\delta$
- **Configuração inicial:** estado  $q_0$ , entrada  $w$  na fita
- **Condição de parada:**  $\exists t : Q_{halt}(t)$

Faint background watermark of a classical building with columns and a triangular pediment.

{19}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-86b435d3ff1e3454a85a4c9e3e5e4ff4_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of a classical building with columns and a triangular pediment.
<!-- /IMAGE_DESCRIPTION -->
### Esboço da Fórmula
### Estrutura de $\phi_{M,w}$

$$\begin{aligned}\phi_{M,w} = & \text{ (configuração inicial)} \\ & \wedge \text{ (axiomas de unicidade)} \\ & \wedge \text{ (axiomas de transição)} \\ & \wedge \text{ (persistência da fita)} \\ & \rightarrow \exists t : Q_{accept}(t)\end{aligned}$$
### Exemplo de Axioma de Transição

Se  $\delta(q_i, a) = (q_j, b, R)$ :

$$\begin{aligned}\forall t \forall p : (Q_i(t) \wedge H(p, t) \wedge T_a(p, t)) \rightarrow \\ (Q_j(t + 1) \wedge H(p + 1, t + 1) \wedge T_b(p, t + 1))\end{aligned}$$

{20}------------------------------------------------
### Completude da Redução
### Teorema

A fórmula  $\phi_{M,w}$  é válida se e somente se  $M$  para e aceita  $w$ .
#### Prova ( $\Rightarrow$ )

Se  $\phi_{M,w}$  é válida, então em particular é verdadeira na interpretação “padrão” onde:

- O domínio são os números naturais (tempos e posições)
- Os predicados têm significado pretendido

Logo, existe  $t$  tal que  $Q_{accept}(t)$  é verdade, i.e.,  $M$  aceita  $w$ .
#### Prova ( $\Leftarrow$ )

Se  $M$  aceita  $w$  em  $t$  passos, a interpretação padrão satisfaz  $\phi_{M,w}$ . Pode-se mostrar que  $\phi_{M,w}$  é válida em **toda** interpretação.

{21}------------------------------------------------
### A Prova de Church
### Abordagem de Church

Church usou o  $\lambda$ -calculus:

- 1 Definiu “ $\lambda$ -definibilidade” como noção de computabilidade
- 2 Mostrou que certas propriedades de termos lambda são indecidíveis
- 3 Codificou isso como problema de lógica
### Problema Indecidível em $\lambda$ -calculus

Dados termos  $M$  e  $N$ , decidir se  $M =_{\beta} N$  (se  $M$  reduz para  $N$ ) é indecidível.
#### Nota Histórica

A prova de Church foi publicada em abril de 1936, a de Turing em novembro de 1936. Turing reconheceu a prioridade de Church, mas sua abordagem com máquinas foi considerada mais intuitiva.

{22}------------------------------------------------
## Semi-decidibilidade
### O Problema de Decisão é Semi-decidível

Embora não possamos **decidir** se  $\phi$  é válida, podemos **reconhecer** fórmulas válidas:
### Procedimento (Enumeração de Provas)

- 1 Enumere todas as provas possíveis:  $\pi_1, \pi_2, \pi_3, \dots$
- 2 Para cada  $\pi_i$ , verifique se é uma prova válida de  $\phi$
- 3 Se encontrar, aceite
### Problema

Se  $\phi$  não é válida, este procedimento **nunca para**.
### Teorema da Completude (Gödel, 1930)

$\phi$  é válida  $\iff \phi$  é provável

Portanto, o procedimento acima **eventualmente** encontra uma prova se  $\phi$  é válida.

Watermark logo of VIT (Vitória, Espírito Santo) featuring a scale of justice and the text 'VIT'.

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-47ee04685ea17359b392963a71753a41_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark logo of VIT (Vitória, Espírito Santo) featuring a scale of justice and the text 'VIT'.
<!-- /IMAGE_DESCRIPTION -->
## Fragmentos Decidíveis
### Nem Tudo é Indecidível

Certos **fragmentos** da lógica de primeira ordem são decidíveis:
### Exemplos Decidíveis

- **Lógica Proposicional:** tabelas-verdade, DPLL, SAT solvers
- **Lógica Monádica:** apenas predicados unários
- **Classe de Bernays-Schönfinkel:**  $\exists^* \forall^*$  sem funções
- **Aritmética de Presburger:** adição, sem multiplicação
- **Teoria de conjuntos finitos**
### Fragmentos Indecidíveis

- Qualquer fragmento que possa expressar aritmética básica
- Lógica com dois predicados binários

{24}------------------------------------------------
### Outros Desenvolvimentos
## O Programa de Hilbert

- **1931:** Gödel mostra incompletude da aritmética
- **1936:** Church e Turing mostram indecidibilidade
- O programa formalista de Hilbert é **impossível**
### Consequências

- A matemática não pode ser completamente mecanizada
- Existem limites fundamentais para o conhecimento algorítmico
- Criatividade e intuição matemática não são redutíveis a regras
### Paradoxo

Provar que algo é impossível de provar algoritmicamente requer primeiro **definir** o que é um algoritmo — e isso levou ao nascimento da Ciência da Computação!

{25}------------------------------------------------
## Resumo
## Pontos Principais

- O **Entscheidungsproblem** de Hilbert perguntava se existe algoritmo para decidir validade em lógica
- **Church** (cálculo lambda) e **Turing** (máquinas) formalizaram “algoritmo”
- A **Tese de Church-Turing** afirma que MTs capturam toda computação
- O Entscheidungsproblem é **indecidível** (redução do Problema da Parada)
- O problema é **semi-decidível** (completude de Gödel)

{26}------------------------------------------------
## Exercício 1: Conceitos Básicos

- 1 Explique a diferença entre os três requisitos de Hilbert para a matemática: completude, consistência e decidibilidade.
- 2 Por que o Problema da Parada precisava ser resolvido **antes** de resolver o Entscheidungsproblem?
- 3 O que significa dizer que a Tese de Church-Turing é uma “tese” e não um “teorema”?

A faint, grayscale watermark of the coat of arms of the University of Coimbra is visible in the background. It features a shield with a star and the motto 'AD VERVM DVOCIT' (To the truth it calls) on a ribbon below.

Faint watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{27}------------------------------------------------
### Exercício 2: Lógica de Primeira Ordem

Classifique cada fórmula como válida, satisfatível (mas não válida), ou insatisfatível:

- 1  $\forall x(P(x) \rightarrow P(x))$
- 2  $\forall xP(x) \rightarrow \exists xP(x)$
- 3  $\exists xP(x) \rightarrow \forall xP(x)$
- 4  $\forall x(P(x) \wedge \neg P(x))$
- 5  $P(a) \wedge \neg P(a)$
- 6  $\forall x\forall y(R(x, y) \rightarrow R(y, x)) \wedge \exists x\exists y(R(x, y) \wedge \neg R(y, x))$

A faint, grayscale watermark of the coat of arms of the University of Coimbra is visible in the background. It features a shield with a cross and a central emblem, topped by a crown and flanked by two figures. Below the shield is a ribbon with the Latin motto 'AD VERVM DVKIT'.

Faint watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVKIT'.

{28}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-83db47f9541df5f9be73289497eaae90_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVKIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Cálculo Lambda

- 1 Reduz a o termo  $(\lambda x. \lambda y. x)$  a  $b$  usando  $\beta$ -redução.
- 2 O termo  $\Omega = (\lambda x. x x)(\lambda x. x x)$  pode ser reduzido a uma forma normal? O que isso representa computacionalmente?
- 3 Escreva um termo lambda que representa a função  $f(x, y) = x + y$  (assuma que você tem constantes numéricas e  $+$ ).
- 4 Por que a equivalência  $M =_{\beta} N$  é indecidível? Relacione com o Problema da Parada.

{29}------------------------------------------------
## Exercício 4: Codificação em Lógica

Considere uma MT simples com:

- Estados:  $q_0, q_1, q_{halt}$
  - Alfabeto:  $\{0, 1, \sqcup\}$
  - Transição:  $\delta(q_0, 1) = (q_1, 0, R)$
- 1 Escreva a fórmula de primeira ordem que codifica esta transição.
  - 2 Escreva a fórmula que representa a configuração inicial com entrada  $w = 11$ .
  - 3 Que predicados você precisaria para expressar “a máquina eventualmente para”?

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and the motto 'D VERVM DVCT'.

{30}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-c2c3abb173421fc58a8c014e41562eb3_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and the motto 'D VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 5: Fragmentos Decidíveis

- 1 A lógica proposicional é decidível. Descreva um algoritmo para decidir se uma fórmula proposicional é uma tautologia.
- 2 Por que a aritmética de Presburger (com adição mas sem multiplicação) é decidível, enquanto a aritmética de Peano (com adição e multiplicação) não é?
- 3 A teoria da ordem dos números reais  $(\mathbb{R}, <)$  é decidível (Tarski). Por que isso não contradiz a indecidibilidade do Entscheidungsproblem?

{31}------------------------------------------------
### Exercício 6: Consequências

- 1 Se o Entscheidungsproblem fosse decidível, que impacto isso teria na prática matemática?
- 2 A indecidibilidade do Entscheidungsproblem significa que existem teoremas matemáticos que **nunca** poderão ser provados? Justifique.
- 3 Compare os resultados de Gödel (incompletude) com os de Church-Turing (indecidibilidade). Qual é a relação entre eles?

A faint, grayscale watermark of the coat of arms of the University of Coimbra is visible in the background. It features a shield with a cross and other heraldic elements, topped with a crown and flanked by two figures. Below the shield is a ribbon with the Latin motto 'AD VERVM DVCT'.

Faint watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVCT'.

{32}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-aa7a4ea43951479b7e7b4c530ea5bc2d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 7: Reflexão Histórica

- 1 Por que o trabalho de Turing é considerado o “nascimento da Ciência da Computação”, mesmo tendo um resultado negativo?
- 2 Turing e Church chegaram ao mesmo resultado usando métodos diferentes. Por que isso fortalece a Tese de Church-Turing?
- 3 A citação de Hilbert “Devemos saber. Saberemos.” foi pronunciada um dia antes de Gödel apresentar seus teoremas de incompletude. Comente sobre a ironia histórica.

{33}------------------------------------------------
## Desafio
### Teorema de Trakhtenbrot (1950)

O problema de decidir se uma fórmula de primeira ordem é satisfatível em um **domínio finito** é indecidível.

- 1 Por que este resultado é surpreendente? (Afinal, podemos testar todas as interpretações finitas até um certo tamanho.)
- 2 Esboce como você reduziria o Problema da Parada a este problema.  
*Dica:* Considere uma fórmula que diz “existe uma sequência de configurações da MT que termina em estado de aceitação”.
## Contraste

Compare com a lógica proposicional, onde satisfatibilidade (SAT) é decidível (embora NP-completo).

{34}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009. ISBN: 978-0521424264.
- [2] Alonzo Church. “An Unsolvable Problem of Elementary Number Theory”. Em: *American Journal of Mathematics* 58.2 (1936), pp. 345–363. DOI: [10.2307/2371045](https://doi.org/10.2307/2371045).
- [3] Martin Davis, ed. *The Undecidable: Basic Papers on Undecidable Propositions, Unsolvable Problems and Computable Functions*. Raven Press, 1965.
- [4] Kurt Gödel. “Die Vollständigkeit der Axiome des logischen Funktionenkalküls”. Em: *Monatshefte für Mathematik und Physik* 37.1 (1930), pp. 349–360. DOI: [10.1007/BF01696781](https://doi.org/10.1007/BF01696781).

{35}------------------------------------------------
## Referências II

- [5] David Hilbert e Wilhelm Ackermann. *Grundzüge der theoretischen Logik*. Berlin: Springer, 1928.
- [6] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006. ISBN: 978-0321455369.
- [7] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994. ISBN: 978-0201530827.
- [8] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012. ISBN: 978-0133468779.
- [9] Alan M. Turing. “On Computable Numbers, with an Application to the Entscheidungsproblem”. Em: *Proceedings of the London Mathematical Society* s2-42.1 (1937), pp. 230–265. DOI: [10.1112/plms/s2-42.1.230](https://doi.org/10.1112/plms/s2-42.1.230).

{36}------------------------------------------------
## Referências III

- [10] Alan M. Turing. “On Computable Numbers, with an Application to the Entscheidungsproblem. A Correction”.  
Em: *Proceedings of the London Mathematical Society*  
s2-43.6 (1938), pp. 544–546. DOI:  
[10.1112/plms/s2-43.6.544](https://doi.org/10.1112/plms/s2-43.6.544).

Faint watermark of the University of Cambridge crest, featuring a shield with four lions and a closed book, surrounded by a ribbon with the Latin motto 'AD VERVM DVCTIT'.

<!-- IMAGE_DESCRIPTION: datalab-aef7fa3e55b1477058e5b4f630f21d12_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Cambridge crest, featuring a shield with four lions and a closed book, surrounded by a ribbon with the Latin motto 'AD VERVM DVCTIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS Escola Politécnica
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->
