<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Motivação**
- **Problemas sobre Linguagens de MTs**
  - Pergunta
- **Teorema de Rice**
  - Propriedades de Linguagens
  - Definição
  - Exemplos de Propriedades
  - Trivialidade
  - Trivial vs. Não-Trivial
- **O Teorema de Rice (1953)**
  - Enunciado
  - “Informalmente”
  - Problemas indecidíveis
  - Atenção!
  - Escopo do Teorema de Rice
  - Exemplos de Propriedades de MTs que são Decidíveis
  - Propriedades de Linguagens Indecidíveis (segundo Rice)
  - Semântica vs. Sintaxe
  - Definição
  - No contexto do Teorema de Rice
  - Exemplos
- **Interpretação do Teorema**
  - Leitura operacional do teorema
  - Restrições fundamentais
  - Alternativas para Análise de Programas
  - Possibilidades
  - Hipótese
  - Preparação
  - Redução ao Problema da Parada
  - Problema de origem
  - Estratégia
  - Intuição
- **Construindo a MT $N_{M,w}$**
  - Contradição
  - Exercício 1: Propriedades Não-Triviais
  - Exercício 2: Aplicações Teóricas do Teorema de Rice
  - Exercício 3: Aplicações Práticas do Teorema de Rice
- **Referências I**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Teorema de Rice

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 13  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

22 de abril de 2026

The logo of the PUCRS Escola Politécnica. It features a small crest on the left with the text "PUCRS" below it. To the right of the crest, the words "ESCOLA" and "POLITÉCNICA" are stacked vertically in a bold, blue, sans-serif font.

Logo of PUCRS Escola Politécnica

{1}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of PUCRS Escola Politécnica
<!-- /IMAGE_DESCRIPTION -->
## Sumário

**1** Teorema de Rice

**2** Aplicações do Teorema de Rice

**3** Prova do Teorema de Rice

**4** Exercícios

A faint, grayscale watermark of the coat of arms of the University of Coimbra is visible on the right side of the slide. The shield features a central star and is flanked by two smaller shields with cross-like symbols. The motto 'AD VERVM DVICIT' is inscribed on a banner at the bottom. The entire emblem is rendered in a light gray color, serving as a background element.

Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-1211e36d120f0d2912a745437f4c8f19_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
## Motivação
## Problemas sobre Linguagens de MTs

Os seguintes problemas são indecidíveis:

- $A_{TM} = \{\langle M, w \rangle \mid M \text{ aceita } w\}$
- $HALT = \{\langle M, w \rangle \mid M \text{ para em } w\}$
- $E_{TM} = \{\langle M \rangle \mid L(M) = \emptyset\}$
### Pergunta

Existe alguma propriedade **não-trivial** de linguagens de MTs que seja decidível? Resposta: **Não!**
## Teorema de Rice

O **Teorema de Rice** generaliza todos estes resultados de indecidibilidade.

{3}------------------------------------------------
### Propriedades de Linguagens
### Definição

Uma **propriedade de linguagens**  $P$  é um conjunto de linguagens Turing-reconhecíveis.

- Dizemos que uma MT  $M$  **satisfaz**  $P$  se  $L(M) \in P$ .
### Exemplos de Propriedades

- $P_1 = \{L \mid L \text{ é finita}\}$  — linguagens finitas
- $P_2 = \{L \mid L \text{ é regular}\}$  — linguagens regulares
- $P_3 = \{L \mid L = \Sigma^*\}$  — linguagem de todas as strings
- $P_4 = \{L \mid \epsilon \in L\}$  — linguagens que contêm  $\epsilon$
- $P_5 = \{L \mid L \neq \emptyset\}$  — linguagens não-vazias

{4}------------------------------------------------
### Trivialidade
#### Propriedade Trivial

Uma propriedade  $P$  é **trivial** se:

- $P = \emptyset$  (nenhuma linguagem satisfaz), ou
- $P$  contém todas as linguagens Turing-reconhecíveis
#### Propriedade Não-Trivial

$P$  é **não-trivial** se existe:

- Pelo menos uma linguagem  $L_1 \in P$ , e
- Pelo menos uma linguagem  $L_2 \notin P$
### Trivial vs. Não-Trivial

Propriedades triviais são “fáceis” de decidir (s/n)

{5}------------------------------------------------
## O Teorema de Rice (1953)
### Enunciado

Seja  $P$  uma propriedade **não-trivial** de linguagens Turing-reconhecíveis. Então o problema:

$$L_P = \{\langle M \rangle \mid L(M) \in P\}$$

é **indecidível**.
### “Informalmente”

Qualquer “pergunta” não-trivial sobre a **linguagem** reconhecida por uma MT é indecidível.
### Problemas indecidíveis

São indecidíveis: “ $L(M)$  é finita?”, “ $L(M)$  é regular?”, “ $L(M) = \Sigma^*$ ?”, “ $L(M)$  contém a string  $w$ ?”, “ $L(M)$  é vazia?”, etc.

{6}------------------------------------------------
### Atenção!
### Escopo do Teorema de Rice

O Teorema de Rice se aplica a propriedades da **linguagem**  $L(M)$ , não a propriedades da **máquina**  $M$  em si.
### Exemplos de Propriedades de MTs que são Decidíveis

- “ $M$  tem exatamente 5 estados?”
- “ $M$  tem uma transição de  $q_0$  para  $q_1$ ?”
- “O alfabeto de  $M$  contém o símbolo  $a$ ?”
### Propriedades de Linguagens Indecidíveis (segundo Rice)

- “ $L(M)$  é infinita?”
- “ $L(M)$  contém alguma string de tamanho 5?”
- “ $L(M) = L(M')$ ?”

{7}------------------------------------------------
### Semântica vs. Sintaxe
### Definição

- A **sintaxe** descreve a forma da máquina, e.g. número de estados, transições, símbolos, ...
- A **semântica** descreve o significado computacional: que linguagem é reconhecida, ...
### No contexto do Teorema de Rice

Rice trata de perguntas **semânticas**, porque dependem apenas de  $L(M)$ . Perguntas meramente **sintáticas** sobre a descrição de  $M$  ficam fora do alcance do teorema e podem ser decidíveis.
### Exemplos

- **Sintática:** “ $M$  usa o símbolo  $a$ ?”
- **Semântica:** “ $L(M)$  contém alguma palavra com  $a$ ?”

{8}------------------------------------------------
## Interpretação do Teorema
### Leitura operacional do teorema

O Teorema de Rice diz que não existe algoritmo geral para decidir propriedades **semânticas e não-triviais** de programas.
#### Intuitivamente

Sempre que a pergunta for sobre **o que o programa faz**, e não apenas sobre **como ele foi escrito**, devemos suspeitar de indecidibilidade.
#### Regra prática

Se a resposta exige executar ou raciocinar sobre o **comportamento** do programa em entradas arbitrárias, Rice costuma se aplicar.

{9}------------------------------------------------
#### Exemplo: Ferramentas de Software
### Restrições fundamentais

Não pode existir uma ferramenta que, para **qualquer** programa arbitrário, responda perfeitamente perguntas como:

- “há bugs?”
- “há vulnerabilidades?”
- “há vazamento de informação?”
- “o código morto nunca será executado?”
#### Exemplos:

- **Compiladores** não conseguem detectar todo código morto.
- **Analizadores estáticos** não conseguem classificar com precisão total todos os defeitos.
- **Antivírus** não conseguem reconhecer todo comportamento malicioso possível.

{10}------------------------------------------------
### Alternativas para Análise de Programas
### Possibilidades

Como uma decisão perfeita é impossível no caso geral, usamos:

- **restrições de modelo:** linguagens ou fragmentos mais simples (redução de escopo);
- **análise aproximada:** aceita falsos positivos/negativos;
- **heurísticas:** úteis na prática, sem garantia total;
- **provas e assistência humana:** quando é preciso alta confiança.
- **IA:** se encaixa como “heurística”, pois não provê garantias.
#### Resultado

O Teorema de Rice não torna análise de programas inútil; ele mostra que ferramentas reais precisam ser **incompletas**, **aproximadas** ou trabalhar sobre **casos restritos**.

{11}------------------------------------------------
#### Prova por Contradição
### Hipótese

Suponha que exista um **decisor**  $D_P$  para  $L_P = \{\langle M \rangle \mid L(M) \in P\}$ . Isto é, dado o código de uma MT  $M$ , o decisor  $D_P$  sempre para e responde corretamente se  $L(M)$  tem a propriedade  $P$ .
### Preparação

Como  $P$  é não-trivial, existe pelo menos uma linguagem reconhecível  $L_1 \in P$ . Seja  $M_1$  uma MT tal que  $L(M_1) = L_1$ .
#### Sem perda de generalidade

Podemos assumir que  $\emptyset \notin P$ . Se  $\emptyset \in P$ , aplicamos o argumento à propriedade complementar  $\overline{P}$  (sobre a classe das linguagens Turing-reconhecíveis); se  $L_P$  fosse decidível, então  $L_{\overline{P}}$  também seria.

{12}------------------------------------------------
### Redução ao Problema da Parada
### Problema de origem

Vamos mostrar que, se  $D_P$  existisse, poderíamos decidir

$$HALT = \{\langle M, w \rangle \mid M \text{ para em } w\},$$

o que é impossível.
### Estratégia

Dada uma instância  $\langle M, w \rangle$  de  $HALT$ , construiremos uma nova MT  $N_{M,w}$  de forma que:

$$\langle M, w \rangle \in HALT \iff L(N_{M,w}) \in P.$$
### Intuição

{13}------------------------------------------------
## Construindo a MT $N_{M,w}$
#### Definição de $N_{M,w}$

Na entrada arbitrária  $x$ , a máquina  $N_{M,w}$  faz o seguinte:

- 1 ignora  $x$  momentaneamente;
- 2 simula  $M$  sobre a entrada fixa  $w$ ;
- 3 se a simulação de  $M(w)$  **parar**, então  $N_{M,w}$  passa a simular  $M_1$  sobre a entrada  $x$ ;
- 4 se  $M(w)$  **nunca parar**, então  $N_{M,w}$  nunca chega ao passo 3.
#### Ponto central

O comportamento semântico de  $N_{M,w}$  depende inteiramente de um fato externo:  **$M$  para ou não para em  $w$ ?**

{14}------------------------------------------------
#### Possíveis retornos de $N_{M,w}$
#### Caso 1: $M$ para em $w$

- A etapa de simulação termina.
- Depois disso,  $N_{M,w}$  passa a agir exatamente como  $M_1$  sobre a entrada  $x$ .
- Logo,  $L(N_{M,w}) = L(M_1) = L_1$ .
- Portanto,  $L(N_{M,w}) \in P$ .
#### Caso 2: $M$ não para em $w$

- A simulação nunca termina.
- O passo 3 jamais é alcançado.
- Assim,  $N_{M,w}$  não aceita nenhuma entrada.
- Logo,  $L(N_{M,w}) = \emptyset \notin P$ .

{15}------------------------------------------------
### Contradição

Pela construção...

$$\langle M, w \rangle \in HALT \iff L(N_{M,w}) \in P$$

Usando o decisor hipotético

Se  $D_P$  existisse, bastaria construir  $\langle N_{M,w} \rangle$  e executar  $D_P(\langle N_{M,w} \rangle)$ :

- se  $D_P$  respondesse **sim**, concluiríamos que  $M$  para em  $w$ ;
- se  $D_P$  respondesse **não**, concluiríamos que  $M$  não para em  $w$ .

Conclusão

Isso decidiria o problema  $HALT$ , o que é impossível. Portanto, o decisor  $D_P$  não pode existir. Logo,  $L_P$  é **indecidível**.

{16}------------------------------------------------
### Exercício 1: Propriedades Não-Triviais

Use o Teorema de Rice para provar que os seguintes problemas são indecidíveis:

- 1  $\{\langle M \rangle \mid L(M) \text{ contém exatamente 10 strings}\}$
- 2  $\{\langle M \rangle \mid L(M) \text{ é uma linguagem regular}\}$
- 3  $\{\langle M \rangle \mid L(M) = \{0^n 1^n \mid n \geq 0\}\}$
- 4  $\{\langle M \rangle \mid |L(M)| \geq 100\}$

Para cada item, identifique qual é a propriedade  $P$  e mostre que é não-trivial.

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a cross and a central emblem, flanked by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT".

Watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.

{17}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-bcc4b9d57d1d23e256f09d0a0a81be73_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Aplicações Teóricas do Teorema de Rice

Explique por que o Teorema de Rice **não** pode ser usado diretamente para os seguintes problemas:

- 1  $\{\langle M \rangle \mid M \text{ tem mais de 5 estados}\}$
- 2  $\{\langle M \rangle \mid M \text{ aceita } \langle M \rangle\}$
- 3  $\{\langle M, w \rangle \mid M \text{ para em } w \text{ em menos de 1000 passos}\}$
- 4  $\{\langle M \rangle \mid M \text{ nunca move a cabeça para a esquerda}\}$

Para cada item, determine se o problema é decidível ou não, e justifique.

The image is a watermark of the University of Coimbra seal. It features a shield with a crown on top, supported by two figures. The shield is divided into sections containing various heraldic symbols, including a star and a cross. Below the shield is a ribbon with the Latin motto 'AD VERVM DVOCIT' (To the truth it calls).

Watermark of the University of Coimbra seal, featuring a shield with a crown and the motto 'AD VERVM DVOCIT'.

{18}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-601cbf7e7b6a7dd9a260c57031279e13_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra seal, featuring a shield with a crown and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Aplicações Práticas do Teorema de Rice

- 1 Um colega propõe criar um “verificador universal de bugs” que analisa qualquer programa e garante que está livre de erros. Use o Teorema de Rice para explicar por que isso é impossível.
- 2 Considere um compilador que tenta otimizar programas eliminando código morto (código que nunca executa). Por que este problema é, em geral, indecidível? Como compiladores reais lidam com isso?
- 3 Um antivírus afirma detectar “todos os vírus”. Isso é possível? Justifique usando os conceitos desta aula.

{19}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.
