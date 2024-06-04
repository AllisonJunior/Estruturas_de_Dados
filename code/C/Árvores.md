# Árvores

Para se implementar uma <a href="Árvores.md" title="elementos organizados não sequêncialmente mais sim em ramos">**árvore binária**</a>, utilizamos a ideia de <a href="Árvores.md" title="Vulgo Node">ramos</a>, onde cada ramo tem no máximo dois ramos e cada ramo tem um valor, ou um dado e referência para os próximos ramos do atual. Por isso aqui está disponibilizada uma implementação simples com algumas funções de ajuda.

--- 

# Árvore Binária
```main.c
# include <stdio.h>
# include <stdlib.h>



// Aqui temos um TAD base de uma árvore binária
// ele contem um valor do tipo inteiro, e dois
// ponteiros para referênciar outros Nodes (vulgo ramos)
// da nossa árvore
typedef struct Node 
{
       int valor;
       struct Node * esquerda;
       struct Node * direita;
} 
Node;

// Função *auxiliar* para criar um Node, com base na função 'insert_Node' 
Node * create_Node ( int valor ) 
{
    Node * new_Node = ( Node * ) malloc ( sizeof ( Node ) );
    if ( !new_Node ) { printf ( "\n- Erro ao alocar memória.\n" ); exit ( EXIT_FAILURE ); }

    new_Node -> valor = valor;
    new_Node -> esquerda = new_Node -> direita = NULL;
    
    return new_Node;
}

// Função para inserir um novo nó na árvore binária
Node * insert_Node ( Node * ramo , int valor ) 
{
    if ( NULL == ramo )               ramo = create_Node ( valor );
    else if ( valor < ramo -> valor ) ramo -> esquerda = insert_Node ( ramo -> esquerda , valor );
    else                              ramo -> direita = insert_Node ( ramo -> direita , valor );
    
    return ramo;
}

// Função para buscar um valor dentro da árvore binária
Node * search_Node ( Node * ramo , int valor ) 
{
    if ( ( ramo == NULL ) || ( ramo -> valor  == valor ) ) return ramo;
    
    if ( valor < ramo -> valor ) return search_Node ( ramo -> esquerda , valor );
    
    return search_Node ( ramo -> direita , valor );
}

// Função *auxiliar* para encontrar o nó com o valor mínimo
Node * findMin_Node ( Node * ramo ) 
{
    while ( ramo -> esquerda != NULL ) ramo = ramo -> esquerda;
    return ramo;
}

// Função para remover um nó da árvore binária
Node * delete_Node ( Node * ramo , int valor ) 
{
    if ( NULL == ramo ) return ramo;

    if ( valor < ramo -> valor )      ramo -> esquerda = delete_Node ( ramo -> esquerda , valor );
    else if ( valor > ramo -> valor ) ramo -> direita = delete_Node ( ramo -> direita , valor );
    else 
    {
        // Aqui o nó foi encontrado
        if ( NULL == ramo -> esquerda ) 
        {
          Node * temp = ramo -> direita;
          free ( ramo );
          return temp;
        } 
        else if ( NULL == ramo -> direita ) 
        {
            Node * temp = ramo -> esquerda;
            free ( ramo );
            return temp;
        }

        // Nó com dois filhos
        Node * temp = findMin_Node ( ramo -> direita );
        ramo -> valor = temp -> valor;
        ramo -> direita = delete_Node ( ramo -> direita , temp -> valor );
    }

    return ramo;
}

// Função para percorrer a árvore em 'ordem'
void printInOrder_Tree ( Node * ramo ) 
{
    if ( NULL != ramo ) 
    {
      printInOrder_Tree ( ramo -> esquerda );
      printf ( "%d " , ramo -> valor );
      printInOrder_Tree ( ramo -> direita );
    }
}

// Função para percorrer a árvore em 'pré-ordem'
void printInPreOrder_Tree ( Node * ramo ) 
{
    if ( NULL != ramo ) 
    {
      printf ( "%d " , ramo -> valor );
      printInPreOrder_Tree ( ramo -> esquerda );
      printInPreOrder_Tree ( ramo -> direita );
    }
}

// Função para percorrer a árvore em 'pós-ordem'
void printInPostOrder_Tree ( Node * ramo ) 
{
    if ( NULL != ramo ) 
    {
      printInPostOrder_Tree ( ramo -> esquerda );
      printInPostOrder_Tree ( ramo -> direita );
      printf ( "%d " , ramo -> valor );
    }
}

// Função para liberar a memória da árvore binária
void free_Tree ( Node * ramo ) 
{
    if ( NULL != ramo ) 
    {
      free_Tree ( ramo -> esquerda );
      free_Tree ( ramo -> direita );
      free ( ramo );
    }
}

int main ( void ) 
{
   // Criando a nossa árvore ( Como Node ou seja, o início ) 
   Node * tree = NULL;

   // Fazendo algumas inserções de Nodes na árvore
   tree = insert_Node ( tree , 50 );
   tree = insert_Node ( tree , 30 );
   tree = insert_Node ( tree , 20 );
   tree = insert_Node ( tree , 40 );
   tree = insert_Node ( tree , 70 );
   tree = insert_Node ( tree , 60 );
   tree = insert_Node ( tree , 80 );

   // Agora podemos percorrer nossa árvore em ordem
   printf ( "- Percurso em ordem: " );
   printInOrder_Tree ( tree );
   printf ( "\n" );

   // Agora removeremos alguns nós, e checamos como fica
   // a organizaç~çao da árvore
   tree = delete_Node ( tree , 20 );

   printf ( "\n- Percurso em ordem após remover o valor {20}: " );
   printInOrder_Tree ( tree );
   printf ( "\n" );

   tree = delete_Node ( tree , 30 );

   printf ( "\n- Percurso em ordem após remover o valor {30}: " );
   printInOrder_Tree ( tree );
   printf ( "\n" );

   tree = delete_Node ( tree , 50 );

   printf ( "\n- Percurso em ordem após remover o valor {50}: " );
   printInOrder_Tree ( tree );
   printf ( "\n" );

   // Após testarmos nossa árvore podemos liberar a memória da árvore
   free_Tree ( tree );
}
```

<h3 align="center"> <a href="#árvores" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

