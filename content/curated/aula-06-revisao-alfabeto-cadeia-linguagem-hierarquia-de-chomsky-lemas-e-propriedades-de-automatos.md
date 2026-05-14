<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Motivação**
- **Teoria de Autômatos e Linguagens Formais**
  - Contexto
- **Alfabeto**
  - Definição
  - Exemplos
- **Cadeia (String)**
  - Definição
  - Notações
  - Exemplos com $\Sigma = \{0, 1\}$
  - Operações com Cadeias
  - Subcadeia (substring)
  - O Conjunto $\Sigma^*$
  - Definição de Linguagem
  - Operações com Linguagens
  - Operações de Conjunto
  - Operações Específicas de Linguagens
  - Quantidade de Linguagens
  - Classes de Linguagens
  - Hierarquia
  - Problemas de Decisão como Linguagens
  - Idea Fundamental
  - Decidibilidade
  - Autômato Finito Determinístico (DFA)
  - Autômato Finito Não-Determinístico (NDFA)
- **Linguagens Regulares**
  - Definição
  - Caracterizações Equivalentes
  - Fechamento
- **Lema do Bombeamento para Linguagens Regulares**
  - Lema (Pumping Lemma)
  - Autômatos de Pilha (PDA)
  - Conclusão
- **Gramáticas Formais**
  - Definição
  - Derivação
  - Linguagem Gerada
- **A Hierarquia de Chomsky**
  - Classificação por Restrições nas Regras
  - Inclusões
  - Correspondência com Autômatos
  - Exemplos de Linguagens em Cada Nível
- **Lema do Bombeamento para LLCs**
  - Enunciado
  - Intuição
  - Comparando os Dois Lemmas do Bombeamento
  - Conclusão
- **Linguagens Decidíveis vs. Reconhecíveis**
  - Definições
  - Relação
  - Teorema
  - Exemplo
- **Resumo: Poderes Computacionais**
  - Exercício 1: Operações com Cadeias
  - Exercício 2: Operações com Linguagens
  - Exercício 3: Cardinalidade e Representação
  - Exercício 4: Autômatos Finitos
  - Exercício 5: Lema do Bombeamento Regular
  - Exercício 6: Gramáticas e Hierarquia
  - Exercício 7: Classificação de Linguagens
  - Exercício 8: PDAs
  - Exercício 9: Bombeamento para LLCs
  - Exercício 10: Reconhecível vs. Decidível
  - Exercício 11: Propriedades de Fechamento
- **Referências I**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Revisão: Alfabeto, Cadeia, Linguagem, Hierarquia de Chomsky, Lemmas e Propriedades de Autômatos

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 06  
Teoria da Computabilidade e Complexidade  
Ciência da Computação

22 de março de 2026

A faint, large-scale watermark of the PUCRS seal is visible in the background on the right side of the slide. The seal features a shield with a star and the motto 'AD VERVM DVOCIT'.

Faint background watermark of the PUCRS seal, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{1}------------------------------------------------
## Sumário

- 1** Alfabetos e Cadeias
- 2** Linguagens
- 3** Autômatos Finitos
- 4** Hierarquia de Chomsky
- 5** Exercícios

A faint, stylized watermark of the coat of arms of the University of Coimbra. It features a shield with a central crest and two side sections containing pine-like trees. Above the shield is a crown and two crossed keys. A ribbon at the bottom bears the Latin motto 'AD VERVM DVICIT'.

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-b6cb8677b4ffb35c6468fa5c24091bff_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized watermark of the coat of arms of the University of Coimbra.
<!-- /IMAGE_DESCRIPTION -->
## Motivação
## Teoria de Autômatos e Linguagens Formais

Para estudar Máquinas de Turing e computabilidade, precisamos de uma base sólida em:

- Teoria de linguagens formais
- Autômatos finitos e suas limitações
- Hierarquia de Chomsky
### Contexto

Máquinas de Turing operam sobre **cadeias** de símbolos e são uma “continuação” do conteúdo estudado na disciplina de Linguagens Formais e Autômatos. Em alguns contextos, essa disciplina é chamada de “Introdução à Teoria da Computação” ou “Teoria da Computação I”.

{3}------------------------------------------------
## Alfabeto
### Definição

Um **alfabeto**  $\Sigma$  é um conjunto finito não-vazio de símbolos.
### Exemplos

- $\Sigma_0 = \{0, 1\}$ , alfabeto binário
- $\Sigma_1 = \{a, b, c, \dots, z\}$ , alfabeto das letras minúsculas
- $\Sigma_2 = \{0, 1, 2, \dots, 9\}$ , alfabeto dos dígitos decimais
- $\Sigma_3 = \{a, b, \dots, z, 0, \dots, 9, \_\}$ , alfabeto dos identificadores
- $\Sigma_4 = \{+, -, \times, \div, =\}$ , alfabeto dos símbolos matemáticos

{4}------------------------------------------------
## Cadeia (String)
### Definição

Uma **cadeia** (ou string, palavra) sobre  $\Sigma$  é uma sequência finita de símbolos de  $\Sigma$ .
### Notações

- $w = a_1 a_2 \cdots a_n$  onde cada  $a_i \in \Sigma$
- $|w| = n$  é o **comprimento** de  $w$
- $\varepsilon$  é a **cadeia vazia** ( $|\varepsilon| = 0$ )
- $w[i]$  ou  $w_i$  denota o  $i$ -ésimo símbolo de  $w$
### Exemplos com $\Sigma = \{0, 1\}$

- $w = 0110$  tem comprimento  $|w| = 4$
- $w = 0$ ;  $|w| = 1$
- $|\varepsilon| = 0$

{5}------------------------------------------------
### Operações com Cadeias
#### Concatenação

Se  $w = a_1 \cdots a_n$  e  $v = b_1 \cdots b_m$ , então:

$$w \cdot v = wv = a_1 \cdots a_n b_1 \cdots b_m$$

Propriedades:

- $|wv| = |w| + |v|$
- $w\varepsilon = \varepsilon w = w$  (elemento neutro)
- $(uv)w = u(vw)$  (associatividade)
#### Potência

- $w^0 = \varepsilon$
- $w^{n+1} = w^n \cdot w$

Exemplo:  $(ab)^3 = ababab$

{6}------------------------------------------------
#### Mais Operações com Cadeias
#### Cadeia Reversa

Se  $w = a_1 a_2 \cdots a_n$ , então  $w^R = a_n \cdots a_2 a_1$ .

Exemplo:  $(abcd)^R = dcba$
### Subcadeia (substring)

$v$  é **subcadeia** de  $w$  se  $w = xvy$  para algumas cadeias  $x, y$ .
#### Prefixo e Sufixo

- $v$  é **prefixo** de  $w$  se  $w = vy$  para algum  $y$
- $v$  é **sufixo** de  $w$  se  $w = xv$  para algum  $x$

Exemplo:  $w = abcde$

- Prefixos:  $\varepsilon, a, ab, abc, abcd, abcde$
- Sufixos:  $\varepsilon, e, de, cde, bcde, abcde$
- Subcadeias:  $\varepsilon, a, b, \dots, bc, bcd, \dots, abcde$

{7}------------------------------------------------
### O Conjunto $\Sigma^*$
#### Definição

$\Sigma^*$  é o conjunto de **todas** as cadeias finitas sobre  $\Sigma$ , incluindo  $\varepsilon$ .

$$\Sigma^* = \bigcup_{n=0}^{\infty} \Sigma^n$$

onde  $\Sigma^n = \{w : |w| = n\}$ .
#### Definição Alternativa

$\Sigma^+ = \Sigma^* - \{\varepsilon\}$ , cadeias não-vazias

Exemplo:  $\Sigma = \{a, b\}$

$$\Sigma^0 = \{\varepsilon\}$$

$$\Sigma^2 = \{aa, ab, ba, bb\}$$

$$\Sigma^1 = \{a, b\}$$

$$\Sigma^* = \{\varepsilon, a, b, aa, ab, ba, bb, aaa, \dots\}$$

{8}------------------------------------------------
#### Propriedades de $\Sigma^*$
#### Cardinalidade

- $|\Sigma^n| = |\Sigma|^n$
- $\Sigma^*$  é **infinito contável** (enumerável)
#### Ordem Canônica

Podemos ordenar  $\Sigma^*$  de forma única:

- 1 Primeiro por comprimento
- 2 Depois lexicograficamente

Para  $\Sigma = \{0, 1\}$  com  $0 < 1$ :

$$\varepsilon, 0, 1, 00, 01, 10, 11, 000, 001, \dots$$
#### Importância

A ordem canônica permite **enumerar** todas as cadeias, o que é essencial para argumentos de diagonalização.

{9}------------------------------------------------
### Definição de Linguagem
#### Definição

Uma **linguagem**  $L$  sobre um alfabeto  $\Sigma$  é um subconjunto de  $\Sigma^*$ :

$$L \subseteq \Sigma^*$$
#### Exemplos

- $L_1 = \{0^n 1^n : n \geq 0\} = \{\varepsilon, 01, 0011, 000111, \dots\}$
- $L_2 = \{w \in \{0, 1\}^* : w = w^R\}$ , palíndromos binários
- $L_3 = \{w \in \{a, b\}^* : |w|_a = |w|_b\}$ , mesmo número de as e bs
- $L_4 = \emptyset$ , linguagem vazia
- $L_5 = \{\varepsilon\}$ , linguagem contendo apenas a cadeia vazia
#### Observação

$\emptyset \neq \{\varepsilon\}$ : o primeiro não possui elementos, o segundo possui um!

{10}------------------------------------------------
### Operações com Linguagens
### Operações de Conjunto

- **União:**  $L_1 \cup L_2 = \{w : w \in L_1 \vee w \in L_2\}$
- **Interseção:**  $L_1 \cap L_2 = \{w : w \in L_1 \wedge w \in L_2\}$
- **Complemento:**  $\bar{L} = \Sigma^* - L$
- **Diferença:**  $L_1 - L_2 = L_1 \cap \bar{L}_2$
### Operações Específicas de Linguagens

- **Concatenação:**  $L_1 \cdot L_2 = \{xy : x \in L_1 \wedge y \in L_2\}$
- **Potência:**  $L^0 = \{\varepsilon\}, L^{n+1} = L^n \cdot L$
- **Fecho de Kleene:**  $L^* = \bigcup_{n=0}^{\infty} L^n$
- **Fecho Positivo:**  $L^+ = \bigcup_{n=1}^{\infty} L^n = L \cdot L^*$

{11}------------------------------------------------
#### Exemplos de Operações

Sejam  $L_1 = \{a, ab\}$  e  $L_2 = \{b, ba\}$ .
#### União

$$L_1 \cup L_2 = \{a, ab, b, ba\}$$
#### Concatenação

$$L_1 \cdot L_2 = \{ab, aba, abb, abba\}$$
#### Potências de $L_1$

$$L_1^0 = \{\varepsilon\}$$

$$L_1^1 = \{a, ab\}$$

$$L_1^2 = \{aa, aab, aba, abab\}$$
#### Fecho de Kleene

$$L_1^* = \{\varepsilon, a, ab, aa, aab, aba, abab, aaa, \dots\}$$

{12}------------------------------------------------
### Quantidade de Linguagens
#### Teorema

O conjunto de todas as linguagens sobre  $\Sigma$  é **incontável**.
#### Prova

- Cada linguagem  $L \subseteq \Sigma^*$  é um subconjunto de  $\Sigma^*$
- O conjunto de todos os subconjuntos é  $\mathcal{P}(\Sigma^*)$
- $|\mathcal{P}(\Sigma^*)| = 2^{|\Sigma^*|} = 2^{\aleph_0}$  (incontável)
#### Consequência

- Existem apenas  $\aleph_0$  programas/máquinas (strings finitas)
- Existem  $2^{\aleph_0}$  linguagens
- Logo, existem linguagens que **nenhum programa pode reconhecer!**

{13}------------------------------------------------
### Classes de Linguagens
### Hierarquia

Linguagens são classificadas pela “complexidade” de reconhecê-las:

Diagrama de hierarquia de linguagens representado por cinco círculos concêntricos. Os círculos são aninhados, com o menor no centro e o maior na base. Os rótulos, de cima para baixo (do maior para o menor conjunto), são: Todas as Linguagens, Recursivamente Enumeráveis, Recursivas (Decidíveis), Livres de Contexto e Regulares.

Diagrama de hierarquia de linguagens

{14}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-c036e2540a94b31357ceb0002f0cacab_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de hierarquia de linguagens
<!-- /IMAGE_DESCRIPTION -->
### Problemas de Decisão como Linguagens
### Idea Fundamental

Todo problema de decisão pode ser formulado como uma linguagem:

$$L_P = \{w : w \text{ codifica uma instância com resposta SIM}\}$$
#### Exemplos

- **PRIMO**:  $\{w : w \text{ codifica um número primo}\}$
- **SAT**:  $\{w : w \text{ codifica uma fórmula satisfatível}\}$
- **HALT**:  $\{(M, x) : M \text{ para na entrada } x\}$
### Decidibilidade

- $L$  é **decidível** se existe algoritmo que sempre termina (sim/não)
- $L$  é **reconhecível** se existe algoritmo que eventualmente termina (somente sim)

{15}------------------------------------------------
### Autômato Finito Determinístico (DFA)
#### Definição

Um DFA é uma 5-tupla  $M = (Q, \Sigma, \delta, q_0, F)$  onde:

- $Q$  é conjunto finito de estados
- $\Sigma$  é alfabeto de entrada
- $\delta : Q \times \Sigma \rightarrow Q$  é função de transição
- $q_0 \in Q$  é estado inicial
- $F \subseteq Q$  é conjunto de estados finais (de aceitação)
#### Funcionamento

- 1 Cursor inicia no estado  $q_0$
- 2 Um símbolo é lido da entrada e consumido
- 3 O cursor se move de acordo com  $\delta$
- 4 A cadeia é aceita se o cursor terminar em estado  $q \in F$

{16}------------------------------------------------
#### Exemplo de DFA

Linguagem: cadeias que terminam em 01

$$L = \{w \in \{0, 1\}^* : w \text{ termina em } 01\}$$

```
graph LR; q0((q0)) -- 1 --> q0; q0 -- 0 --> q1((q1)); q1 -- 0 --> q1; q1 -- 1 --> q2(((q2))); q2 -- 1 --> q0; q2 -- 0 --> q1;
```

Diagrama de um DFA com três estados: q0, q1 e q2. q0 é o estado inicial, q2 é o estado final. Transições: q0 para q0 com 1, q0 para q1 com 0, q1 para q1 com 0, q1 para q2 com 1, q2 para q0 com 1, q2 para q1 com 0.

- $Q = \{q_0, q_1, q_2\}$ ,  $\Sigma = \{0, 1\}$
- $q_0$ : estado inicial,  $F = \{q_2\}$
- $q_1$ : último símbolo foi 0,  $q_2$ : últimos símbolos foram 01

{17}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-29f586959675cafdf81cf934954908eb_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de um DFA com três estados: q0, q1 e q2.
<!-- /IMAGE_DESCRIPTION -->
### Autômato Finito Não-Determinístico (NDFA)
#### Definição

Um NDFA é uma 5-tupla  $M = (Q, \Sigma, \delta, q_0, F)$  onde:

- $\delta : Q \times (\Sigma \cup \{\varepsilon\}) \rightarrow \mathcal{P}(Q)$

Diferenças do DFA:

- $\delta$  retorna um **conjunto** de estados
- Permite transições- $\varepsilon$  (sem consumir símbolo)
- Aceita se **algum** caminho leva a um estado final
#### Teorema

DFAs e NDFAs possuem o **mesmo poder expressivo**:

$L$  é reconhecida por NDFA  $\iff L$  é reconhecida por DFA

{18}------------------------------------------------
## Linguagens Regulares
### Definição

Uma linguagem é **regular** se é reconhecida por algum DFA (equivalentemente, por algum NDFA).
### Caracterizações Equivalentes

$L$  é regular  $\iff$  qualquer uma das seguintes:

- $L$  é reconhecida por um DFA
- $L$  é reconhecida por um NDFA
- $L$  é descrita por uma expressão regular
- $L$  é gerada por uma gramática regular
### Fechamento

Linguagens regulares são fechadas sob:

- União, interseção, complemento, diferença
- Concatenação, fecho de Kleene, reverso

{19}------------------------------------------------
## Lema do Bombeamento para Linguagens Regulares
### Lema (Pumping Lemma)

Se  $L$  é regular, então existe  $p \geq 1$  (comprimento de bombeamento) tal que toda cadeia  $w \in L$  com  $|w| \geq p$  pode ser dividida como  $w = xyz$  onde:

- 1  $|xy| \leq p$
- 2  $|y| > 0$
- 3  $xy^i z \in L$  para todo  $i \geq 0$
#### Exemplo de Uso (estrutura de prova)

O lema é usado para provar que linguagens **não** são regulares:

- Suponha que  $L$  é regular
- Seja  $p$  o comprimento de bombeamento
- Encontre  $w \in L$  com  $|w| \geq p$  que não pode ser bombeado
- Contradição! Logo  $L$  não é regular

{20}------------------------------------------------
#### Exemplo: $\{0^n 1^n\}$ não é Regular
#### Afirmação

$L = \{0^n 1^n : n \geq 0\}$  não é regular.
#### Prova

Suponha que  $L$  é regular com comprimento de bombeamento  $p$ .

Considere  $w = 0^p 1^p \in L$  (note que  $|w| = 2p \geq p$ ).

Pela condição 1,  $xy$  consiste apenas de 0s (pois  $|xy| \leq p$ ).

Pela condição 2,  $y = 0^k$  para algum  $k > 0$ .

Pela condição 3,  $xy^2z = 0^{p+k} 1^p$  deveria estar em  $L$ .

Mas  $0^{p+k} 1^p \notin L$  pois  $p + k \neq p$ .

Contradição! Logo  $L$  não é regular.

{21}------------------------------------------------
### Autômatos de Pilha (PDA)
#### Definição

Um PDA é uma 7-tupla  $M = (Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)$ :

- $\Gamma$  é alfabeto da pilha
- $\delta : Q \times (\Sigma \cup \{\varepsilon\}) \times \Gamma \rightarrow \mathcal{P}(Q \times \Gamma^*)$  é a função de transição
- $Z_0 \in \Gamma$ , símbolo inicial da pilha
- Outros elementos equivalem aos encontrados em DFA e NDFA
#### Expressividade

PDAs reconhecem as **linguagens livres de contexto**. Exemplo:  
 $L = \{0^n 1^n : n \geq 0\}$  (não é regular, mas é livre de contexto).
#### Limitação

PDAs não reconhecem **linguagens sensíveis ao contexto** ou **recursivamente enumeráveis**, e.g.  $\{a^n b^n c^n : n \geq 0\}$ . Para isso, precisamos de Máquinas de Turing!

{22}------------------------------------------------
#### Exemplo de PDA: $\{0^n 1^n : n \geq 0\}$

```
graph LR; q0((q0)) -- "0, Z0/XZ0" --> q0; q0 -- "0, X/XX" --> q0; q0 -- "1, X/$\epsilon$" --> q1((q1)); q1 -- "1, X/$\epsilon$" --> q1; q1 -- "$\epsilon$, Z0/Z0" --> qf(((qf))); style q0 fill:#fff,stroke:#000,stroke-width:2px; style q1 fill:#fff,stroke:#000,stroke-width:2px; style qf fill:#fff,stroke:#000,stroke-width:3px; style q0_text fill:#000,stroke:none; style q1_text fill:#000,stroke:none; style qf_text fill:#000,stroke:none;
```

Diagram of a Pushdown Automaton (PDA) for the language {0^n 1^n : n $\geq$ 0}. The automaton has three states: q0, q1, and qf. q0 is the start state, q1 is the middle state, and qf is the final state (double circle). Transitions: q0 has a self-loop labeled '0, Z0/XZ0' and '0, X/XX'; q0 to q1 is labeled '1, X/$\epsilon$'; q1 has a self-loop labeled '1, X/$\epsilon$'; q1 to qf is labeled '$\epsilon$, Z0/Z0'.

<!-- IMAGE_DESCRIPTION: datalab-86b4670fc1a5a694821ee92b99c1209a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Pushdown Automaton (PDA) for the language {0^n 1^n : n ≥ 0}.
<!-- /IMAGE_DESCRIPTION -->
#### Descrição das transições

- **Em  $q_0$ :** empilha  $X$  para cada símbolo de entrada  $0$
- **Transição  $q_0 \rightarrow q_1$ :** ao ler o primeiro  $1$ , muda para fase de comparação
- **Em  $q_1$ :** desempilha um  $X$  para cada símbolo de entrada  $1$
- **Transição  $q_1 \rightarrow q_f$ :** aceita quando a pilha está vazia (apenas  $Z_0$  no topo)

{23}------------------------------------------------
#### Exemplo de PDA: $\{0^n 1^n : n \geq 0\}$ (contd.)
#### Estratégia

- 1 Enquanto lê 0s, empilha um símbolo  $X$  para cada 0
- 2 Ao começar a ler 1s, desempilha um  $X$  para cada 1
- 3 Aceita quando a entrada termina junto com a pilha
#### Transições principais

- $(q_0, 0, Z_0) \rightarrow (q_0, XZ_0)$  e  $(q_0, 0, X) \rightarrow (q_0, XX)$
- $(q_0, 1, X) \rightarrow (q_1, \varepsilon)$
- $(q_1, 1, X) \rightarrow (q_1, \varepsilon)$
- $(q_1, \varepsilon, Z_0) \rightarrow (q_f, Z_0)$
#### Noção intuitiva

A pilha guarda quantos 0s foram vistos; a fase de leitura dos 1s confere se a quantidade coincide.

{24}------------------------------------------------
#### Outro Exemplo de PDA: $L = \{wcw^R : w \in \{a,b\}^*\}$
#### Ideia

A letra  $c$  marca o meio da cadeia:

- antes de  $c$ , o PDA empilha os símbolos de  $w$
- depois de  $c$ , o PDA compara a entrada com o topo da pilha
#### Exemplo de execução

Para a cadeia  $abcba$  com marcador central, isto é,  $abcba = ab c ba$ :

- 1 lê  $a, b$  e empilha  $a, b$
- 2 lê  $c$  e muda para a fase de comparação
- 3 lê  $b, a$  e desempilha  $b, a$
### Conclusão

Um PDA consegue comparar partes da entrada quando a estrutura é **aninhada** ou **espelhada**. Já dependências entre **três contagens independentes** exigem mais expressividade.

{25}------------------------------------------------
## Gramáticas Formais
### Definição

Uma gramática é uma 4-tupla  $G = (V, \Sigma, R, S)$  onde:

- $V$  — conjunto finito de variáveis (não-terminais)
- $\Sigma$  — alfabeto de terminais (disjunto de  $V$ )
- $R \subseteq (V \cup \Sigma)^* V (V \cup \Sigma)^* \times (V \cup \Sigma)^*$  — regras de produção
- $S \in V$  — símbolo inicial
### Derivação

$\alpha \Rightarrow \beta$  se  $\alpha = \gamma A \delta$ ,  $\beta = \gamma \omega \delta$  e  $(A \rightarrow \omega) \in R$ .

$\alpha \Rightarrow^* \beta$  se existe sequência  $\alpha = \alpha_0 \Rightarrow \alpha_1 \Rightarrow \dots \Rightarrow \alpha_n = \beta$ .
### Linguagem Gerada

$$L(G) = \{w \in \Sigma^* : S \Rightarrow^* w\}$$

{26}------------------------------------------------
## A Hierarquia de Chomsky
### Classificação por Restrições nas Regras

Tipo 0 Gramáticas irrestritas:  $\alpha \rightarrow \beta$  (qualquer)

Tipo 1 Sensíveis ao contexto:  $\alpha A \beta \rightarrow \alpha \gamma \beta$  com  $|\gamma| \geq 1$

Tipo 2 Livres de contexto:  $A \rightarrow \gamma$

Tipo 3 Regulares:  $A \rightarrow aB$  ou  $A \rightarrow a$  ou  $A \rightarrow \varepsilon$
### Inclusões

Regulares  $\subset$  LLCs  $\subset$  LSCs  $\subset$  R.E.

Todas as inclusões são **estritas**.

{27}------------------------------------------------
### Correspondência com Autômatos

| Tipo | Linguagens                 | Reconhecedor                  |
|------|----------------------------|-------------------------------|
| 3    | Regulares                  | Autômato Finito               |
| 2    | Livres de Contexto         | Autômato com Pilha            |
| 1    | Sensíveis ao Contexto      | Autômato Linearmente Limitado |
| 0    | Recursivamente Enumeráveis | Máquina de Turing             |
#### Observação

- Cada nível adiciona “memória”
- AFD: memória finita (estados)
- AP: memória de pilha (LIFO)
- ALL: memória linear no tamanho da entrada
- MT: memória ilimitada (fita infinita)

{28}------------------------------------------------
### Exemplos de Linguagens em Cada Nível
#### Tipo 3: Regulares

- $\{w : w \text{ contém } 01 \text{ como subcadeia}\}$
- $\{w : |w| \text{ é par}\}$
- Qualquer linguagem finita
#### Tipo 2: Livres de Contexto

- $\{0^n 1^n : n \geq 0\}$
- $\{ww^R : w \in \{a, b\}^*\}$ , palíndromos pares
- Expressões aritméticas bem formadas
#### Tipo 1: Sensíveis ao Contexto

- $\{a^n b^n c^n : n \geq 0\}$
- $\{ww : w \in \{a, b\}^*\}$ , cópias

{29}------------------------------------------------
#### Tipo 0: Linguagens Recursivamente Enumeráveis
#### Características

- Reconhecidas por Máquinas de Turing
- Nenhuma restrição nas regras de produção
- Podem não parar para cadeias rejeitadas
#### Exemplos

- Problema da Parada (HALT)
- Qualquer linguagem decidível
- Linguagens com comportamento não-determinístico arbitrário
#### Observação importante

Nem toda linguagem recursivamente enumerável é decidível. Existem linguagens que podem ser reconhecidas (MT para sim) mas não há MT que sempre para.

{30}------------------------------------------------
## Lema do Bombeamento para LLCs
### Enunciado

Se  $L$  é uma linguagem livre de contexto, então existe  $p \geq 1$  tal que toda cadeia  $w \in L$  com  $|w| \geq p$  pode ser escrita como

$$w = uvxyz$$

de modo que:

- 1  $|vxy| \leq p$
- 2  $|vy| > 0$
- 3  $uv^i xy^i z \in L$  para todo  $i \geq 0$
### Intuição

Em árvores de derivação suficientemente grandes, algum não-terminal se repete em um caminho. Isso permite “bombar” duas regiões da cadeia ao mesmo tempo.

{31}------------------------------------------------
### Comparando os Dois Lemmas do Bombeamento

| Classe             | Decomposição | Parte bombeada            |
|--------------------|--------------|---------------------------|
| Regulares          | $w = xyz$    | apenas $y$                |
| Livres de contexto | $w = uvxyz$  | $v$ e $y$ simultaneamente |
#### Uso típico

Assumimos que  $L$  é livre de contexto, escolhemos uma cadeia longa e mostramos que qualquer decomposição válida viola a forma da linguagem após bombear.

{32}------------------------------------------------
#### Exemplo de Prova: $\{a^n b^n c^n : n \geq 0\}$ não é LLC
#### Idea da prova

Suponha que  $L = \{a^n b^n c^n : n \geq 0\}$  seja livre de contexto e seja  $p$  o comprimento de bombeamento.
#### Escolha da cadeia

Tome  $w = a^p b^p c^p$ . Como  $|vxy| \leq p$ , o trecho  $vxy$  fica contido em no máximo **duas** das três regiões.
### Conclusão

Ao bombear com  $i = 0$  ou  $i = 2$ , alteramos a quantidade de símbolos em apenas uma ou duas regiões:

- ou muda o número de *as*
- ou muda o número de *bs*
- ou muda o número de *cs*
- ou mudam duas contagens, mas a terceira fica intacta

Em todos os casos, a igualdade  $|a| = |b| = |c|$  é destruída.

{33}------------------------------------------------
## Linguagens Decidíveis vs. Reconhecíveis
### Definições

- $L$  é **reconhecível** (r.e.) se existe MT  $M$  que aceita  $w \in L$
- $L$  é **decidível** (recursiva) se existe MT  $M$  que sempre para e aceita exatamente  $L$
### Relação

Decidíveis  $\subset$  Reconhecíveis  $\subset$  Todas
### Teorema

$L$  é decidível  $\iff L$  e  $\bar{L}$  são reconhecíveis.
### Exemplo

O problema da parada HALT é reconhecível mas não decidível.

{34}------------------------------------------------
## Resumo: Poderes Computacionais

The diagram illustrates the hierarchy of computational power using nested ellipses. The outermost ellipse is black and labeled "Todas as Linguagens". Inside it is a blue ellipse labeled "Recursivamente Enumeráveis". Within the blue ellipse is a green ellipse labeled "Decidíveis (Recursivas) (MT)". Inside the green ellipse is an orange ellipse labeled "Sensíveis ao Contexto". Within the orange ellipse is a red ellipse labeled "Livres de Contexto". The innermost ellipse is pink and labeled "Regulares". A faint watermark of the University of Coimbra crest is visible in the background.

Diagram showing the hierarchy of computational power with nested ellipses.

{35}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-875c6f4f441fdd3ca7e1908fd1582983_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram showing the hierarchy of computational power with nested ellipses.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 1: Operações com Cadeias

Seja  $\Sigma = \{a, b\}$ .

- 1 Liste todas as cadeias de  $\Sigma^*$  com comprimento  $\leq 3$  em ordem canônica.
- 2 Para  $w = abba$ , liste todos os prefixos, sufixos e subcadeias.
- 3 Calcule:  $|((ab)^3b)^R|$
- 4 Seja  $w = aba$ . Calcule  $w^0$ ,  $w^2$  e  $w^R$ .
- 5 Explique a diferença entre  $\varepsilon$  e  $\emptyset$ .

The image is a watermark of the University of Coimbra's coat of arms. It features a shield with a star in the center, flanked by two smaller shields. The shield is supported by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT". The entire emblem is rendered in a light gray, semi-transparent style.

Watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{36}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-63ae75eedbc0eeea2efd2ee19c2fbc7d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-911a4f4b97be8e1dcf81e58b080dc0e2_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9cc5ec27db4e35a26008bce9b9cd0bc8_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-3ddb2696ae060a47bd0e5af5d68cac65_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra crest with the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 2: Operações com Linguagens

Sejam  $L_1 = \{a^n : n \geq 0\}$  e  $L_2 = \{b^n : n \geq 0\}$ .

- 1 Descreva  $L_1 \cdot L_2$
- 2 Descreva  $L_1 \cup L_2$
- 3 Descreva  $(L_1 \cup L_2)^*$
- 4  $L_1 \cdot L_2 = L_2 \cdot L_1$ ?
- 5 Calcule  $L_1 \cap L_2$  e explique por quê.
- 6 Seja  $\Sigma = \{a, b\}$ . Descreva o complemento de  $L = \{w \in \Sigma^* : w \text{ contém } ab\}$ .

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a star in the center, surrounded by four smaller shields. The shield is supported by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVICIT".

Watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{37}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-7898f899fb291b02fbb353e0337c5514_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the University of Coimbra coat of arms, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-9642ee15d719705144037077981aaa99_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-4ca62688976b4bef770a81683f9d9eef_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 3: Cardinalidade e Representação

- 1 Por que  $\Sigma^*$  é infinito contável para todo alfabeto finito  $\Sigma$ ?
- 2 Por que o conjunto de todas as linguagens sobre  $\Sigma$  é incontável?
- 3 Explique por que a diferença entre os dois itens anteriores implica que existem linguagens que nenhuma máquina reconhece.
- 4 Se  $L = \{ab, ba\}$ , descreva  $L^2$ ,  $L^+$  e  $L^*$ .

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a star in the center, surrounded by four smaller shields. The shield is supported by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT".

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{38}------------------------------------------------
### Exercício 4: Autômatos Finitos

- 1 Construa um DFA para  $L = \{w \in \{0, 1\}^* : w \text{ contém } 010\}$
- 2 Construa um NDFA para  
 $L = \{w \in \{a, b\}^* : w \text{ termina em } ab \text{ ou } ba\}$
- 3 Converta o DFA do item anterior em NDFA
- 4 Construa um DFA para o complemento da linguagem do item 1
- 5 Construa um NDFA para  
 $L = \{w \in \{a, b\}^* : w \text{ tem número par de } a\}$

The image is a watermark of the University of Coimbra's coat of arms. It features a shield with a star in the center, surrounded by smaller stars. The shield is flanked by two supporters. Below the shield is a ribbon with the Latin motto "AD VERVM DVOCIT".

Watermark of the University of Coimbra crest, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.

{39}------------------------------------------------
### Exercício 5: Lema do Bombeamento Regular

**Desafio!** Use o Lema do Bombeamento para provar que as seguintes linguagens **não** são regulares:

- 1  $L = \{a^{n^2} : n \geq 0\}$  (potências quadradas de  $a$ )
- 2  $L = \{a^p : p \text{ é primo}\}$
- 3  $L = \{0^n 1^m : n \neq m\}$
- 4  $L = \{ww : w \in \{a, b\}^*\}$

**Dica:** Para cada linguagem, escolha cuidadosamente a cadeia  $w$  a ser bombeada.

A faint, gray watermark of the coat of arms of the University of Coimbra is visible in the background. It features a shield with a cross and a star, topped by a crown and flanked by two figures. Below the shield is a ribbon with the Latin motto "AD VERVM DVICIT".

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and a star, and the motto 'AD VERVM DVICIT'.

{40}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-d3294dc879b451b369c0b06f42e9b39f_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the PUCRS seal, featuring a shield with a star and the motto 'AD VERVM DVOCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-5dddb446832bc0d98a7265b1d79c3054_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Watermark of the coat of arms of the University of Coimbra, featuring a shield with a cross and a star, and the motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 6: Gramáticas e Hierarquia

- 1 Associe cada classe abaixo ao reconhecedor correspondente:
  - Regulares
  - Livres de contexto
  - Sensíveis ao contexto
  - Recursivamente enumeráveis
- 2 Dê um exemplo de linguagem que seja:
  - Regular
  - Livre de contexto mas não regular
  - Sensível ao contexto mas não livre de contexto
  - Recursivamente enumerável mas não sensível ao contexto

A faint, grey watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a cross and a crown, flanked by two figures. Below the shield is a ribbon with the Latin motto 'AD VERVM DVOCIT'.

Watermark of the University of Coimbra crest with the motto 'AD VERVM DVOCIT'.

{41}------------------------------------------------
### Exercício 7: Classificação de Linguagens

Classifique cada linguagem abaixo como Regular (R), Livre de Contexto (LLC), Sensível ao Contexto (LSC), Recursivamente Enumerável (R.E.), ou nenhuma das anteriores:

- 1  $\{a^n b^n : n \geq 0\}$
- 2  $\{a^n b^n c^n : n \geq 0\}$
- 3  $\{w : w \text{ tem igual número de } a\text{s e } b\text{s}\}$ , assuma o alfabeto  $\{a, b\}$
- 4  $\{ww^R : w \in \{a, b\}^*\}$
- 5  $\{a^{2^n} : n \geq 0\}$
- 6  $\{w : w \text{ não contém } aa \text{ como subcadeia}\}$ , assuma o alfabeto  $\{a, b\}$

Justifique suas respostas.

{42}------------------------------------------------
### Exercício 8: PDAs

- 1 Descreva, em alto nível, como um PDA reconhece  $L = \{0^n 1^n : n \geq 0\}$ .
- 2 Projete um PDA para  $L = \{wcw^R : w \in \{a, b\}^*\}$ .
- 3 Explique por que um autômato finito não basta para reconhecer as linguagens dos itens anteriores.
- 4 Um PDA poderia reconhecer  $\{a^n b^n c^n : n \geq 0\}$ ? Justifique.

The image is a watermark of the coat of arms of the University of Coimbra. It features a shield with a star and the motto 'AD VERVM DVICIT' (To the truth, victory). The shield is flanked by two figures, and the entire emblem is rendered in a light gray color.

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{43}------------------------------------------------
### Exercício 9: Bombeamento para LLCs

**Desafio!** Use o lema do bombeamento para linguagens livres de contexto para mostrar que as linguagens abaixo **não** são LLCs:

- 1  $\{a^n b^n c^n : n \geq 0\}$
- 2  $\{ww : w \in \{a, b\}^*\}$
- 3  $\{a^n b^n c^n d^n : n \geq 0\}$

**Dica:** analise onde o trecho  $vxy$  pode ficar e o que acontece ao bombear com  $i = 0$  ou  $i = 2$ .

A faint, gray watermark of the coat of arms of the University of Coimbra is visible in the background. It features a shield with a star and the motto 'AD VERVM DVICIT' on a banner below.

Watermark of the coat of arms of the University of Coimbra, featuring a shield with a star and the motto 'AD VERVM DVICIT'.

{44}------------------------------------------------
### Exercício 10: Reconhecível vs. Decidível

- 1 Defina, com suas palavras, o que significa uma linguagem ser reconhecível.
  - 2 Defina o que significa uma linguagem ser decidível.
  - 3 Toda linguagem decidível é reconhecível? E o contrário? Justifique.
  - 4 Explique o significado do teorema:  $L$  é decidível  $\iff L$  e  $\overline{L}$  são reconhecíveis.

A faint, stylized background image of the coat of arms of the University of Coimbra, featuring a shield with a cross and a star, and a ribbon with the Latin motto 'AD VERVM DVICIT'.

{45}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-f254a67565344d514e13763a4e556a70_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** A faint, stylized background image of the coat of arms of the University of Coimbra, featuring a shield with a cross and a star, and a ribbon with the Latin motto 'AD VERVM DVICIT'.
<!-- /IMAGE_DESCRIPTION -->
### Exercício 11: Propriedades de Fechamento

- 1 **Desafio!** Prove que se  $L_1$  e  $L_2$  são regulares, então  $L_1 \cap L_2$  é regular.

**Dica:** Construa um DFA produto.

- 2 **Desafio!** Prove que linguagens livres de contexto são fechadas sob união mas **não** sob interseção.

**Dica:** Para a não-clausura, considere  $L_1 = \{a^n b^n c^m\}$  e  $L_2 = \{a^m b^n c^n\}$ .

- 3 **Desafio!** Se  $L$  é regular e  $L'$  é livre de contexto, classifique:

- $L \cap L'$
- $L \cup L'$
- $L^*$
- $L'^*$

{46}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

A faint, semi-transparent watermark of the University of Coimbra's coat of arms is visible in the background. It features a shield with a cross and the motto 'AD VERVM DVCT' on a ribbon at the bottom.

Faint background watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVCT'.

<!-- IMAGE_DESCRIPTION: datalab-fb15f15a7d964c8490c9317e43e40c1a_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint background watermark of the University of Coimbra coat of arms, featuring a shield with a cross and the motto 'AD VERVM DVCT'.
<!-- /IMAGE_DESCRIPTION -->
