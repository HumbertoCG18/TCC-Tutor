<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **1 Decidibilidade e Reconhecibilidade**
- **2 Máquinas de Turing Universais**
- **3 Indecidibilidade**
- **4 Reduções**
- **5 Exercícios**
- **Recapitulação: Classes de Linguagens**
  - Linguagem Turing-Reconhecível (R.E.)
  - Linguagem Turing-Decidível (Recursiva)
  - Relação
  - Exemplos de Linguagens Decidíveis
  - Linguagens Regulares
  - Linguagens Livres de Contexto
  - Problemas Aritméticos
  - Problemas de Decisão sobre DFAs
  - Problemas de Decisão sobre GLCs
  - Teorema: Decidível $\iff$ R.E. e co-R.E.
  - Corolário: Existem Linguagens não R.E.
- **A Máquina de Turing Universal**
  - Definição
  - Comportamento
  - Importância
  - Implementação de $U$
  - Estrutura (3 fitas)
  - Algoritmo
  - Propriedades da MT Universal
  - Conexão com Computadores Reais
  - Von Neumann (1945)
  - Interpretadores e Compiladores
  - Máquinas Virtuais
  - O Problema da Parada
  - Definição
  - Teorema (Turing, 1936)
  - Significado
  - Prova: *HALT* é Indecidível
  - Prova por Diagonalização
  - Construção de $D$
  - Contradição
  - Análise da Contradição
  - Conclusão
  - Visualização: Argumento Diagonal
  - $A_{TM}$ é Indecidível
  - Consequências da Indecidibilidade
  - Impossibilidades
  - Teorema de Rice
  - Redução de Problemas
  - Prova por redução de $A_{TM}$
  - Mais Problemas Indecidíveis
  - Hierarquia de Problemas
- **Resumo**
  - Conceitos Principais
  - Exercício 1: Decidibilidade
  - Exercício 2: MT Universal
  - Exercício 3: Indecidibilidade
  - Exercício 4: Reduções
  - Exercício 5: Classificação
  - Desafio: Teorema de Rice
  - Teorema de Rice
- **Referências I**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Linguagens Reconhecíveis e Linguagens Decidíveis; Máquinas de Turing Universais

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 10  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

10 de abril de 2026

Logo of PUCRS (Pontifical University of Rio Grande do Sul)

ESCOLA  
POLITÉCNICA

Faint background watermark of the PUCRS seal featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{1}------------------------------------------------
## Sumário
## 1 Decidibilidade e Reconhecibilidade
## 2 Máquinas de Turing Universais
## 3 Indecidibilidade
## 4 Reduções
## 5 Exercícios

A faint, light gray watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two smaller shields with a repeating pattern of stylized trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVKIT'.

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-669865256db7d33e9cb759eac2e226c8_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVKIT'.
<!-- /IMAGE_DESCRIPTION -->
## Recapitulação: Classes de Linguagens
### Linguagem Turing-Reconhecível (R.E.)

$L$  é **reconhecível** se existe MT  $M$  tal que:

- $(\forall w \in L).A(w)$ , onde  $A(x)$  significa que  $M$  aceita  $w$
- $(\forall w \notin L).?R(w)$ , onde  $?R(x)$  significa que  $M$  rejeita ou não para
### Linguagem Turing-Decidível (Recursiva)

$L$  é **decidível** se existe MT  $M$  onde:

- $(\forall w \in L).A(w)$
- $(\forall w \notin L).R(w)$ , onde  $R(x)$  significa que  $M$  rejeita  $w$  e  $M$  sempre para (decisor).
### Relação

Decidível  $\subset$  Reconhecível  $\subset$  Todas as Linguagens

{3}------------------------------------------------
### Exemplos de Linguagens Decidíveis
### Linguagens Regulares

- $A_{DFA} = \{\langle D, w \rangle : D \text{ é DFA que aceita } w\}$
- Decidível: simule  $D$  em  $w$ , sempre para em  $|w|$  passos.
### Linguagens Livres de Contexto

- $A_{CFG} = \{\langle G, w \rangle : G \text{ é GLC que gera } w\}$
- Decidível: use algoritmo CYK (programação dinâmica).
### Problemas Aritméticos

- $\{(a, b, c) : a + b = c\}$ , verificar soma
- $\{n : n \text{ é primo}\}$ , teste de primalidade (AKS)
- $\{(a, b) : \gcd(a, b) = 1\}$ , coprimos (Euclides)

{4}------------------------------------------------
### Problemas de Decisão sobre DFAs
#### $A_{DFA}$ , Aceitação de DFA

$$A_{DFA} = \{ \langle D, w \rangle : D \text{ é DFA e } D \text{ aceita } w \}$$

**Decidível:** Simule  $D$  em  $w$ .
#### $E_{DFA}$ , Linguagem vazia (aceita nenhuma string)

$$E_{DFA} = \{ \langle D \rangle : L(D) = \emptyset \}$$

**Decidível:** Use busca (BFS/DFS) a partir do estado inicial. Se algum estado final é alcançável, rejeite; senão, aceite.
#### $EQ_{DFA}$ , Equivalência de DFAs

$$EQ_{DFA} = \{ \langle D_1, D_2 \rangle : L(D_1) = L(D_2) \}$$

**Decidível:** Construa DFA para  $(L(D_1) \cap \overline{L(D_2)}) \cup (\overline{L(D_1)} \cap L(D_2))$  e teste se é vazio.

{5}------------------------------------------------
### Problemas de Decisão sobre GLCs
#### $A_{CFG}$ , Aceitação de GLC

$$A_{CFG} = \{ \langle G, w \rangle : G \text{ é GLC e } w \in L(G) \}$$

**Decidível:** Algoritmo CYK em  $O(n^3 |G|)$ .
#### $E_{CFG}$ , Linguagem vazia (gera nenhuma string)

$$E_{CFG} = \{ \langle G \rangle : L(G) = \emptyset \}$$

**Decidível:** Marque variáveis que geram terminais; aceite sse  $S$  não é marcado.
#### $EQ_{CFG}$ , Equivalência de GLCs

$$EQ_{CFG} = \{ \langle G_1, G_2 \rangle : L(G_1) = L(G_2) \}$$

**Indecidível!** Não podemos decidir se duas GLCs geram a mesma linguagem.

{6}------------------------------------------------
### Teorema: Decidível $\iff$ R.E. e co-R.E.
#### Teorema

Uma linguagem  $L$  é decidível se e somente se  $L$  e  $\bar{L}$  são reconhecíveis.
#### Prova

$(\Rightarrow)$  Se  $L$  é decidível:

- O decisor  $M$  reconhece  $L$
- Trocando  $q_{acc}$  e  $q_{rej}$ , obtemos decisor para  $\bar{L}$

$(\Leftarrow)$  Se  $L$  e  $\bar{L}$  são reconhecíveis:

- Sejam  $M_1$  reconhecedor de  $L$  e  $M_2$  de  $\bar{L}$
- Construa  $M$  que simula  $M_1$  e  $M_2$  em paralelo
- Se  $M_1$  aceita, aceite. Se  $M_2$  aceita, rejeite.
- Para toda  $w$ : ou  $w \in L$  ou  $w \in \bar{L}$ , então  $M$  sempre para.

{7}------------------------------------------------
### Corolário: Existem Linguagens não R.E.
#### Corolário

Se  $L$  é reconhecível mas não decidível, então  $\bar{L}$  não é reconhecível.
#### Prova

Suponha  $L$  reconhecível, não decidível, e  $\bar{L}$  reconhecível.  
Pelo teorema anterior,  $L$  seria decidível. Contradição!
#### Exemplo

O problema da parada  $HALT$  é reconhecível mas não decidível.  
Logo,  $\overline{HALT}$  não é reconhecível!  
Existem entradas  $(M, w)$  para as quais não podemos nem confirmar que  $M$  não para.

{8}------------------------------------------------
## A Máquina de Turing Universal
### Definição

Uma **MT Universal**  $U$  é uma MT que pode simular qualquer outra MT:

$$U(\langle M, w \rangle) = M(w)$$

para toda MT  $M$  e entrada  $w$ .
### Comportamento

- Se  $M$  aceita  $w$ , então  $U$  aceita  $\langle M, w \rangle$
- Se  $M$  rejeita  $w$ , então  $U$  rejeita  $\langle M, w \rangle$
- Se  $M$  não para em  $w$ , então  $U$  não para em  $\langle M, w \rangle$
### Importância

- $U$  é um modelo de computação de propósito geral
- Computadores podem simular (emular) outros computadores

{9}------------------------------------------------
### Implementação de $U$
### Estrutura (3 fitas)

- 1 **Fita 1:** Descrição da MT  $M$  (lista de transições)
- 2 **Fita 2:** Conteúdo simulado da fita de  $M$
- 3 **Fita 3:** Estado atual de  $M$
### Algoritmo

- 1 Verifique se  $\langle M, w \rangle$  é codificação válida
- 2 Inicialize: copie  $w$  para Fita 2,  $q_0$  para Fita 3
- 3 Repita:
  - Leia símbolo atual na Fita 2
  - Busque transição para (estado, símbolo) na Fita 1
  - Se não existe, rejeite
  - Atualize: símbolo na Fita 2, posição, estado na Fita 3
  - Se estado é  $q_{acc}$ , aceite. Se é  $q_{rej}$ , rejeite.

{10}------------------------------------------------
### Propriedades da MT Universal
#### $U$ é uma MT válida

$U$  é uma MT com número finito de estados e alfabeto finito, independentemente de qual  $M$  está sendo simulada.
#### $U$ reconhece $A_{TM}$

A linguagem reconhecida por  $U$  é:

$$A_{TM} = \{\langle M, w \rangle : M \text{ é MT que aceita } w\}$$
#### $U$ não decide $A_{TM}$

$U$  pode não parar (quando  $M$  não para em  $w$ ), isto é,  $A_{TM}$  é **indecidível!**

{11}------------------------------------------------
### Conexão com Computadores Reais
### Von Neumann (1945)

Arquitetura de computador baseada na ideia de MT Universal:

- Programa armazenado na memória (como dados)
- CPU executa instruções lidas da memória
- Mesmo hardware executa diferentes programas
### Interpretadores e Compiladores

- **Interpretador:** implementação direta de MT Universal
- Recebe código-fonte + entrada, executa passo a passo
- Exemplos: Python, JavaScript, shells
### Máquinas Virtuais

JVM, CLR: MT Universal para bytecode específico.

{12}------------------------------------------------
### O Problema da Parada
### Definição

$$HALT = \{\langle M, w \rangle : M \text{ é uma MT que para na entrada } w\}$$
### Teorema (Turing, 1936)

$HALT$  é indecidível.
### Significado

Não existe algoritmo que, dado um programa e uma entrada, sempre determina corretamente se o programa termina naquela entrada. Hoje, este é um famoso (e importante) resultado na Ciência da Computação.

{13}------------------------------------------------
### Prova: *HALT* é Indecidível
### Prova por Diagonalização

Suponha que *HALT* seja decidível. Seja  $H$  o decisor:

$$H(\langle M, w \rangle) = \begin{cases} \text{aceita} & \text{se } M \text{ para em } w \\ \text{rejeita} & \text{se } M \text{ não para em } w \end{cases}$$
### Construção de $D$

Construa MT  $D$  que, na entrada  $\langle M \rangle$ :

- 1 Execute  $H(\langle M, \langle M \rangle \rangle)$
- 2 Se  $H$  aceita (i.e.,  $M$  para em  $\langle M \rangle$ ), entre em loop infinito
- 3 Se  $H$  rejeita (i.e.,  $M$  não para em  $\langle M \rangle$ ), aceite
### Contradição

O que acontece quando executamos  $D(\langle D \rangle)$ ?

{14}------------------------------------------------
#### A Máquina $D$ : Fluxo de Execução

```
graph TD; A[Entrada: <M>] --> B[Codifica <M, <M>>]; B --> C[Executa H(<M, <M>>)]; C --> D{H aceita?}; D -- SIM --> E[Loop]; E --> F((D ñ para)); D -- NÃO --> G[Aceita]; G --> H((D para));
```

Flowchart of the execution flow of Turing machine D. It starts with 'Entrada: ', followed by 'Codifica >', then 'Executa H(>)'. A decision diamond 'H aceita?' follows. If 'SIM', it goes to 'Loop' and then to a red circle 'D ñ para'. If 'NÃO', it goes to 'Aceita' and then to a green circle 'D para'.

Faint watermark of the University of Coimbra coat of arms, featuring a crown, a shield with a cross, and the motto 'VERVM DVOCIT'.

{15}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-8740e63f5546e4004e600f24d883acba_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the PUCRS seal featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-bffdddb47fced140f8d17fdc2a29f592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Flowchart of the execution flow of Turing machine D.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-15ee1fd7e4011d0d5dcb11b291fb91d7_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the University of Coimbra coat of arms, featuring a crown, a shield with a cross, and the motto 'VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Análise da Contradição
#### Caso 1: $D$ para em $\langle D \rangle$

- Então  $H(\langle D, \langle D \rangle \rangle)$  aceita
- Então  $D$  entra em loop infinito (pela construção)
- Contradição:  $D$  para e não para ao mesmo tempo!
#### Caso 2: $D$ não para em $\langle D \rangle$

- Então  $H(\langle D, \langle D \rangle \rangle)$  rejeita
- Então  $D$  aceita (pela construção), logo para
- Contradição:  $D$  não para e para ao mesmo tempo!
### Conclusão

Ambos os casos levam a contradição. Logo, o decisor  $H$  não pode existir.  $HALT$  é indecidível.  $\square$

{16}------------------------------------------------
### Visualização: Argumento Diagonal

|       | $\langle M_0 \rangle$ | $\langle M_1 \rangle$ | $\langle M_2 \rangle$ | $\langle M_3 \rangle$ | $\langle D \rangle$ | ... |
|-------|-----------------------|-----------------------|-----------------------|-----------------------|---------------------|-----|
| $M_0$ | <b>P</b>              | N                     | P                     | P                     | ?                   |     |
| $M_1$ | P                     | <b>N</b>              | N                     | P                     | ?                   |     |
| $M_2$ | N                     | P                     | <b>P</b>              | N                     | ?                   |     |
| $M_3$ | P                     | P                     | N                     | <b>N</b>              | ?                   |     |
| $D$   | N                     | P                     | N                     | P                     | <b>?</b>            |     |
| $\vdots$     |                       |                       |                       |                       |                     |     |

- P = para, N = não para
- $D$  é construída para diferir de  $M_i$  na diagonal
- $D(\langle M_i \rangle)$ : para sse  $M_i(\langle M_i \rangle)$  não para
- $D(\langle D \rangle) = ?$

A faint, stylized illustration of a coat of arms featuring a crown, a shield with a star and the letters 'MAC', and a banner with the Latin motto 'AD VERVM DVCTIT'.

{17}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-bcc4b9d57d1d23e256f09d0a0a81be73_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized illustration of a coat of arms featuring a crown, a shield with a star and the letters 'MAC', and a banner with the Latin motto 'AD VERVM DVCTIT'.
<!-- /IMAGE_DESCRIPTION -->
### $A_{TM}$ é Indecidível
#### Definição

$$A_{TM} = \{\langle M, w \rangle : M \text{ é MT que aceita } w\}$$
#### Teorema

$A_{TM}$  é indecidível (mas é reconhecível).
#### Prova

Suponha que  $A_{TM}$  seja decidível com decisor  $A$ . Construa decisor  $H'$  para  $HALT$ : na entrada  $\langle M, w \rangle$ :

- 1 Construa  $M'$  que simula  $M$  em  $w$  e aceita se  $M$  para (aceita ou rejeita)
- 2 Execute  $A(\langle M', w \rangle)$
- 3 Aceite se  $A$  aceita, rejeite se  $A$  rejeita

$H'$  decide  $HALT$  (contradição). Logo  $A_{TM}$  é indecidível.  $\square$

{18}------------------------------------------------
### Consequências da Indecidibilidade
### Impossibilidades

Não existem algoritmos para:

- Determinar se um programa para em uma entrada
- Determinar se dois programas computam a mesma função
- Determinar se um programa tem bugs
- Verificar automaticamente propriedades de programas (Teorema de Rice)
### Teorema de Rice

Seja  $P$  uma propriedade não-trivial de funções computáveis.  
Então  $\{e : \varphi_e \text{ tem propriedade } P\}$  é indecidível.
#### Não-trivial

“Não-trivial” = algumas funções possuem  $P$ , outras não. Exemplo: “a função é total” (nem todas são).

{19}------------------------------------------------
### Redução de Problemas
#### Conceito

Para provar que um problema  $B$  é indecidível:

- 1 Escolha um problema  $A$  que sabemos ser indecidível
- 2 Mostre que se  $B$  fosse decidível, poderíamos decidir  $A$
- 3 Conclua que  $B$  é indecidível
#### Redução de $A$ para $B$

Uma **redução** de  $A$  para  $B$  é uma função computável  $f$  tal que:

$$w \in A \iff f(w) \in B$$

Notação:  $A \leq_m B$  (“ $A$  se reduz a  $B$ ”)
#### Consequência

Se  $A \leq_m B$  e  $B$  é decidível, então  $A$  é decidível.

Contrapositiva: Se  $A$  é indecidível e  $A \leq_m B$ , então  $B$  é indecidível.

{20}------------------------------------------------
#### Exemplo: $E_{TM}$ é Indecidível
#### Definição

$$E_{TM} = \{\langle M \rangle : L(M) = \emptyset\}$$

“A linguagem de  $M$  é vazia?”
#### Teorema

$E_{TM}$  é indecidível.
### Prova por redução de $A_{TM}$

Construa redução  $f$ : dado  $\langle M, w \rangle$ , produza  $\langle M' \rangle$  onde  $M'$ , na entrada  $x$ :

- 1 Ignora  $x$
- 2 Simula  $M$  em  $w$
- 3 Se  $M$  aceita  $w$ , aceita

Então:  $L(M') = \Sigma^*$  se  $M$  aceita  $w$ , e  $L(M') = \emptyset$  se  $M$  não aceita

{21}------------------------------------------------
### Mais Problemas Indecidíveis
#### $EQ_{TM}$ , Equivalência de MTs

$$EQ_{TM} = \{\langle M_1, M_2 \rangle : L(M_1) = L(M_2)\}$$

Indecidível (redução de  $E_{TM}$ : compare  $M$  com MT que rejeita tudo).
#### $REGULAR_{TM}$

$$REGULAR_{TM} = \{\langle M \rangle : L(M) \text{ é regular}\}$$

Indecidível (Teorema de Rice: ser regular é propriedade não-trivial).
#### $ALL_{TM}$

$$ALL_{TM} = \{\langle M \rangle : L(M) = \Sigma^*\}$$

Indecidível e nem mesmo reconhecível!

{22}------------------------------------------------
### Hierarquia de Problemas

Venn diagram showing the hierarchy of language classes. A large black oval is labeled 'Todas as Linguagens'. Inside it, a blue oval is labeled 'R.E.' and a red oval is labeled 'co-R.E.'. The intersection of the blue and red ovals is labeled 'Decidíveis' in green. Inside the blue oval but outside the red one, the text 'A\_TM' and 'HALT' are shown. Inside the red oval but outside the blue one, the text 'A\_TM' and 'HALT' are shown with a bar over them. Inside the green intersection, the text 'A\_DFA' is shown. Outside the blue and red ovals but inside the black oval, the text 'EQ\_TM' is shown.

- **Decidíveis:**  $A_{DFA}$ ,  $E_{DFA}$ ,  $A_{CFG}$ , primalidade
- **R.E. não decidíveis:**  $A_{TM}$ ,  $HALT$
- **co-R.E. não decidíveis:**  $\overline{A_{TM}}$ ,  $\overline{HALT}$ ,  $ALL_{TM}$
- **Nem R.E. nem co-R.E.:**  $EQ_{TM}$

{23}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-86b4670fc1a5a694821ee92b99c1209a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Venn diagram showing the hierarchy of language classes.
<!-- /IMAGE_DESCRIPTION -->
## Resumo
### Conceitos Principais

- MT Universal: simula qualquer **outra** MT
- Existem problemas indecidíveis (HALT,  $A_{TM}$ )
- Diagonalização: técnica fundamental para provas de impossibilidade (revisão)
- Reduções: técnica para transferir indecidibilidade
- Hierarquia: Decidíveis  $\subset$  R.E.  $\subset$  Todas

| Categoria             | Se $w \in L$ (Pertence) | Se $w \notin L$ (Não Pertence) |
|-----------------------|-------------------------|--------------------------------|
| Decidível             | Para e Aceita           | Para e Rejeita                 |
| Reconhecível (R)      | Para e Aceita           | Pode entrar em Loop            |
| co-Reconhecível (coR) | Pode entrar em Loop     | Para e Rejeita                 |
| Nem R nem co-R (N)    | Pode entrar em Loop     | Pode entrar em Loop            |

{24}------------------------------------------------
### Exercício 1: Decidibilidade

Prove que as seguintes linguagens são decidíveis:

- 1  $\{\langle D \rangle : D \text{ é AFD e } L(D) \text{ é finita}\}$
- 2  $\{\langle D \rangle : D \text{ é AFD e } L(D) \text{ contém alguma cadeia de comprimento par}\}$
- 3  $\{\langle G \rangle : G \text{ é GLC e } \varepsilon \in L(G)\}$
- 4  $\{\langle R \rangle : R \text{ é expressão regular e } L(R) = \Sigma^*\}$

Para cada uma, descreva o algoritmo do decisor.

The image is a faint, gray watermark of the coat of arms of the University of Coimbra. It features a shield with a star in the center, surrounded by smaller stars. The shield is flanked by two figures, likely representing the university's heraldic supporters. Below the shield is a ribbon with the Latin motto "AD VERVM DVICIT" (To the truth, it conquers).

Coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{25}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-2f49752384f0d40dcfa439810d5ad58e_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: MT Universal

- 1 Descreva como a MT Universal  $U$  verifica se  $\langle M \rangle$  é uma codificação válida de MT.
- 2 Se  $M$  tem  $n$  estados e alfabeto de tamanho  $k$ , quantas transições  $M$  pode ter no máximo?
- 3 Se  $U$  usa 3 fitas e cada passo de  $M$  é simulado em tempo proporcional ao tamanho de  $\langle M \rangle$ , qual a complexidade de  $U$  para simular  $t$  passos de  $M$ ?
- 4 Explique por que  $U$  não pode ser um decisor (sempre parar).

{26}------------------------------------------------
### Exercício 3: Indecidibilidade

- 1 Complete a prova de que  $A_{TM}$  é indecidível, mostrando que a MT  $D$  construída na prova de HALT também serve para  $A_{TM}$ .
- 2 Prove que  $\{e : \varphi_e(0) = 0\}$  é indecidível.  
Dica: reduza de  $A_{TM}$ .
- 3 Prove que  $\{e : \varphi_e \text{ é função constante}\}$  é indecidível.  
Dica: use o Teorema de Rice.

The image is a watermark of the University of Coimbra seal. It features a shield with a star in the center, surrounded by four quadrants containing various heraldic symbols. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVOCIT". The entire seal is rendered in a light gray, semi-transparent style.

Watermark of the University of Coimbra seal, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{27}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-1695df64fe320e3f81049cfe402c8155_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 4: Reduções

Prove que as seguintes linguagens são indecidíveis usando reduções:

1  $INFINITE_{TM} = \{\langle M \rangle : L(M) \text{ é infinita}\}$

Dica: reduza de  $A_{TM}$ .

2  $\{\langle M \rangle : M \text{ aceita pelo menos 2 cadeias distintas}\}$

3  $\{\langle M, w \rangle : M \text{ move o cabeçote para a esquerda ao processar } w\}$

4  $\{\langle M \rangle : \text{existe } w \text{ tal que } M \text{ aceita } w \text{ em menos de } |w|^2 \text{ passos}\}$

The image is a watermark of the University of Coimbra's coat of arms. It features a shield with a star at the top and a banner at the bottom with the Latin motto "AD VERVM DVOCIT". The shield is flanked by two figures, and the entire emblem is rendered in a light gray, semi-transparent style.

Watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{28}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-ae83f54db5532eefc57d2e11a76e56d9_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 5: Classificação

Classifique cada linguagem como: (D) Decidível, (R) Reconhecível não-decidível, (coR) co-Reconhecível não-decidível, ou (N) Nem R.E. nem co-R.E.

- 1  $\{\langle M \rangle : M \text{ aceita } \varepsilon\}$
- 2  $\{\langle M \rangle : M \text{ rejeita } \varepsilon\}$
- 3  $\{\langle M \rangle : L(M) = \emptyset\}$
- 4  $\{\langle M \rangle : L(M) \neq \emptyset\}$
- 5  $\{\langle M \rangle : L(M) \text{ é regular}\}$
- 6  $\{\langle M_1, M_2 \rangle : L(M_1) \cap L(M_2) \neq \emptyset\}$

Justifique cada resposta.

The image is a watermark of the University of Coimbra's coat of arms. It features a shield with a cross and a central emblem, flanked by two smaller shields. Above the shield is a crown, and below it is a ribbon with the Latin motto "AD VERVM DVCT". The entire emblem is rendered in a light gray color.

Watermark of the University of Coimbra crest, featuring a shield with a cross and the motto 'AD VERVM DVCT'.

{29}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-aa1ad572ba493829cf259738c9668fe2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra crest, featuring a shield with a cross and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
### Desafio: Teorema de Rice
### Teorema de Rice

Seja  $P$  uma propriedade não-trivial de linguagens r.e.:

- Existe  $M_1$  com  $L(M_1)$  tendo propriedade  $P$
- Existe  $M_2$  com  $L(M_2)$  não tendo propriedade  $P$

Então  $L_P = \{\langle M \rangle : L(M) \text{ tem propriedade } P\}$  é indecidível.

- 1 Prove o Teorema de Rice usando redução de  $A_{TM}$ .  
Dica: Dado  $\langle M, w \rangle$ , construa  $M'$  tal que  $L(M')$  tem  $P$  sse  $M$  aceita  $w$ .
- 2 Use o Teorema de Rice para provar que as seguintes linguagens são indecidíveis:
  - $\{\langle M \rangle : L(M) \text{ contém exatamente 42 cadeias}\}$
  - $\{\langle M \rangle : L(M) \text{ é livre de contexto}\}$
  - $\{\langle M \rangle : L(M) = L(M_0)\}$  para alguma MT fixa  $M_0$

{30}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Faint background watermark of the University of Cambridge crest, featuring a shield with four lions and a closed book, with the motto 'AD VERVM DVCTIT' below.

<!-- IMAGE_DESCRIPTION: datalab-011d7628370283ec23a24c1772507121_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Cambridge crest, featuring a shield with four lions and a closed book, with the motto 'AD VERVM DVCTIT' below.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS (Pontifical University of Rio Grande do Sul)
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->
