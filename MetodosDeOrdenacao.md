# Métodos de Ordenação
## _O que são e para que servem?_

_Algoritmos de ordenação são algoritmos que organizam determinado conjunto de dados em ordem crescente ou decrescente baseado em seu valor. Nesse sentido, a entrada é uma lista desorganizada e a saída é uma lista organizada de acordo com a ordenação desejada. 
São importantes pois determinados algoritmos exigem uma determinada ordenação para poderem ser executados._

## Bubble Sort

- Simples
-   Estável


Resumidamente, o Bubble Sort faz a ordenação através da comparação entre pares de elementos, isto é, ele percorre a lista diversas vezes do seu início ao fim comparando dois números a cada vez. Supondo que deseja-se obter uma ordenação crescente de dados, ele avalia se o primeiro elemento é maior ou menor que o segundo. Se for maior, ele os troca de lugar, de modo que o maior sempre fique à direita. Se for descrescente, ele faz o contrário. Assim o algoritmo se repete até que a lista esteja toda ordenada;

> for (j = 0; j < n; j++) {
>     for (i = 0; i < n-1; i++) {
>         if (lista[i] > lista[i + 1]) {
>             aux = lista[i];
>             lista[i] = lista[i + 1];
>	  lista[i + 1] = aux;
 > }}}
 
-  Nesse algoritmo, **j** representa a variável a ser utilizada para contar quantidade de vezes  que a lista será lida, enquanto **i** refere-se à posição de determinado elemento na lista e **n**, à quantidade de termos da lista. Então, **até que a quantidade de vezes que a lista deve ser lida, e até que todos os elementos sejam verificados, verifique se o primeiro elemento é maior que o segundo. Se for, os troque de lugar.**

- **Exemplo:**  
    Considere a lista: 5, 4, 3, 2, 1
    -  **O algoritmo inicia ->**
    - 4, 5, 3, 2, 1 -> 4 > 5? F - Não troca; 5 > 3? V - Troca;
    - 4, 3, 5, 2, 1 -> 5 > 2? V - Troca; 
    - 4, 3, 2, 5, 1 -> 5 > 1? V - Troca; 
    - 4, 3, 2, 1, 5 -> 4 > 3? V - Troca; 
    - 3, 4, 2, 1, 5 -> 4 > 2? V - Troca;
    - 3, 2, 4, 1, 5 -> 4 > 1? V - Troca; 
    - 3, 2, 1, 4, 5 -> 4 > 5? F -Não troca; Repete do início; 3 > 2? V - Troca
    - 2, 3, 1, 4, 5 -> 3 > 1? V - Troca; 
    - 2, 1, 3, 4, 5 -> 3 > 4? F - Não Troca; Repete do início; 2 > 1? V - Troca
    - 1, 2, 3, 4, 5 -> Leitura completa com todas as verificações realizadas com sucesso = Ordem completa;
    - //LISTA ORDENADA COM SUCESSO
    - **O algoritmo termina;**

## Insertion Sort

- É o método a ser utilizado quando o arquivo está “quase”
ordenado.
- É um bom método quando se deseja adicionar uns poucos
itens a um arquivo ordenado, pois o custo é linear.
- É estável.

O Insertion Sort, em resumo, executa uma leitura dos elementos da esquerda para a direita comparando-os percorrendo toda a lista. A ideia é que: a medida que vai lendo, vai substituindo os elementos de modo que os menores valores fiquem à esquerda.

> for (j = 1; j < n; j++)
> { aux = lista[j];
>       for (i = j - 1; (i >= 0) && (lista[i] > aux); i--) 
>       { lista[i + 1] = lista[i];}
>   lista[i + 1] = aux; 
> }

- Exemplo
    Considere a lista: 5, 4, 3, 2, 1
    - **O algoritmo inicia ->** 
    - 4, 5, 3, 2, 1
    - 4, 3, 5, 2, 1
    - 3, 4, 5, 2, 1 //aqui ele vai retirar o 2, trazer os números da esquerda para cobrir seu lugar e colocar o 2 na primeira posição.
    - 2, 3, 4, 5, 1
    - //A mesma coisa para o número 1 agora.
    - 1, 2, 3, 4, 5
    - //LISTA ORDENADA COM SUCESSO
    - **O algoritmo termina;**

## Selection Sort

- Custo Linear de entrada para o movimento de registros
- Utilizado para registros de arquivos muito grandes
- É interessante para listas pequenas
- É instável

Esse algoritmo tem como base a ideia de passar o menor valor para a primeira posição (ou o maior, dependendo se é crescente ou decrescente), o segundo menor para a segunda e assim até que a lista esteja completamente ordenada. Para isso, ele inicia baseando-se por posição. Ele avalia o valor na primeira posição e verifica se à sua direita há algum valor menor. Se houver, ele os substitui. Depois vai para a posição seguinte e assim por diante até que a lista esteja toda ordenada.

> for (i = 0; i < n-1; i++) { 
> // antes de comparar, considera-se como menor o valor no índice // atual  do     loop, ou seja, o valor inserido
> // no índice que o loop está.
> menor = lista[i];
> indiceMenor = i; 
> // compara com os outros valores da lista 
> for (j = i + 1; j < n; j++) { 
> if (lista[j] < menor) { 
> menor = lista[j]; 
> indiceMenor = j; 
> } 
> }
> // realiza a troca dos valores
> lista[indiceMenor] = lista[i];
> lista[i] = menor;
> }

- Exemplo 
    - Considere a lista: 5, 4, 3, 2, 1
    - **O algoritmo inicia ->**
    - //O algoritmo procura o menor número a partir da primeira posição e faz //uma substituição dos valores
    - 1, 4, 3, 2, 5 
    - //repete o passo anterior, mas agora a partir da segunda posição.
    - 1, 2, 3, 4, 5    
    - //Nesse caso, a ordenação fica correta com apenas duas trocas;
    - **O algoritmo termina;**

## Quick Sort
- É o mais eficiente quando se trata de tempo de execução em listas grandes;
- Quanto maior a lista, maior a diferença de tempo de execução entre quick e os demais sorts;

O funcionamento do Quick Sort baseia-se em uma rotina fundamental cujo nome é particionamento. Particionar significa escolher um número qualquer presente no array, chamado de pivot, e colocá-lo em uma posição tal que todos os elementos à esquerda são menores ou iguais e todos os elementos à direita são maiores. Desse modo, ao final de sua execução, é possível obter uma lista ordenada corretamente. 

> void quickSort(int inicio, int fim) { 
> if (inicio < fim) { 
>                     	int indicePivo = separar(inicio, fim);
>                     	quickSort(inicio, indicePivo - 1); 
> quickSort(indicePivo + 1, fim); 
> }
>   }
> int separar(int inicio, int fim) {
> int pivo = lista[inicio]; 
> int i = inicio + 1, f = fim; 
> while (i <= f) {
> 	if (lista[i] <= pivo) 
> i++; 
> else if (pivo < lista[f]) 
> f--; 
> else { 
> int troca = lista[i]; 
> 		lista[i] = lista[f];
> lista[f] = troca; 
> i++; 
> f--; 
> } }
> lista[inicio] = lista[f];
> lista[f] = pivo;
> return f;
> }

- Exemplo:
    - Considere a lista: 5, 4, 3, 2, 1:
    - **O algoritmo inicia ->** 
    - //PRIMEIRO ESCOLHE ALGUM PIVÔ
    - 5, 4, 3, 2, 1
    - //Verifica os números à esquerda do pivô. Eles devem ser menores que
    - //o pivô. Caso não sejam, o pivô é movido para uma posição em que //todos os números da esquerda sejam iguais ou menores e os da direita //maiores.
    - 3, 5, 4, 2, 1
    - //Escolhe outro pivô
    - 3, 5, 4, 2, 1
    - //Repete o processo
    - 2, 3, 5, 4, 1
    - //Escolhe outro pivô
    - 2, 3, 5, 4, 1
    - 2, 3, 4, 1, 5
    - //E outro
    - 2, 3, 4, 1, 5
    - 1, 2, 3, 4, 5
    - //LISTA ORDENADA COM SUCESSO
    - **O algoritmo termina;**

## Mas e aí? Qual o melhor método?

#### _Análise 1 - Lista com 10000 elementos ordenada de maneira crescente_;

 Algoritmo | Tempo(ms) | Comparações |	Movimentações
| --- | --- | --- | --- |
Bubble sort |	934,5364	| 50005000 |	0
Selection Sort |	508,5891 |	49995000 |	29997
Insertion sort |	0,3558 |	9999 |	19998
Quick sort |	2,0824 |	125439 |	17712

#### _Análise 2 - Lista com 10000 elementos ordenada de maneira decrescente_;

Algoritmo |	Tempo(ms) |	Comparações |	Movimentações
---|---|---|---|
Bubble sort |	1838,0272 |	50005000 |	149985000
Selection Sort |	665,2050 |	49995000 |	29997
Insertion sort |	1074,1171 |	9999 |	50014998
Quick sort |	2,1279 |	125452 |	32712

#### _Análise 3 - Lista com 10000 elementos completamente desordenada_;

Algoritmo |	Tempo(ms) |	Comparações |	Movimentações
---|---|---|---
Bubble sort |	1455,9734 |	50005000 |	74237889
Selection Sort |	545,1068 |	49995000 |	29997
Insertion sort |	539,6891 |	9999 |	24765961
Quick sort |	4,5072 |	176065 |	103635

- O Bubble Sort é o algoritmo mais ineficiente devido ao seu tempo de resposta. Ele é o algoritmo mais simples de ser implementado, mas sua simplicidade não compensa sua ineficiência, seja em casos ordenados, ou desordenados; 
- O Insertion Sort se mostrou muito eficiente no primeiro caso, em que a lista já está ordenada. Seu tempo de execução foi o mais rápido e suas comparações foram as menores, comprovando que é um excelente método para casos em que há necessidade de inserir um novo elemento na lista;
- O Selection Sort se deu menor número de movimentações na segunda análise, em listas ordenadas de maneira decrescente;
- O Quick Sort é, sem dúvidas, o algoritmo mais eficiente em casos em que a lista possui muitos elementos e está desordenada ou organizada da maneira oposta a que se deseja;




