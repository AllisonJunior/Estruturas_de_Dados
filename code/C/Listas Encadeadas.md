# Listas Encadeadas

A linguagem de programação C não possui uma forma padrão de se implementar <a href="Listas Encadeadas.md" title="sequência de nós">**listas encadeadas**</a>, com isso utilizamos um <a href="Listas Encadeadas.md" title="Tipo Abstrato de Dado: Struct">**TAD**</a> para chegar a esse resultado sempre na forma dinâmica. A lista pode ser encadeada ou duplamente encadeada, a diferença se resume ao uso de um <a href="Listas Encadeadas.md" title="Ponteiro para um dado similar"> **Node** </a> ou mais, onde no caso da encadeada padrão, só temos o valor e o ponteiro para o próximo dado e já na duplamente encadeada temos um ponteiro para o dado anterior e o próximo.

--- 

# Lista Encadeada
```main.c
# include <stdio.h>
# include <stdlib.h>



// Aqui temos um TAD 'Node' que em resumo
// funciona como um elemento de uma sequência
// ou seja, a nossa lista será composta desse TAD
// Ele contém um valor e um ponteiro para um próximo
// Node assim seguindo 
typedef struct Node 
{
       char valor;
       struct Node * proximo;
} 
Node;

// Aqui temos o TAD da nossa lista que terá um ponteiro
// para referênciar nodes e assim termos uma sequência de
// elementos para poder acessar 
typedef struct { Node * frente; } Lista;

// Função para fazer a inicialização da lista com referência
void init_Lista ( Lista * ref ) { ref -> frente = NULL; }

// Função para adicionar um elemento na frente da lista
void append ( Lista * ref , char valor ) 
{
    Node * new_Node = ( Node * ) malloc ( sizeof ( Node ) );
    if ( new_Node == NULL ) { printf ( "\n- Alocação de memória falhou!\n" ); return; }
   
    new_Node -> valor = valor;
    new_Node -> proximo = NULL;

    if ( ref -> frente == NULL ) ref -> frente = new_Node;
    else 
    {
        Node * current = ref -> frente;
        
        while ( current -> proximo != NULL ) 
             current = current -> proximo;
        
        current -> proximo = new_Node;
    }
}

// Função para remover o último elemento
void removeLast ( Lista * ref ) 
{
    if ( ref -> frente == NULL ) { printf ( "\n- A lista está vazia!\n"); return; }
    
    Node * current = ref -> frente;
    Node * prev = NULL;
    
    while ( current -> proximo != NULL ) 
    {
          prev = current;
          current = current -> proximo;
    }
    
    if ( prev == NULL ) { free ( current ); ref -> frente = NULL; } 
    else                { prev -> proximo = NULL; free ( current ); }
}

// Função para remover o primeiro elemento
void removeFirst ( Lista * ref ) 
{
    if ( ref -> frente == NULL ) { printf ( "\n- A lista está vazia!\n"); return; }

    Node * temp = ref -> frente;
    ref -> frente = ref -> frente -> proximo;

    free ( temp );
}


// Função para remover com base em um parâmetro
void removeIt ( Lista * ref , char value ) 
{
    Node * current = ref -> frente;
    Node * prev = NULL;

    while ( current != NULL && current -> valor != value ) 
    {
         prev = current;
         current = current -> proximo;
    }

    if ( current == NULL ) { printf ( "\n- [%c] Não encontrado na lista!\n" , value ); return; }
    if ( prev == NULL )    { ref -> frente = current -> proximo; }
    else                     prev -> proximo = current -> proximo;
    
    free ( current );
}

// Função para printar a lista
void printList ( Lista * ref ) 
{
    if ( ref -> frente == NULL ) { printf ( "\n- A lista está vazia!\n" ); return; }
    
    printf ( "Lista: ");

    Node * current = ref -> frente;
    
    while ( current != NULL ) 
    {
         printf ( "%c " , current -> valor );
         current = current -> proximo;
    }
    printf ( "\n" );
}


int main ( void ) 
{
   // Criamos nossa lista e a inicializamos
   Lista codes; init_Lista ( &codes );  

   // Agora faremos algumas adições na lista
   append ( &codes , '@' );
   append ( &codes , '!' );
   append ( &codes , '#' );
   append ( &codes , '&' );
   append ( &codes , '$' );
   append ( &codes , '%' );
   printf ( "[ APÓS INSERIR OS VALORES ]\n" );
   printList ( &codes ); // E vemos seu estado atual

   // Agora faremos algumas remoções da lista
   printf ( "\n[ REMOVENDO POR COMPARAÇÃO DE VALOR ]\n" );
   removeIt ( &codes , '&' );
   printList ( &codes );

   printf ( "\n[ REMOVENDO O ÚLTIMO ELEMENTO ]\n" );
   removeLast ( &codes );
   printList ( &codes );
   
   printf ( "\n[ REMOVENDO O PRIMEIRO ELEMENTO ]\n" );
   removeFirst ( &codes );
   printList ( &codes ); // E vemos seu estado atual
}
```

# Lista Duplamente Encadeada
```main.c
```

<h3 align="center"> <a href="#listas-encadeadas" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

