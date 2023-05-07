Download Link: https://assignmentchef.com/product/solved-ene4014-homework-2
<br>
<strong>Exercise 1 </strong>Write a function

calculate : exp→float

that returns a result of a given arithmetic formula. The exp type is defined as follows:

type exp = X | INT of int

| REAL of float

| ADD of exp * exp

| SUB of exp * exp

| MUL of exp * exp

| DIV of exp * exp

| SIGMA of exp * exp * exp

| INTEGRAL of exp * exp * exp

For example, the following arithmetic formulas can be written in the exp type:

<h1>               SIGMA(INT1<em>,</em>INT10<em>,</em>SUB(MUL(X<em>,</em>X)<em>,</em>INT1))          INTEGRAL(REAL1<em>.</em>0<em>,</em>REAL10<em>.</em>0<em>,</em>SUB(MUL(X<em>,</em>X)<em>,</em>INT1))</h1>

When you compute integrals, <em>dx </em>should be 0.1. <em>2</em>

<strong>Exercise 2 </strong>Write a function

diff : ae∗string→AE

that differentiates the given algebraic expression with respect to the variable given as the second argument. The ae type is defined as follows:

type ae = CONST of int

| VAR of string

| POWER of string * int

| TIMES of ae list

| SUM of ae list

For example, <em>x</em><sup>2 </sup>+ 2<em>x </em>+ 1 is represented by

SUM [POWER (“x”, 2); TIMES [CONST 2; VAR “x”]; CONST 1]

and differentiating it (w.r.t. “<em>x</em>”) gives 2<em>x </em>+ 2, which can be represented by

SUM [TIMES [CONST 2; VAR “x”]; CONST 2]

<strong>Exercise 3 </strong>The following type specifies a set of <em>big integers </em>which can represent positive numbers larger than the 32-bit integer limit (2<sup>32</sup>− 1).

type bigint = BigInt of string

For example, a big integer 1032 is represented as BigInt “1032”.

Write a function compute_bigint : op -&gt; bigint * bigint -&gt; bigint

that returns a resulting big integer for a given arithmetic operation along with two big integers as operands, and the op type is defined as follows:

type op = ADD | MUL

The function should behaves as follows:

compute_bigint ADD ((BigInt ‘‘1032″), (BigInt ‘‘1032″))

= BigInt ‘‘2064″ compute_bigint MUL ((BigInt ‘‘183829184395481829391″), (BigInt ‘‘76187828″))

= BigInt ‘‘14005546282103253594766852748″

<strong>Exercise 4 </strong>Write a function

countstring : string→string→int<em>.</em>

that returns the number of substrings in a given string. count string s x count how many times x is found in s (if x is the empty string “”, 0 is returned.

For instance,

countstring “aaa<sup>00 </sup>“a” = 3

countstring “aaa<sup>00 </sup>“aa” = 2

countstring “abababababa<sup>00 </sup>“aba” = 5

countstring “GeeksforGeeksforGeeksforGeeks<sup>00 </sup>“GeeksforGeeks<sup>00 </sup>= 3

countstring “aaa<sup>00 </sup>“” = 0

Note that the function should give correct results when two occurrences of the substring overlap. You may refer to the OCaml standard API https://ocaml.

org/api/String.html for useful functions for manipulating strings.

<strong>Exercise 5 </strong>Consider the following triangle which is called Pascals triangle:

1

1          1

1          2          1

1          3          3          1

1          4          6          4          1

where the numbers on an edge of the triangle are all 1, and each number inside the triangle is the sum of the two numbers above it.

Write a function

pascal : int * int -&gt; int

that computes an element of Pascals triangle at a location specified by a row and a column (starting from 0). For example, pascal should behave as follows:

pascal (0,0) = 1 pascal (1,0) = 1 pascal (0,0) = 1 pascal (2,1) = 2

pascal (4,2) = 6

<strong>Exercise 6 </strong>The edit distance<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> is a string metric for measuring the difference between two strings. Informally, the edit distance between two strings is the minimum number of single-character edits (insertions, deletions or substitutions) required to change one string into the other. For example, the edit distance between “kitten” and “sitting” is 3, since the following three edits change one into the other, and there is no way to do it with fewer than three edits:

<ol>

 <li>kitten → sitten (substitution of “s” for “k”)</li>

 <li>sitten → sittin (substitution of “i” for “e”)</li>

 <li>sittin → sitting (insertion of “g” at the end).</li>

</ol>

Write a function closest : string -&gt; string list -&gt; string

which takes a string <em>s </em>and a list of string <em>vocab</em>, and returns a string in <em>vocab </em>which is the most similar to <em>s</em>. For example, closest “kitten” [“sitting”; “fighting”; “kicking”] = “sitting”

because the edit distance between “kitten” and “”fighting” is 5 and the distance between “kitten” and “kicking” is 4. In case of tie (i.e., multiple strings of the same edit distance), the leftmost element in the list <em>vocab </em>should be returned.

When computing the edit distance between two strings <em>a </em>and <em>b </em>(denoted <em>dist</em>(<em>a,b</em>), you may refer to the following inductive definition. <em>tail</em>(<em>a</em>) denotes a substring of <em>a </em>without the first character of <em>a </em>(e.g., <em>tail</em>(”<em>abc</em>”) = ”<em>bc</em>”).

<table width="527">

 <tbody>

  <tr>

   <td width="288"><sup></sup> <em>dist</em>(<em>tail</em>(<em>a</em>)<em>,tail</em>(<em>b</em>))<em>dist</em>(<em>a,b</em>) =                           <em>dist</em>(<em>tail</em>(<em>a</em>)<em>,b</em>)<sub></sub><sup></sup><sub> </sub>1 + min<sub> </sub><em>distdist</em>((<em>a,tailtail</em>(<em>a</em><sub>)</sub>(<em>,tailb</em>)) (<em>b</em>))</td>

   <td width="239">(the first characters of <em>a </em>and <em>b </em>are equal)</td>

  </tr>

 </tbody>

</table>

length of <em>a     </em>(<em>b </em>is the empty string) length of <em>b </em>(<em>a </em>is the empty string)

<strong>Exercise 7 </strong>A graph is a structure amounting to a set of nodes in which some pairs of the nodes are related<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>.

We can depict personal relationships by a graph. Suppose person A likes person B, who likes person C. Person C also likes person B. Another person D likes person A. These relations can be represented by the following graph.

Let us suppose this “like” relation is <em>transitive </em>in the sense that if A likes B and B likes C, then A also likes C.

Write a function

likes : relationships -&gt; person -&gt; int

that given a graph of relationships and a person, returns the number of people whom the person likes. The type relationships is for representing a graph of personal relationships, which is defined as follow:

type relationships = (string * string) list

For example, the above graph can be represented as let graph = [(“A”, “B”); (“B”, “C”); (“C”, “B”); (“D”, “A”)]

The function should behave as follows:

likes graph “A” = 2 likes graph “B” = 2 likes graph “C” = 2 likes graph “D” = 3

<strong>Exercise 8 </strong>In the above graph, B likes him/herself for the following reason: B likes C and C likes B, and because the relation is transitive, B also likes B. For a similar reason, C also likes him/herself.

Write a function

selflove : relationships→int

that returns the number of people who like him/herself. For example, given the above graph, selflove graph should return 2.

<a href="#_ftnref1" name="_ftn1"></a>