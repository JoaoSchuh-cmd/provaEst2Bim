# Árvore Balanceada
## _O que é e para que serve?_

Árvore binária é um conceito aplicado em estrutura de dados cujo objetivo é facilitar verificações complexas ou tomadas de decisões. Por exemplo: suponhamos que deseja-se procurar por um determinado número dentro de uma lista desordenada que contém vários números. O jeito mais aparente de se fazer seria por verificações comparando o número que se está verificando com o número que se deseja ser encontrado até que ele seja encontrado. Segue abaixo:
[3, 1, 4, 15, 12, 8, 6, 5, 10, 14, 2, 11, 13]
Nesse exemplo, supondo que se deseja encontrar o número 13, seriam necessárias 13 verificações até que ele fosse encontrado. 
A árvore binária auxilia nesse sentido, uma vez que possui como fator, subdividir determinada busca em outras menores.

No mesmo exemplo, a busca seria reduzida a apenas 4 verificações. Ela segue uma propriedade muito importante para que isso ocorra: Ela é baseada em nós, sendo que cada nó é a raíz de outras subárvores. Em cada nó, as subárvores à sua esquerda possuem números menores que ele mesmo e à direita, números maiores. Baseado nessa propriedade, o algoritmo é o seguinte:

## Algoritmo árvore binária

> public void inserir(No node, int valor) {
  //verifica se a árvore já foi criada
   if (node != null) {
    //Verifica se o valor a ser inserido é menor que o nodo corrente da árvore, se sim vai para subárvore esquerda
    if (valor < node.valor) {
        //Se tiver elemento no nodo esquerdo continua a busca
        if (node.esquerda != null) {
            inserir(node.esquerda, valor);
        } else {
            //Se nodo esquerdo vazio insere o novo nodo aqui
            System.out.println("  Inserindo " + valor + " a esquerda de " + node.valor);
            node.esquerda = new No(valor);
        }
    //Verifica se o valor a ser inserido é maior que o nodo corrente da árvore, se sim vai para subárvore direita
    } else if (valor > node.valor) {
        //Se tiver elemento no nodo direito continua a busca
        if (node.direita != null) {
            inserir(node.direita, valor);
        } else {
            //Se nodo direito vazio insere o novo nodo aqui
            System.out.println("  Inserindo " + valor + " a direita de " + node.valor);
            node.direita = new No(valor);
        }
    }
  }
}

## Árvore Binária Balanceada
A árvore binária balanceada é como uma determinante para polir ainda mais a busca por árvores binárias. Ela garante que a altura das subárvores sejam iguais ou no máximo + 1 ou - 1 de diferença, sendo assim, a busca é muito mais polida. Há vários tipos de árvores balanceadas como: AVL, Rubro-Negra, 2-3, SpaceGoat e por ai vai. Todas elas têm o mesmo objetivo: mantar as subdivisões da árvore com a mesma altura para equilibra-la e facilitar as buscas. Vejamos a seguir um algoritmo de funcionamento da árvore AVL.

## Algoritmo AVL
>// O método de procura numa AVL é semelhante ao busca binária de uma árvore binária de busca comum.
public BSTNode<T> search(T element) {
    return search(element, this.root);
}

>// Método auxiliar à recursão.
private BSTNode<T> search(T element, BSTNode<T> node) {
    if (element == null || node.isEmpty()) {
        return new BSTNode<T>();
    }
    
   > if (node.isEmpty() || node.getData().equals(element)) {
        return node;
    } else if (node.getData().compareTo(element) > 0) {
        return search(element, node.getLeft());
    } else {
        return search(element, node.getRight());
    }
}

## Principal diferença em tempo de execução

O tempo de execução de uma busca em árvores binárias é diretamente proporcional a altura de seus nós, logo, quanto maior for a altura de um nó, mais tempo é gasto até que se encontre determinado elemento dentro dela. Isso é logicamente explicado uma vez que o objetivo de uma árvore binária é justamente quebrar uma sequência de verificações em micro verificações guiadas para agilizar o processo. 
Nesse sentido, árvores binárias balanceadas tem uma vantagem um pouco maior, pois não permitem alturas elevadas e ainda padronizam essa altura em todos os nós da árvore. Isso é muito relevante pois permite com que o tempo entre as buscas seja proporcional.

