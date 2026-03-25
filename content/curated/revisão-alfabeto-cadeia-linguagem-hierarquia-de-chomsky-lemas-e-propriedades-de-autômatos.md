# Revisão: Alfabeto, Cadeia, Linguagem, Hierarquia de Chomsky, Lemas e Propriedades de **Autômatos**

Prof. Anderson Roberto Pinheiro Domingues

anderson.domingues@pucrs.br

Aula 06 Teoria da Computabilidade e Complexidade Ciência da Computação

22 de marco de 2026

![](content/images/revisão-alfabeto-cadeia-linguagem-hierarquia-de-chomsky-lemas-e-propriedades-de-autômatos-_page_0_Picture_10.png)

# Sumário

0000000

- 1 Alfabetos e Cadeias
- 2 Linguagens
- 3 Autômatos Finitos
- 4 Hierarquia de Chomsky
- 5 Exercícios

![](content/images/revisão-alfabeto-cadeia-linguagem-hierarquia-de-chomsky-lemas-e-propriedades-de-autômatos-_page_1_Picture_7.png)

### Teoria de Autômatos e Linguagens Formais

Para estudar Máquinas de Turing e computabilidade, precisamos de uma base sólida em:

- Teoria de linguagens formais
- Autômatos finitos e suas limitações
- Hierarquia de Chomsky

#### Contexto

Máguinas de Turing operam sobre cadeias de símbolos e são uma "continuação" do conteúdo estudado na disciplina de Linguagens Formais e Autômatos. Em alguns contextos, essa disciplina é chamada de "Introdução à Teoria da Computação" ou "Teoria da Computação I".

### Alfabeto

Alfabetos e Cadeias

### Definição

Um alfabeto  $\Sigma$  é um conjunto finito não-vazio de símbolos.

#### Exemplos

- $\blacksquare$   $\Sigma_0 = \{0,1\}$ , alfabeto binário
- $\blacksquare$   $\Sigma_1=\{a,b,c,\ldots,z\}$ , alfabeto das letras minúsculas
- $\blacksquare$   $\Sigma_2 = \{0, 1, 2, \ldots, 9\}$  , alfabeto dos dígitos decimais
- $\blacksquare$   $\Sigma_3 = \{a, b, \dots, z, 0, \dots, 9, \_\}$ , alfabeto dos identificadores
- $\Sigma_4 = \{+, -, \times, \div, =\}$ , alfabeto dos símbolos matemáticos

# Cadeia (String)

#### Definição

Alfabetos e Cadeias

Uma **cadeia** (ou string, palavra) sobre  $\Sigma$  é uma sequência finita de símbolos de  $\Sigma$ .

### Notações

- $w = a_1 a_2 \cdots a_n$  onde cada  $a_i \in \Sigma$
- |w| = n é o **comprimento** de w
- $\blacksquare$   $\varepsilon$  é a cadeia vazia ( $|\varepsilon|=0$ )
- w[i] ou  $w_i$  denota o i-ésimo símbolo de w

### Exemplos com $\Sigma = \{0,1\}$

- w = 0110 tem comprimento |w| = 4
- w = 0; |w| = 1
- $|\varepsilon|=0$

# Operações com Cadeias

### Concatenação

Se  $w = a_1 \cdots a_n$  e  $v = b_1 \cdots b_m$ , então:

$$w \cdot v = wv = a_1 \cdots a_n b_1 \cdots b_m$$

#### Propriedades:

- |wv| = |w| + |v|
- $w\varepsilon = \varepsilon w = w$  (elemento neutro)
- (uv)w = u(vw) (associatividade)

#### Potência

- $\mathbf{w}^0 = \varepsilon$
- $\mathbf{w}^{n+1} = \mathbf{w}^n \cdot \mathbf{w}$

Exemplo:  $(ab)^3 = ababab$ 

# Mais Operações com Cadeias

#### Cadeia Reversa

Alfabetos e Cadeias

Se  $w = a_1 a_2 \cdots a_n$ , então  $w^R = a_n \cdots a_2 a_1$ .

Exemplo:  $(abcd)^R = dcba$ 

### Subcadeia (substring)

v é **subcadeia** de w se w = xvy para algumas cadeias x, y.

#### Prefixo e Sufixo

- $v \in \mathbf{prefixo}$  de  $w \operatorname{se} w = vy$  para algum y
- $v \in \mathbf{sufixo}$  de w = xv para algum x

### Exemplo: w = abcde

- Prefixos:  $\varepsilon$ , a, ab, abc, abcd, abcde
- Sufixos:  $\varepsilon$ , e, de, cde, bcde, abcde
- Subcadeias:  $\varepsilon$ , a, b, ..., bc, bcd, ..., abcde

# O Conjunto $\Sigma^*$

#### Definição

 $\Sigma^*$  é o conjunto de **todas** as cadeias finitas sobre  $\Sigma$ , incluindo  $\varepsilon$ .

$$\Sigma^* = \bigcup_{n=0}^{\infty} \Sigma^n$$

onde  $\Sigma^n = \{ w : |w| = n \}.$ 

#### Definição Alternativa

 $\Sigma^+ = \Sigma^* - \{ \varepsilon \}$ , cadeias não-vazias

### Exemplo: $\Sigma = \{a, b\}$

$$\Sigma^{0} = \{\varepsilon\}$$

$$\Sigma^{2} = \{aa, ab, ba, bb\}$$

$$\Sigma^{1} = \{a, b\}$$

$$\Sigma^{*} = \{\varepsilon, a, b, aa, ab, ba, bb, aaa, \ldots\}$$

#### Cardinalidade

Alfabetos e Cadeias

- $|\Sigma^n| = |\Sigma|^n$
- $\Sigma$\* é infinito contável (enumerável)

#### Ordem Canônica

Podemos ordenar  $\Sigma^*$  de forma única:

- 1 Primeiro por comprimento
- 2 Depois lexicograficamente

Para  $\Sigma = \{0, 1\} \text{ com } 0 < 1$ :

$$\varepsilon$$
, 0, 1, 00, 01, 10, 11, 000, 001, . . .

### **Importância**

A ordem canônica permite **enumerar** todas as cadeias, o que é essencial para argumentos de diagonalização.

# Definição de Linguagem

### Definição

Alfabetos e Cadeias

Uma **linguagem** L sobre um alfabeto  $\Sigma$  é um subconjunto de  $\Sigma^*$ :

$$L\subseteq \Sigma^*$$

### Exemplos

- $L_1 = \{0^n 1^n : n \ge 0\} = \{\varepsilon, 01, 0011, 000111, \ldots\}$
- $L_2 = \{w \in \{0,1\}^* : w = w^R\}$ , palindromos binários
- $L_3 = \{ w \in \{a, b\}^* : |w|_a = |w|_b \}$ , mesmo número de as e bs
- $L_4 = \emptyset$ . linguagem vazia
- $L_5 = \{\varepsilon\}$ , linguagem contendo apenas a cadeia vazia

#### Observação

 $\emptyset \neq \{\varepsilon\}$ : o primeiro não possui elementos, o segundo possui um!

# Operações com Linguagens

### Operações de Conjunto

Alfabetos e Cadeias

- União:  $L_1 \cup L_2 = \{w : w \in L_1 \lor w \in L_2\}$
- Interseção:  $L_1 \cap L_2 = \{w : w \in L_1 \land w \in L_2\}$
- Complemento:  $\overline{L} = \Sigma^* L$
- Diferença:  $L_1 L_2 = L_1 \cap \overline{L_2}$

### Operações Específicas de Linguagens

- Concatenação:  $L_1 \cdot L_2 = \{xy : x \in L_1 \land y \in L_2\}$
- Potência:  $L^0 = \{\varepsilon\}, L^{n+1} = L^n \cdot L$
- Fecho de Kleene:  $L^* = \bigcup_{n=0}^{\infty} L^n$
- Fecho Positivo:  $L^+ = \bigcup_{n=1}^{\infty} L^n = L \cdot L^*$

# Exemplos de Operações

Sejam  $L_1 = \{a, ab\} \in L_2 = \{b, ba\}.$ 

#### União

Alfabetos e Cadeias

$$L_1 \cup L_2 = \{a, ab, b, ba\}$$

#### Concatenação

$$L_1 \cdot L_2 = \{ab, aba, abb, abba\}$$

#### Potências de L<sub>1</sub>

$$L_1^0 = \{\varepsilon\}$$
 $L_1^1 = \{a, ab\}$ 
 $L_1^2 = \{aa, aab, aba, abab\}$ 

#### Fecho de Kleene

$$L_1^* = \{\varepsilon, a, ab, aa, aab, aba, abab, aaa, \ldots\}$$

### Quantidade de Linguagens

#### Teorema

Alfabetos e Cadeias

O conjunto de todas as linguagens sobre  $\Sigma$  é **incontável**.

#### Prova

- Cada linguagem  $L \subseteq \Sigma^*$  é um subconjunto de  $\Sigma^*$
- O conjunto de todos os subconjuntos é  $\mathcal{P}(\Sigma^*)$
- $|\mathcal{P}(\Sigma^*)| = 2^{|\Sigma^*|} = 2^{\aleph_0}$  (incontável)

### Consequência

- Existem apenas ℵ<sub>0</sub> programas/máquinas (strings finitas)
- Existem 2<sup>ℵ0</sup> linguagens
- Logo, existem linguagens que nenhum programa pode reconhecer!

# Classes de Linguagens

### Hierarquia

0000000

Linguagens são classificadas pela "complexidade" de reconhecê-las:

![](content/images/revisão-alfabeto-cadeia-linguagem-hierarquia-de-chomsky-lemas-e-propriedades-de-autômatos-_page_13_Picture_8.png)

# Problemas de Decisão como Linguagens

#### Ideia Fundamental

Todo problema de decisão pode ser formulado como uma linguagem:

 $L_P = \{ w : w \text{ codifica uma instância com resposta SIM} \}$ 

### **Exemplos**

- **PRIMO**: {w : w codifica um número primo}
- **SAT**: {w : w codifica uma fórmula satisfatível}
- **HALT**:  $\{(M, x) : M \text{ para na entrada } x\}$

#### Decidibilidade

- L é decidível se existe algoritmo que sempre termina (sim/não)
- L é reconhecível se existe algoritmo que eventualmente termina (somente sim)

### Definição

Alfabetos e Cadeias

Um DFA é uma 5-tupla  $M = (Q, \Sigma, \delta, q_0, F)$  onde:

- Q é conjunto finito de estados
- $\Sigma$ é alfabeto de entrada
- $\bullet$   $\delta: Q \times \Sigma \rightarrow Q$  é função de transição
- $\mathbf{q}_0 \in Q$  é estado inicial
- $F \subseteq Q$  é conjunto de estados finais (de aceitação)

#### **Funcionamento**

- 1 Cursor inicia no estado  $q_0$
- 2 Um símbolo é lido da entrada e consumido
- 3 O cursor se move de acordo com  $\delta$
- A cadeia é aceita se o cursor terminar em estado  $g \in F$

# Exemplo de DFA

### Linguagem: cadeias que terminam em 01

 $L = \{ w \in \{0,1\}^* : w \text{ termina em } 01 \}$ 

![](content/images/revisão-alfabeto-cadeia-linguagem-hierarquia-de-chomsky-lemas-e-propriedades-de-autômatos-_page_16_Figure_8.png)

- $Q = \{q_0, q_1, q_2\}, \Sigma = \{0, 1\}$
- $\blacksquare$   $q_0$ : estado inicial,  $F = \{q_2\}$
- $\blacksquare$   $q_1$ : último símbolo foi 0,  $q_2$ : últimos símbolos foram 01

### Autômato Finito Não-Determinístico (NDFA)

#### Definição

Alfabetos e Cadeias

Um NDFA é uma 5-tupla  $M = (Q, \Sigma, \delta, q_0, F)$  onde:

$$\bullet \delta: Q \times (\Sigma \cup \{\varepsilon\}) \to \mathcal{P}(Q)$$

Diferenças do DFA:

- $\blacksquare$   $\delta$  retorna um  ${\bf conjunto}$  de estados
- $\blacktriangle$  Permite transições- $\varepsilon$  (sem consumir símbolo)
- Aceita se algum caminho leva a um estado final

#### Teorema

DFAs e NDFAs possuem o mesmo poder expressivo:

L é reconhecida por NDFA  $\iff$  L é reconhecida por DFA

### Linguagens Regulares

#### Definição

Uma linguagem é regular se é reconhecida por algum DFA (equivalentemente, por algum NDFA).

#### Caracterizações Equivalentes

L é regular  $\iff$  qualquer uma das seguintes:

- L é reconhecida por um DFA
- L é reconhecida por um NDFA
- L é descrita por uma expressão regular
- L é gerada por uma gramática regular

#### Fechamento

Linguagens regulares são fechadas sob:

- União, interseção, complemento, diferença
- Concatenação, fecho de Kleene, reverso

20 / 47

### Lema (Pumping Lemma)

Se L é regular, então existe  $p \ge 1$  (comprimento de bombeamento) tal que toda cadeia  $w \in L$  com |w| > p pode ser dividida como w = xyz onde:

- 1  $|xy| \leq p$
- |y| > 0

Prof. Anderson R. P. Domingues

 $xy^iz \in L$  para todo  $i \geq 0$ 

### Exemplo de Uso (estrutura de prova)

O lema é usado para provar que linguagens **não** são regulares:

- Suponha que L é regular
- Seja p o comprimento de bombeamento
- Encontre  $w \in L$  com  $|w| \ge p$  que não pode ser bombeado
- Contradição! Logo L não é regular

# Exemplo: $\{0^n1^n\}$ não é Regular

#### Afirmação

 $L = \{0^n 1^n : n \ge 0\}$  não é regular.

#### Prova

Alfabetos e Cadeias

Suponha que L é regular com comprimento de bombeamento p.

Considere  $w = 0^p 1^p \in L$  (note que  $|w| = 2p \ge p$ ).

Pela condição 1, xy consiste apenas de 0s (pois  $|xy| \le p$ ).

Pela condição 2,  $y = 0^k$  para algum k > 0.

Pela condição 3,  $xy^2z = 0^{p+k}1^p$  deveria estar em L.

Mas  $0^{p+k}1^p \notin L$  pois  $p + k \neq p$ .

Contradição! Logo L não é regular.

### Autômatos de Pilha (PDA)

#### Definição

Alfabetos e Cadeias

Um PDA é uma 7-tupla  $M = (Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)$ :

- $\Gamma$ é alfabeto da pilha
- $\delta: Q \times (\Sigma \cup \{\varepsilon\}) \times \Gamma \to \mathcal{P}(Q \times \Gamma^*)$  é a função de transição
- $Z_0 \in \Gamma$ , símbolo inicial da pilha
- Outros elementos equivalem aos encontrados em DFA e NDFA

#### Expressividade

PDAs reconhecem as **linguagens livres de contexto**. Exemplo:  $L = \{0^n 1^n : n > 0\}$  (não é regular, mas é livre de contexto).

### Limitação

PDAs não reconhecem linguagens sensíveis ao contexto ou recursivamente enumeráveis, e.g.  $\{a^nb^nc^n : n \ge 0\}$ . Para isso, precisamos de Máquinas de Turing!

# Exemplo de PDA: $\{0^n1^n : n \geq 0\}$

![](content/images/revisão-alfabeto-cadeia-linguagem-hierarquia-de-chomsky-lemas-e-propriedades-de-autômatos-_page_22_Figure_5.png)

#### Descrição das transições

- Em  $q_0$ : empilha X para cada símbolo de entrada 0
- Transição  $q_0 \to q_1$ : ao ler o primeiro 1, muda para fase de comparação
- **Em**  $q_1$ : desempilha um X para cada símbolo de entrada 1
- Transição  $q_1 \rightarrow q_f$ : aceita quando a pilha está vazia (apenas  $Z_0$  no topo)

# Exemplo de PDA: $\{0^n1^n : n \ge 0\}$ (contd.)

### Estratégia

Alfabetos e Cadeias

- I Enquanto lê 0s, empilha um símbolo X para cada 0
- $\bf 2$  Ao começar a ler 1s, desempilha um X para cada 1
- 3 Aceita quando a entrada termina junto com a pilha

### Transições principais

- $\blacksquare (q_0,0,Z_0) \rightarrow (q_0,XZ_0) \ {\rm e} \ (q_0,0,X) \rightarrow (q_0,XX)$
- $\blacksquare (q_0,1,X) \to (q_1,\varepsilon)$
- $\blacksquare \ (q_1,1,X) \to (q_1,\varepsilon)$

#### Noção intuitiva

A pilha guarda quantos 0s foram vistos; a fase de leitura dos 1s confere se a quantidade coincide.

# Outro Exemplo de PDA: $L = \{wcw^R : w \in \{a, b\}^*\}$

#### Ideia

Alfabetos e Cadeias

A letra c marca o meio da cadeia:

- antes de c, o PDA empilha os símbolos de w
- depois de c, o PDA compara a entrada com o topo da pilha

### Exemplo de execução

Para a cadeia abcba com marcador central, isto é. abcba = abcba:

- 🔳 lê a, b e empilha a, b
- 2 lê c e muda para a fase de comparação
- 3 lê b, a e desempilha b, a

#### Conclusão

Um PDA consegue comparar partes da entrada quando a estrutura é aninhada ou espelhada. Já dependências entre três contagens independentes exigem mais expressividade.

#### Definição

Uma gramática é uma 4-tupla  $G = (V, \Sigma, R, S)$  onde:

- V conjunto finito de variáveis (não-terminais)
- $\Sigma$  alfabeto de terminais (disjunto de V)
- $R \subseteq (V \cup \Sigma)^* V (V \cup \Sigma)^* \times (V \cup \Sigma)^*$  regras de produção
- $S \in V$  símbolo inicial

#### Derivação

$$\alpha \Rightarrow \beta$$
 se  $\alpha = \gamma A \delta$ ,  $\beta = \gamma \omega \delta$  e  $(A \to \omega) \in R$ .  
 $\alpha \Rightarrow^* \beta$  se existe sequência  $\alpha = \alpha_0 \Rightarrow \alpha_1 \Rightarrow \cdots \Rightarrow \alpha_n = \beta$ .

### Linguagem Gerada

$$L(G) = \{ w \in \Sigma^* : S \Rightarrow^* w \}$$

# A Hierarquia de Chomsky

### Classificação por Restrições nas Regras

Tipo 0 Gramáticas irrestritas:  $\alpha \to \beta$  (qualquer)

Tipo 1 Sensíveis ao contexto:  $\alpha A\beta \rightarrow \alpha \gamma \beta$  com  $|\gamma| > 1$ 

Tipo 2 Livres de contexto:  $A \rightarrow \gamma$ 

Tipo 3 Regulares:  $A \rightarrow aB$  ou  $A \rightarrow a$  ou  $A \rightarrow \varepsilon$ 

#### Inclusões

Regulares  $\subset$  LLCs  $\subset$  LSCs  $\subset$  R.E.

Todas as inclusões são estritas.

# Correspondência com Autômatos

| Tipo | Linguagens                 | Reconhecedor                  |
|------|----------------------------|-------------------------------|
| 3    | Regulares                  | Autômato Finito               |
| 2    | Livres de Contexto         | Autômato com Pilha            |
| 1    | Sensíveis ao Contexto      | Autômato Linearmente Limitado |
| 0    | Recursivamente Enumeráveis | Máquina de Turing             |

#### Observação

Alfabetos e Cadeias

- Cada nível adiciona "memória"
- AFD: memória finita (estados)
- AP: memória de pilha (LIFO)
- Al I · memória linear no tamanho da entrada
- MT: memória ilimitada (fita infinita)

# Exemplos de Linguagens em Cada Nível

### Tipo 3: Regulares

Alfabetos e Cadeias

- {w : w contém 01 como subcadeia}
- $\blacksquare$  {w : |w| é par}
- Qualquer linguagem finita

#### Tipo 2: Livres de Contexto

- $\bullet$  {0<sup>n</sup>1<sup>n</sup> : n > 0}
- $\blacksquare$  { $ww^R$  :  $w \in \{a, b\}^*$ }, palindromos pares
- Expressões aritméticas bem formadas

#### Tipo 1: Sensíveis ao Contexto

- $\blacksquare \{a^n b^n c^n : n > 0\}$
- $\blacksquare$  {ww :  $w \in \{a, b\}^*$ }, cópias

# Tipo 0: Linguagens Recursivamente Enumeráveis

#### Característ<u>icas</u>

Alfabetos e Cadeias

- Reconhecidas por Máquinas de Turing
- Nenhuma restrição nas regras de produção
- Podem não parar para cadeias rejeitadas

#### Exemplos

- Problema da Parada (HALT)
- Qualquer linguagem decidível
- Linguagens com comportamento não-determinístico arbitrário

#### Observação importante

Nem toda linguagem recursivamente enumerável é decidível. Existem linguagens que podem ser reconhecidas (MT para sim) mas não há MT que sempre para.

Referências

# Lema do Bombeamento para LLCs

#### Enunciado

Se L é uma linguagem livre de contexto, então existe p > 1 tal que toda cadeia  $w \in L$  com  $|w| \ge p$  pode ser escrita como

$$w = uvxyz$$

de modo que:

- 1  $|vxy| \leq p$
- |vv| > 0
- 3  $uv^i x v^i z \in L$  para todo i > 0

#### Intuição

Em árvores de derivação suficientemente grandes, algum não-terminal se repete em um caminho. Isso permite "bombear" duas regiões da cadeia ao mesmo tempo.

# Comparando os Dois Lemas do Bombeamento

| Classe             | Decomposição | Parte bombeada        |
|--------------------|--------------|-----------------------|
| Regulares          | w = xyz      | apenas y              |
| Livres de contexto | w = uvxyz    | v e y simultaneamente |

#### Uso típico

Assumimos que L é livre de contexto, escolhemos uma cadeia longa e mostramos que qualquer decomposição válida viola a forma da linguagem após bombear.

# Exemplo de Prova: $\{a^n b^n c^n : n \ge 0\}$ não é LLC

### Ideia da prova

Suponha que  $L = \{a^n b^n c^n : n \ge 0\}$  seja livre de contexto e seja po comprimento de bombeamento.

#### Escolha da cadeia

Tome  $w = a^p b^p c^p$ . Como |vxy| < p, o trecho vxy fica contido em no máximo duas das três regiões.

#### Conclusão

Ao bombear com i=0 ou i=2, alteramos a quantidade de símbolos em apenas uma ou duas regiões:

- ou muda o número de as
- ou muda o número de bs
- ou muda o número de cs
- ou mudam duas contagens, mas a terceira fica intacta

Em todos os casos, a igualdade |a| = |b| = |c| é destruída.

# Linguagens Decidíveis vs. Reconhecíveis

### Definicões

- L é **reconhecível** (r.e.) se existe MT M que aceita  $w \in L$
- L é **decidível** (recursiva) se existe MT M que sempre para e aceita exatamente L

### Relação

Decidíveis $\subset$ Reconhecíveis $\subset$ Todas

#### Teorema

L é decidível  $\iff$  L e  $\overline{L}$  são reconhecíveis.

### Exemplo

O problema da parada HALT é reconhecível mas não decidível.

### Resumo: Poderes Computacionais

0000000

![](content/images/revisão-alfabeto-cadeia-linguagem-hierarquia-de-chomsky-lemas-e-propriedades-de-autômatos-_page_34_Picture_2.png)

![](_page_34_Picture_3.jpeg)

# Exercício 1: Operações com Cadeias

Seja  $\Sigma = \{a, b\}$ .

Alfabetos e Cadeias

- I Liste todas as cadeias de  $\Sigma^*$  com comprimento < 3 em ordem canônica.
- 2 Para w = abba, liste todos os prefixos, sufixos e subcadeias.
- 3 Calcule:  $|((ab)^3b)^R|$
- 4 Seja w = aba. Calcule  $w^0$ ,  $w^2$  e  $w^R$ .
- **5** Explique a diferença entre  $\varepsilon$  e  $\emptyset$ .

Alfabetos e Cadeias

# Exercício 2: Operações com Linguagens

Sejam  $L_1 = \{a^n : n \ge 0\}$  e  $L_2 = \{b^n : n \ge 0\}$ .

- 1 Descreva  $L_1 \cdot L_2$
- **2** Descreva  $L_1 \cup L_2$
- $\blacksquare$  Descreva  $(L_1 \cup L_2)^*$
- 4  $L_1 \cdot L_2 = L_2 \cdot L_1$ ?
- **5** Calcule  $L_1 \cap L_2$  e explique por quê.
- 6 Seja  $\Sigma = \{a, b\}$ . Descreva o complemento de  $L = \{ w \in \Sigma^* : w \text{ contém } ab \}.$

![](content/images/revisão-alfabeto-cadeia-linguagem-hierarquia-de-chomsky-lemas-e-propriedades-de-autômatos-_page_36_Picture_13.png)

Alfabetos e Cadeias

# Exercício 3: Cardinalidade e Representação

- **1** Por que  $\Sigma^*$  é infinito contável para todo alfabeto finito  $\Sigma$ ?
- 2 Por que o conjunto de todas as linguagens sobre  $\Sigma$  é incontável?
- 3 Explique por que a diferença entre os dois itens anteriores implica que existem linguagens que nenhuma máquina reconhece.
- 4 Se  $L = \{ab, ba\}$ , descreva  $L^2$ ,  $L^+$  e  $L^*$ .

### Exercício 4: Autômatos Finitos

Alfabetos e Cadeias

- 1 Construa um DFA para  $L = \{w \in \{0,1\}^* : w \text{ contém } 010\}$
- 2 Construa um NDFA para  $L = \{w \in \{a, b\}^* : w \text{ termina em } ab \text{ ou } ba\}$
- Converta o DFA do item anterior em NDFA
- 4 Construa um DFA para o complemento da linguagem do item
- 5 Construa um NDFA para  $L = \{w \in \{a, b\}^* : w \text{ tem número par de } as\}$

Alfabetos e Cadeias

# Exercício 5: Lema do Bombeamento Regular

**Desafio!** Use o Lema do Bombeamento para provar que as seguintes linguagens não são regulares:

- 1  $L = \{a^{n^2} : n \ge 0\}$  (potências quadradas de a)
- $L = \{a^p : p \text{ é primo}\}$
- $L = \{0^n 1^m : n \neq m\}$
- 4  $L = \{ww : w \in \{a, b\}^*\}$

**Dica**: Para cada linguagem, escolha cuidadosamente a cadeia w a ser hombeada

# Exercício 6: Gramáticas e Hierarquia

- Associe cada classe abaixo ao reconhecedor correspondente:
  - Regulares

Alfabetos e Cadeias

- Livres de contexto
- Sensíveis ao contexto
- Recursivamente enumeráveis
- 2 Dê um exemplo de linguagem que seja:
  - Regular
  - Livre de contexto mas não regular
  - Sensível ao contexto mas não livre de contexto
  - Recursivamente enumerável mas não sensível ao contexto

# Exercício 7: Classificação de Linguagens

Classifique cada linguagem abaixo como Regular (R), Livre de Contexto (LLC), Sensível ao Contexto (LSC), Recursivamente Enumerável (R.E.), ou nenhuma das anteriores:

- 1  $\{a^nb^n: n \geq 0\}$
- 2  $\{a^n b^n c^n : n \ge 0\}$
- $\{w: w \text{ tem igual número de } as e bs\}$ , assuma o alfabeto  $\{a,b\}$
- 4  $\{ww^R : w \in \{a, b\}^*\}$
- 5  $\{a^{2^n}: n \geq 0\}$
- 6  $\{w : w \text{ não contém } aa \text{ como subcadeia}\}$ , assuma o alfabeto  $\{a,b\}$

Justifique suas respostas.

### Exercício 8: PDAs

Alfabetos e Cadeias

- Descreva, em alto nível, como um PDA reconhece  $L = \{0^n 1^n : n \ge 0\}.$
- **2** Projete um PDA para  $L = \{wcw^R : w \in \{a, b\}^*\}$
- 3 Explique por que um autômato finito não basta para reconhecer as linguagens dos itens anteriores.
- 4 Um PDA poderia reconhecer  $\{a^nb^nc^n : n \ge 0\}$ ? Justifique.

# Exercício 9: Bombeamento para LLCs

**Desafio!** Use o lema do bombeamento para linguagens livres de contexto para mostrar que as linguagens abaixo **não** são LLCs:

- 1  $\{a^n b^n c^n : n \ge 0\}$
- 2  $\{ww : w \in \{a, b\}^*\}$

**Dica**: analise onde o trecho vxy pode ficar e o que acontece ao bombear com i = 0 ou i = 2.

### Exercício 10: Reconhecível vs. Decidível

- Defina, com suas palavras, o que significa uma linguagem ser reconhecível.
- 2 Defina o que significa uma linguagem ser decidível.
- 3 Toda linguagem decidível é reconhecível? E o contrário? Justifique.
- 4 Explique o significado do teorema: L é decidível  $\iff L$  e  $\overline{L}$  são reconhecíveis.

Alfabetos e Cadeias

Exercícios

Referências

Alfabetos e Cadeias

### Exercício 11: Propriedades de Fechamento

**1** Desafio! Prove que se  $L_1$  e  $L_2$  são regulares, então  $L_1 \cap L_2$  é regular.

**Dica**: Construa um DFA produto.

**Desafio!** Prove que linguagens livres de contexto são fechadas sob união mas não sob interseção.

**Dica**: Para a não-clausura, considere  $L_1 = \{a^n b^n c^m\}$  e  $L_2 = \{a^m b^n c^n\}.$ 

- **Desafio!** Se L é regular e L' é livre de contexto, classifique:
  - $\blacksquare I \cap I'$
  - / U/′

  - **I** //\*

### Referências I

Alfabetos e Cadeias

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. Introduction to Automata Theory, Languages, and Computation. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Exercícios

Referências
