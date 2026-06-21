<!-- EXEC_SUMMARY_START -->
## Sumário
> *Leia antes de varrer o arquivo. Vá direto à seção relevante para a pergunta do aluno.*

- **Sumário**
- **Contexto Histórico**
  - O Problema de Hilbert (1928)
  - A Resposta de Turing (1936)
  - Importância
  - Ideia Intuitiva
- **Componentes de uma Máquina de Turing**
  - Funcionamento Básico
  - Comparação com Autômatos Finitos
  - Diferença Fundamental
- **Por que Máquinas de Turing?**
  - Generalidade
  - Robustez
  - Padrão de Referência
- **Definição de Máquina de Turing**
  - Definição
  - Convenções
  - A Função de Transição
  - Configuração
  - Definição
  - Relação de Transição
  - Definição
  - Regras
  - Fecho Transitivo
  - Computação
  - Configuração Inicial
  - Definições
  - Linguagem Reconhecida
  - Diagrama de Estados
- **Convenções**
  - Descrição de Alto Nível
  - Níveis de Descrição
  - Ideia
  - Estados
  - Descrição de Alto Nível
  - Complexidade
  - Descrição de Alto Nível
  - Problema
  - Descrição
- **Máquinas de Turing como Reconhecedores**
  - Reconhecedor de Linguagem
  - Decisor de Linguagem
  - Diferença
  - Definições Fundamentais
  - Linguagem Turing-reconhecível
  - Linguagem Turing-decidível
  - Relação
- **Por que “Recursivamente Enumerável”?**
  - Teorema
  - Enumerador
  - Equivalência
  - Propriedades de Linguagens R.E.
  - Fechamento
  - Não Fechamento
  - Linguagens Decidíveis vs. Reconhecíveis
  - Teorema
  - O Problema da Parada
  - Afirmação
  - Reconhecibilidade
  - Hierarquia de Linguagens
- **Resumo**
- **Classes de Linguagens**
- **Fatos Importantes**
  - Exercício 1: Rastreamento de Configurações
  - Exercício 2: Projeto de MTs
  - Exercício 3: Operações com MTs
  - Exercício 4: Reconhecibilidade e Decidibilidade
  - Exercício 5: Enumeradores
  - Desafio: MT para Multiplicação
  - Especificação
- **Referências I**
- **Imagens Curadas**

<!-- EXEC_SUMMARY_END -->
{0}------------------------------------------------

# Máquinas de Turing e Linguagens Recursivamente Enumeráveis

Prof. Anderson Roberto Pinheiro Domingues

[anderson.domingues@pucrs.br](mailto:anderson.domingues@pucrs.br)

Aula 07

Teoria da Computabilidade e Complexidade  
Ciência da Computação

27 de março de 2026

The logo of the Escola Politécnica da PUCRS. It features a small crest on the left with a shield, a cross, and a star. To the right of the crest, the text "PUCRS" is written in a small font, followed by a vertical line and then "ESCOLA POLITÉCNICA" in a larger, bold, blue font.

Logo of Escola Politécnica da PUCRS

{1}------------------------------------------------
## Sumário

- 1 Introdução às Máquinas de Turing
- 2 Definição Formal
- 3 Exemplos de Máquinas de Turing
- 4 Linguagens Recursivamente Enumeráveis
- 5 Exercícios

The image is a large, light gray watermark of the coat of arms of the University of São Paulo (USP). It features a shield with a central vertical band containing a stylized 'M' and 'U' monogram, flanked by two vertical bands with a repeating cross pattern. Above the shield is a crown, and on either side are crossed keys. A banner at the bottom reads 'AD VERVM DVCIT'.

Coat of arms of the University of São Paulo (USP)

{2}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-cb00037bd3b3af9720d5551ad2f818dd_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-eca7fa4eb8dd1303e4bd56aee6555b2d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-c2c3abb173421fc58a8c014e41562eb3_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-4a7229c854e8286e8d38fc192a3ba1d4_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-aa7a4ea43951479b7e7b4c530ea5bc2d_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-7b86546611b0b5929a4da6eb922e559c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of São Paulo (USP)
<!-- /IMAGE_DESCRIPTION -->
## Contexto Histórico
### O Problema de Hilbert (1928)

**Entscheidungsproblem:** Existe um procedimento mecânico que decide se qualquer afirmação matemática é verdadeira ou falsa?
### A Resposta de Turing (1936)

Alan Turing formalizou a noção de “procedimento mecânico” através de um modelo abstrato de computação: a **Máquina de Turing**.

Usando este modelo, provou que o Entscheidungsproblem é **impossível**.
### Importância

A Máquina de Turing é o modelo teórico fundamental de computação, usado para definir:

{3}------------------------------------------------
### Ideia Intuitiva
## Componentes de uma Máquina de Turing

- 1 Fita:** memória infinita dividida em células
- 2 Cabeçote:** lê e escreve na fita, move-se
- 3 Controle:** estados que determinam o comportamento

The diagram illustrates the components of a Turing Machine. It shows a horizontal row of cells representing the tape, labeled 'Fita (infinita)' below. The cells contain the sequence:  $\square$ ,  $a$ ,  $b$ ,  $b$ ,  $a$ ,  $\square$ ,  $\square$ ,  $\square$ ,  $\square$ ,  $\square$ ,  $\square$ , followed by an ellipsis. Above the fourth cell (containing 'b'), the label 'Cabeçote' has a downward arrow pointing to it. To the right of the tape, the label 'Controle' is positioned above a circle containing the state  $q_2$ . Ellipses are also present at the far left and far right of the tape row.

Diagram of a Turing Machine components: Fita (infinite tape) and Controle (control unit).

{4}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-0c9723d1620cf51bc2b7a380ce7e23c0_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagram of a Turing Machine components: Fita (infinite tape) and Controle (control unit).
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION: datalab-ddc7460821484f1ae2835c67955c554c_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama de Estados de uma Máquina de Turing
<!-- /IMAGE_DESCRIPTION -->
### Funcionamento Básico

A cada passo, a MT:

- 1 **Lê** o símbolo na posição atual da fita
- 2 Baseada no estado atual e símbolo lido:
  - **Escreve** um símbolo na posição atual
  - **Move** o cabeçote (esquerda ou direita)
  - **Muda** para um novo estado
- 3 Continua até atingir um estado de parada

“Tipos” de Parada

- **Aceita**: para em estado de aceitação
- **Rejeita**: para em estado de rejeição
- **Loop**: nunca para (não é uma parada!)

{5}------------------------------------------------
### Comparação com Autômatos Finitos

| Característica   | DFA                  | PDA                           | MT                 |
|------------------|----------------------|-------------------------------|--------------------|
| Fita/Entrada     | Somente leitura      | Somente leitura               | Leitura e escrita  |
| Memória auxiliar | Nenhuma              | Pilha                         | Fita infinita      |
| Movimento        | Somente direita      | Somente direita               | Esquerda e direita |
| Memória total    | Finita (estados)     | Finita (estados) + Pilha      | Infinita (fita)    |
| Parada           | Sempre para          | Sempre para                   | Pode não parar     |
| Poder            | Linguagens regulares | Linguagens livres de contexto | Todas computáveis  |
### Diferença Fundamental

A fita infinita com leitura/escrita dá à MT memória ilimitada e flexível, permitindo reconhecer linguagens muito mais complexas que DFAs/NDFAs e PDAs.

{6}------------------------------------------------
## Por que Máquinas de Turing?
### Generalidade

Toda computação realizada por qualquer computador pode ser simulada por uma MT (**Tese** de Church-Turing).
### Robustez

Variações do modelo (múltiplas fitas, não-determinismo, etc.) têm o mesmo poder computacional.
### Padrão de Referência

A MT é o “melhor que temos” para definir computabilidade:

- “Computável” = “Computável por MT”
- “Decidível” = “Decidível por MT que sempre para”

{7}------------------------------------------------
## Definição de Máquina de Turing
### Definição

É uma 7-tupla  $M = (Q, \Sigma, \Gamma, \delta, q_0, q_{acc}, q_{rej})$ :

- $Q$ , conjunto finito de **estados**
- $\Sigma$ , **alfabeto de entrada** (não contém  $\sqcup$ )
- $\Gamma$ , **alfabeto da fita**, com  $\Sigma \subset \Gamma$  e  $\sqcup \in \Gamma$
- $\delta : Q \times \Gamma \rightarrow Q \times \Gamma \times \{L, R\}$ , **função de transição**
- $q_0 \in Q$ , **estado inicial**
- $q_{acc} \in Q$ , **estado de aceitação**
- $q_{rej} \in Q$ , **estado de rejeição** ( $q_{rej} \neq q_{acc}$ )
### Convenções

- $\sqcup$  é o símbolo **branco** (blank)
- $L$  = mover à esquerda,  $R$  = mover à direita
- A máquina para ao atingir  $q_{acc}$  ou  $q_{rej}$

{8}------------------------------------------------
### A Função de Transição
#### Interpretação de $\delta(q, a) = (q', b, D)$

Se a MT está no estado  $q$  lendo o símbolo  $a$ , então:

- 1 Escreve  $b$  na posição atual (substituindo  $a$ )
- 2 Move o cabeçote na direção  $D$  (L ou R)
- 3 Muda para o estado  $q'$
#### Exemplo

$$\delta(q_1, a) = (q_2, b, R)$$

“Se está em  $q_1$  lendo  $a$ : escreve  $b$ , move à direita, vai para  $q_2$ ”
#### Observação

$\delta$  não está definida para  $q_{acc}$  e  $q_{rej}$ . A máquina para nestes estados.

{9}------------------------------------------------
### Configuração
### Definição

Uma **configuração** descreve completamente o estado atual da computação:

$$(q, u, v)$$

onde:

- $q \in Q$ , estado atual
- $u \in \Gamma^*$ , conteúdo da fita à esquerda do cabeçote
- $v \in \Gamma^+$ , conteúdo da fita a partir do cabeçote (inclui posição atual)
#### Notação Alternativa

Escrevemos a configuração como  $uqv$ , onde  $q$  indica a posição do cabeçote (antes do primeiro símbolo de  $v$ ).

Exemplo:  $abq_2bba$  significa:

{10}------------------------------------------------
### Relação de Transição
### Definição

$C_1 \vdash C_2$  (“ $C_1$  leva a  $C_2$ ”) se a MT vai da configuração  $C_1$  para  $C_2$  em um passo.
### Regras

Se  $\delta(q, b) = (q', c, R)$ :

$$uaq bv \vdash uacq' v$$

Se  $\delta(q, b) = (q', c, L)$ :

$$uaq bv \vdash uq' acv$$
### Fecho Transitivo

$C_1 \vdash^* C_2$  se existe sequência  $C_1 \vdash C'_1 \vdash \dots \vdash C_2$ .

{11}------------------------------------------------
### Computação
### Configuração Inicial

Para entrada  $w = w_1 w_2 \cdots w_n$ :

$$C_0 = q_0 w_1 w_2 \cdots w_n$$

(estado inicial, cabeçote na primeira posição, fita contém  $w$ )
### Definições

A MT  $M$  na entrada  $w$ :

- **Aceita** se  $q_0 w \vdash^* u q_{acc} v$  para alguns  $u, v$
- **Rejeita** se  $q_0 w \vdash^* u q_{rej} v$  para alguns  $u, v$
- **Loop** (não para) caso contrário
### Linguagem Reconhecida

$$L(M) = \{w \in \Sigma^* : M \text{ aceita } w\}$$

{12}------------------------------------------------
### Diagrama de Estados
## Convenções

- Estados são círculos
- Estado inicial: seta entrando
- Estado de aceitação: círculo duplo
- Transições: setas rotuladas  $a \rightarrow b, D$

O diagrama apresenta três estados:

- q<sub>0</sub>**: Estado inicial, representado por um círculo simples com uma seta rotulada "start" apontando para ele.
- q<sub>1</sub>**: Estado intermediário, representado por um círculo simples.
- q<sub>acc</sub>**: Estado de aceitação, representado por um círculo duplo.

As transições são as seguintes:

- De **q<sub>0</sub>** para **q<sub>1</sub>**: Uma seta rotulada  $a \rightarrow X, R$ .
- De **q<sub>1</sub>** para **q<sub>1</sub>** (auto-loop): Uma seta curva no topo do estado rotulada  $a \rightarrow a, R$ .
- De **q<sub>1</sub>** para **q<sub>acc</sub>**: Uma seta rotulada  $\sqcup \rightarrow \sqcup, L$ .

Diagrama de Estados de uma Máquina de Turing

Transição  $a \rightarrow X, R$ : lendo  $a$ , escreve  $X$ , move à direita.

{13}------------------------------------------------
### Descrição de Alto Nível
### Níveis de Descrição

Podemos descrever uma MT em três níveis:

- 1 **Formal**: 7-tupla completa com  $\delta$  explícita
- 2 **Implementação**: descrição do funcionamento dos estados e transições
- 3 **Alto nível**: descrição algorítmica em português/pseudocódigo
#### Exemplo de Alto Nível

MT para  $L = \{0^n 1^n : n \geq 0\}$ , com entrada  $w$ :

- 1 Se  $w = \varepsilon$ , aceite
- 2 Marque o primeiro 0 não-marcado com X
- 3 Mova à direita até encontrar um 1 não-marcado
- 4 Se não encontrar, rejeite. Senão, marque-o com Y
- 5 Volte ao início e repita
- 6 Se todos os 0s e 1s estão marcados, aceite

{14}------------------------------------------------
##### Exemplo 1: $L = \{0^n 1^n : n \geq 0\}$
### Ideia

Repetidamente marque um 0 e um 1 correspondente, até todos estarem marcados.
### Estados

- $q_0$ : estado inicial, procura 0 para marcar
- $q_1$ : movendo à direita, procurando 1
- $q_2$ : movendo à esquerda, voltando ao início
- $q_{acc}$ : aceita
- $q_{rej}$ : rejeita
#### Alfabeto

$\Sigma = \{0, 1\}, \Gamma = \{0, 1, X, Y, \sqcup\}$

{15}------------------------------------------------
#### Exemplo 1: Transições

| Estado | Símbolo  | Transição                                     |
|--------|----------|-----------------------------------------------|
| $q_0$  | 0        | $(q_1, X, R)$ ; marca 0, busca 1              |
| $q_0$  | Y        | $(q_0, Y, R)$ ; pula Y                        |
| $q_0$  | $\sqcup$ | $(q_{acc}, \sqcup, R)$ ; todos marcados       |
| $q_1$  | 0        | $(q_1, 0, R)$ ; pula 0s                       |
| $q_1$  | Y        | $(q_1, Y, R)$ ; pula Ys                       |
| $q_1$  | 1        | $(q_2, Y, L)$ ; marca 1, volta                |
| $q_1$  | $\sqcup$ | $(q_{rej}, \sqcup, R)$ ; sem 1 correspondente |
| $q_2$  | 0, Y     | $(q_2, \cdot, L)$ ; volta                     |
| $q_2$  | X        | $(q_0, X, R)$ ; reinicia                      |

{16}------------------------------------------------
##### Exemplo 1: Execução em 0011

| Passo | Configuração |
|-------|--------------|
| 0     | $q_0$ 0011   |
| 1     | $X q_1$ 011  |
| 2     | $X0 q_1$ 11  |
| 3     | $X q_2$ 0Y1  |
| 4     | $q_2 X0Y1$   |
| 5     | $X q_0$ 0Y1  |
| 6     | $XX q_1$ Y1  |
| 7     | $XXY q_1$ 1  |
| 8     | $XX q_2$ YY  |
| 9     | $X q_2$ XYY  |
| 10    | $XX q_0$ YY  |
| 11    | $XXY q_0$ Y  |
| 12    | $XXYY q_0$ $\square$ |
| 13    | Aceita!      |

Coat of arms of the University of Coimbra, featuring a shield with a star and a banner reading 'AD VERVM DVCIT'.

{17}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-c3ee41c6d46565ab4198d0a9c69108c5_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Coat of arms of the University of Coimbra, featuring a shield with a star and a banner reading 'AD VERVM DVCIT'.
<!-- /IMAGE_DESCRIPTION -->
##### Exemplo 2: $L = \{ww : w \in \{a, b\}^*\}$
### Descrição de Alto Nível

“Na entrada  $x$ :

- 1 Se  $|x|$  é ímpar, rejeite
- 2 Marque a primeira metade distinguindo-a da segunda
- 3 Compare símbolo a símbolo as duas metades
- 4 Se todas as comparações forem iguais, aceite; senão, rejeite”
### Complexidade

Esta MT é mais complexa que a anterior, pois precisa:

- Encontrar o meio da cadeia
- Manter controle de posições correspondentes

Existem várias estratégias de implementação.

{18}------------------------------------------------
#### Exemplo 3: $L = \{a^n b^n c^n : n \geq 0\}$
### Descrição de Alto Nível

“Na entrada  $w$ :

- 1 Se  $w = \varepsilon$ , aceite
- 2 Verifique se  $w$  tem a forma  $a^*b^*c^*$ ; senão, rejeite
- 3 Marque um  $a$ , um  $b$  e um  $c$  por vez
- 4 Se alguma letra acabar antes das outras, rejeite
- 5 Se todas acabarem juntas, aceite”
#### Observação

Esta linguagem **não** é livre de contexto! MTs podem reconhecer linguagens que APs não conseguem.

{19}------------------------------------------------
#### Exemplo 4: Soma Unária
### Problema

Dados  $m$  e  $n$  em unário (sequências de 1s), calcular  $m + n$ .

Entrada:  $1^m \# 1^n$  Saída esperada:  $1^{m+n}$
### Descrição

“Na entrada  $1^m \# 1^n$ :

- 1 Substitua o  $\#$  por 1
- 2 Apague o último 1 (para compensar o  $\#$  extra)
- 3 Pare”
#### Exemplo

$111\#11 \rightarrow 11111 \rightarrow 1111$

$3 + 2 = 5 \checkmark$

{20}------------------------------------------------
## Máquinas de Turing como Reconhecedores
### Reconhecedor de Linguagem

Uma MT  $M$  **reconhece** uma linguagem  $L$  se:

$$L = \{w : M \text{ aceita } w\}$$

Note que  $M$  pode entrar em loop para  $w \notin L$ .
### Decisor de Linguagem

Uma MT  $M$  **decide** uma linguagem  $L$  se:

- $M$  sempre para (para toda entrada)
- $M$  aceita  $w$  sse  $w \in L$
### Diferença

Reconhecedor: pode não parar para entradas fora de  $L$ .

Decisor: sempre para, com resposta correta.

{21}------------------------------------------------
### Definições Fundamentais
### Linguagem Turing-reconhecível

Uma linguagem  $L$  é **Turing-reconhecível** (ou recursivamente enumerável, r.e.) se existe uma MT  $M$  tal que:

$$L = L(M) = \{w : M \text{ aceita } w\}$$
### Linguagem Turing-decidível

Uma linguagem  $L$  é **Turing-decidível** (ou recursiva, ou decidível) se existe uma MT  $M$  que:

- 1 Para em todas as entradas
- 2 Aceita exatamente as cadeias de  $L$
### Relação

Toda linguagem decidível é reconhecível, mas a recíproca é **falsa**.

{22}------------------------------------------------
## Por que “Recursivamente Enumerável”?
### Teorema

Uma linguagem  $L$  é Turing-reconhecível sse existe uma MT que **enumera** os elementos de  $L$ .
### Enumerador

Uma MT  $E$  é um **enumerador** para  $L$  se:

- $E$  tem uma “fita de saída” especial
- $E$  escreve cadeias de  $L$  na saída, separadas por marcador
- Toda cadeia de  $L$  é eventualmente escrita
### Equivalência

$L$  é r.e.  $\iff L$  pode ser enumerada por alguma MT.

Daí o nome “recursivamente enumerável”.

{23}------------------------------------------------
### Propriedades de Linguagens R.E.
### Fechamento

Linguagens r.e. são fechadas sob:

- União: se  $L_1, L_2$  são r.e., então  $L_1 \cup L_2$  é r.e.
- Interseção: se  $L_1, L_2$  são r.e., então  $L_1 \cap L_2$  é r.e.
- Concatenação: se  $L_1, L_2$  são r.e., então  $L_1 \cdot L_2$  é r.e.
- Fecho de Kleene: se  $L$  é r.e., então  $L^*$  é r.e.
### Não Fechamento

Linguagens r.e. **não** são fechadas sob complemento!

Se  $L$  é r.e.,  $\bar{L}$  pode não ser r.e.

{24}------------------------------------------------
### Linguagens Decidíveis vs. Reconhecíveis
### Teorema

$L$  é decidível  $\iff L$  e  $\bar{L}$  são reconhecíveis.
#### Prova ( $\Rightarrow$ )

Se  $L$  é decidível, a MT decisor  $M$  reconhece  $L$ .

Trocando  $q_{acc}$  e  $q_{rej}$  de  $M$ , obtemos decisor para  $\bar{L}$ .
#### Prova ( $\Leftarrow$ )

Sejam  $M_1$  e  $M_2$  reconhecedores de  $L$  e  $\bar{L}$ .

Construa  $M$  que simula  $M_1$  e  $M_2$  em paralelo:

- Se  $M_1$  aceita, aceite
- Se  $M_2$  aceita, rejeite

Para toda  $w$ , ou  $w \in L$  ou  $w \in \bar{L}$ , então  $M$  sempre para.

{25}------------------------------------------------
#### Exemplo: Uma Linguagem R.E. não Decidível
### O Problema da Parada

$$HALT = \{ \langle M, w \rangle : M \text{ é MT que para na entrada } w \}$$
### Afirmação

$HALT$  é reconhecível mas não decidível.
### Reconhecibilidade

Construa MT  $U$  que, na entrada  $\langle M, w \rangle$ :

- 1 Simula  $M$  em  $w$
- 2 Se  $M$  para, aceita

$U$  reconhece  $HALT$  (aceita sse  $M$  para em  $w$ ).

{26}------------------------------------------------
### Hierarquia de Linguagens

O diagrama ilustra a hierarquia das linguagens de computação através de três elipses concêntricas. A maior elipse, com contorno preto, representa 'Todas as Linguagens'. Dentro dela, uma elipse azul com contorno sólido representa as 'Reconhecíveis (R.E.)'. A menor elipse, com contorno verde sólido, representa as 'Decidíveis'. Uma terceira elipse, com contorno vermelho tracejado, representa as 'co-R.E.' e está parcialmente sobreposta à elipse azul. O rótulo 'HALT' está localizado na parte inferior esquerda da elipse azul, e o rótulo  $\overline{HALT}$  está na parte inferior direita da elipse vermelha tracejada. No fundo da slide, há uma imagem desbotada do brasão da Universidade de Coimbra.

Diagrama da hierarquia de linguagens de computação

- $\text{Decidíveis} = \text{R.E.} \cap \text{co-R.E.}$
- $HALT$  é R.E. mas não co-R.E.
- $\overline{HALT}$  é co-R.E. mas não R.E.

{27}------------------------------------------------

<!-- IMAGE_DESCRIPTION: datalab-4cde160bcc69b7b6c81b648dd0e4252e_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Diagrama da hierarquia de linguagens de computação
<!-- /IMAGE_DESCRIPTION -->
## Resumo
## Classes de Linguagens

| Classe          | MT para  | MT aceita        |
|-----------------|----------|------------------|
| Decidível       | Sempre   | Sse $w \in L$    |
| Reconhecível    | Às vezes | Sse $w \in L$    |
| co-Reconhecível | Às vezes | Sse $w \notin L$ |
## Fatos Importantes

- Decidível  $\subset$  Reconhecível  $\subset$  Todas
- Reconhecível  $\neq$  co-Reconhecível
- Decidível  $=$  Reconhecível  $\cap$  co-Reconhecível
- Existem linguagens que não são reconhecíveis nem co-reconhecíveis

{28}------------------------------------------------
### Exercício 1: Rastreamento de Configurações

Considere a MT com  $Q = \{q_0, q_1, q_{acc}, q_{rej}\}$ ,  $\Sigma = \{a, b\}$ ,  $\Gamma = \{a, b, \sqcup\}$  e transições:

- $\delta(q_0, a) = (q_0, a, R)$
- $\delta(q_0, b) = (q_1, b, R)$
- $\delta(q_0, \sqcup) = (q_{rej}, \sqcup, R)$
- $\delta(q_1, a) = (q_{rej}, a, R)$
- $\delta(q_1, b) = (q_1, b, R)$
- $\delta(q_1, \sqcup) = (q_{acc}, \sqcup, R)$

- 1 Trace a execução para as entradas:  $aabb$ ,  $abab$ ,  $aaaa$
- 2 Que linguagem esta MT reconhece?
- 3 Esta MT é um decisor? Justifique.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a central star, flanked by two vertical banners with the letters 'M' and 'P'. Above the shield is a crown and two crossed keys. Below the shield is a ribbon with the Latin motto 'VERVM DVCT'.

Coat of arms of the University of São Paulo (USP)

{29}------------------------------------------------
### Exercício 2: Projeto de MTs

Projete Máquinas de Turing (descrição de alto nível ou diagrama) para:

- 1  $L = \{w \in \{a, b\}^* : |w|_a = |w|_b\}$
- 2  $L = \{a^n b^{2n} : n \geq 0\}$
- 3  $L = \{w\#w : w \in \{0, 1\}^*\}$  (verificar se duas cadeias são iguais)
- 4  $L = \{1^n : n \text{ é potência de } 2\}$

Para cada uma, indique se sua MT é um decisor.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a large five-pointed star in the center. The shield is flanked by two crossed flags. Above the shield is a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{30}------------------------------------------------
### Exercício 3: Operações com MTs

- 1 Dadas MTs  $M_1$  e  $M_2$  que reconhecem  $L_1$  e  $L_2$ , descreva como construir uma MT para  $L_1 \cup L_2$ .
- 2 Mostre que se  $M_1$  e  $M_2$  são decisores, então a MT para  $L_1 \cup L_2$  também é decisor.
- 3 Dada MT  $M$  que reconhece  $L$ , como construir MT para  $L^*$ ?
- 4 Por que é difícil construir MT para  $\bar{L}$  a partir de  $M$ ?

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a white field containing a pattern of green pine trees. A large green star is positioned at the bottom center of the shield. Above the shield is a crest depicting a figure holding a staff. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{31}------------------------------------------------
### Exercício 4: Reconhecibilidade e Decidibilidade

Classifique cada afirmação como Verdadeira ou Falsa. Justifique.

- 1** Toda linguagem finita é decidível.
- 2** Se  $L$  é decidível, então  $L$  é reconhecível.
- 3** Se  $L$  é reconhecível, então  $L$  é decidível.
- 4** Se  $L$  e  $\bar{L}$  são reconhecíveis, então  $L$  é decidível.
- 5** Se  $L$  não é reconhecível, então  $\bar{L}$  é reconhecível.
- 6** Existe uma linguagem que não é reconhecível nem co-reconhecível.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a large five-pointed star in the center. The shield is flanked by two crossed keys (the keys of St. Peter). Above the shield is a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{32}------------------------------------------------
### Exercício 5: Enumeradores

- 1 Descreva um enumerador para  $L = \{a^n b^n : n \geq 0\}$ .
- 2 Prove que se  $L$  é infinita e decidível, então  $L$  pode ser enumerada em ordem lexicográfica.
- 3 Prove que se  $L$  pode ser enumerada em ordem lexicográfica (sem repetições), então  $L$  é decidível.

**Dica:** Compare a entrada com os elementos enumerados.

The image shows the coat of arms of the University of São Paulo (USP). It features a shield with a large five-pointed star in the center. The shield is flanked by two crossed flags. Above the shield is a crown. A banner at the bottom of the shield contains the Latin motto "AD VERVM DVCT".

Coat of arms of the University of São Paulo (USP)

{33}------------------------------------------------
### Desafio: MT para Multiplicação

Projete uma Máquina de Turing que computa a multiplicação de dois números em unário.
### Especificação

- Entrada:  $1^m \# 1^n$  (representando  $m$  e  $n$ )
- Saída:  $1^{m \times n}$  na fita

- 1 Descreva o algoritmo de alto nível.
- 2 Quantos estados sua MT precisa aproximadamente?
- 3 Qual a complexidade de tempo (número de passos) em função de  $m$  e  $n$ ?

**Dica:** Use a definição  $m \times n = \underbrace{n + n + \dots + n}_{m \text{ vezes}}$ .

{34}------------------------------------------------
## Referências I

- [1] Sanjeev Arora e Boaz Barak. *Computational Complexity: A Modern Approach*. Cambridge University Press, 2009.
- [2] John E. Hopcroft, Rajeev Motwani e Jeffrey D. Ullman. *Introduction to Automata Theory, Languages, and Computation*. 3rd. Pearson, 2006.
- [3] Christos H. Papadimitriou. *Computational Complexity*. Addison-Wesley, 1994.
- [4] Michael Sipser. *Introduction to the Theory of Computation*. 3rd. Cengage Learning, 2012.

Faint watermark of a university crest or seal, featuring a shield with a cross and a banner below it reading 'AD VERVM DVCIT'.

<!-- IMAGE_DESCRIPTION: datalab-474827f04e18dc4a3b073e8785813a76_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Faint watermark of a university crest or seal, featuring a shield with a cross and a banner below it reading 'AD VERVM DVCIT'.
<!-- /IMAGE_DESCRIPTION -->

<!-- IMAGE_DESCRIPTION_ORPHANS -->
## Imagens Curadas

Descrições preservadas para imagens detectadas no documento, mas sem referência markdown compatível no corpo principal.

<!-- IMAGE_DESCRIPTION: datalab-1d7527f4316cfe2d342b08d1653d1592_img.jpg -->
<!-- Tipo: generico -->
> **[Descrição de imagem]** Logo of Escola Politécnica da PUCRS
<!-- /IMAGE_DESCRIPTION -->
<!-- /IMAGE_DESCRIPTION_ORPHANS -->
