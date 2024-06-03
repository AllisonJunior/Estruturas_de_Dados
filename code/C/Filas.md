# Filas

A linguagem de programação C não possui uma forma padrão de se implementar <a href="Filas.md" title="uma coleção linear de elementos similar a uma pilha">**Filas**</a>, que também seguem o princípio de <a href="Filas.md" title="Last In, First Out: o último elemento inserido é o primeiro a ser removido.">**LIFO**</a>, por isso utilizamos um <a href="Filas.md" title="Tipo Abstrato de Dado: Struct">**TAD**</a> para chegar a esse resultado. As filas podem ser implementadas tanto como um modelo de implementação estática como um modelo de implementação na forma dinâmica. Portanto abaixo estarão disponibilizadas as duas possíveis implementações:

--- 

# Fila Estática
```main.c
// Constantes
# define QUEUE_SIZE 10

# include <stdio.h>



// Aqui temos uma estrutura base para
// referênciar uma fila, a mesma contém
// um vetor e 2 índices de referência de
// índice.
typedef struct 
{
       int valor [ QUEUE_SIZE ];
       int frente, final;
} 
Fila;

// Função para inicializar o TAD 'fila'
void init_Fila ( Fila * ref ) 
{
    ref -> frente = -1;
    ref -> final  = -1;
}

// Função para inicializar o TAD 'fila' com return
Fila new_Fila ( void )
{
    Fila queue;

    queue . frente = -1;
    queue . final  = -1;

    return queue;
}

// Função para checar se a fila está vazia
int isEmpty ( Fila * ref ) { return ( ref -> frente  == -1 && ref -> final  == -1 ); }

// Função para checar se a fila está cheia
int isFull ( Fila * ref ) { return ( ( ref -> final + 1 ) % QUEUE_SIZE == ref -> frente ); }

// Função para inserir na fila
void enqueue ( Fila * ref , int valor ) 
{
    if ( isFull ( ref ) )  { printf ( "Queue is full.\n" ); return; }
    if ( isEmpty ( ref ) ) { ref -> frente = 0; ref -> final = 0; } 
    else                     ref -> final  = ( ref -> final + 1 ) % QUEUE_SIZE;
    
    ref -> valor [ ref -> final ] = valor;
}

// Função para remover da fila  
int dequeue ( Fila  * ref ) 
{
    int valor = 0;

    if ( isEmpty ( ref ) ) { printf ( "Queue is empty.\n" ); return -1; }

    valor = ref -> valor [ ref -> frente ];

    if ( ref -> frente == ref -> final ) { ref -> frente = -1; ref -> final = -1; } 
    else                                   ref -> frente = ( ref -> frente + 1 ) % QUEUE_SIZE;
    
    return valor;
}

// Função para printar toda a fila
void printQueue ( Fila * ref ) 
{
    if ( isEmpty ( ref ) ) { printf ( "Queue is empty.\n" ); return; }
    
    printf ( "- Fila: ");

    for ( int i = ref -> frente ; i != ref -> final ; i = ( i + 1 ) % QUEUE_SIZE ) 
       printf ( "%d " , ref -> valor [ i ] );

    printf ( "%d\n" , ref -> valor [ ref -> final ] );
}

int main ( void ) 
{
   // Criando nossa fila com todos os campos zerados por isso '= { 0 }'
   Fila queue = { 0 };

   // Fazendo a inicialização da nossa fila 
   init_Fila ( &queue );

   // Fazendo um teste de adição de valores e por fim printando ela
   enqueue ( &queue , 10 );
   enqueue ( &queue , 20 );
   enqueue ( &queue , 30 );
   enqueue ( &queue , 40 );
   enqueue ( &queue , 50 );
   enqueue ( &queue , 60 );
   printQueue ( &queue );

   // Fazendo algumas remoções e printando a fila novamente
   printf ("\n- Removido: %d\n", dequeue ( &queue ) );
   printf ("- Removido: %d\n\n",   dequeue ( &queue ) );
   printQueue ( &queue );
}
```

# Fila Dinâmica
```main.c
# include <stdio.h>
# include <stdlib.h>



// Aqui temos um TAD que referência um
// Nó de uma Fila, ou seja, a fila será
// composta inteiramente desse TAD abaixo
// o mesmo contém, um ponteiro para um dado
// próximo de mesmo tipo e um valor comum
// nesse caso usaremos um inteiro
typedef struct Node 
{
       int valor;
       struct Node * proximo;
} 
Node;

// Aqui temos a nosso TAD de fila dinâmica, que 
// consiste em 2 ponteiros, um que referência a 
// frente e outro o final, para simularmos o efeito
// de quem estiver na frente sair primeiro
typedef struct { Node * frente , * final; } Fila;

// Função para inicializar uma fila atráves de referência
void initQueue ( Fila * ref ) { ref -> frente = NULL; ref -> final = NULL; }

// Função para checar se a fila está vazia
int isEmpty ( Fila  * ref ) { return ( ref -> frente == NULL ); }

// Função para enfileirar um valor
void enqueue ( Fila * ref , int valor_novo ) 
{
    Node * new_Node = ( Node * ) malloc ( sizeof ( Node ) );
    if ( NULL == new_Node ) { printf ( "\n- Alocação de memória para o Node falhou!.\n" ); return; }
    
    new_Node -> valor = valor_novo;
    new_Node -> proximo = NULL;
    
    if ( isEmpty ( ref ) ) { ref -> frente = new_Node; ref -> final = new_Node; }
    else                   { ref -> final -> proximo = new_Node; ref -> final = new_Node; }
}

// Função para desinfileirar o valor da frente da fila
int dequeue ( Fila * ref ) 
{
    if ( isEmpty ( ref ) ) { printf ("\n- A Fila está vazia!\n"); return -1; }
    
    int valor = ref -> frente -> valor;
    Node * temporario = ref -> frente;
    
    ref -> frente = ref -> frente -> proximo;
    if ( NULL == ref -> frente ) ref -> final = NULL;
    
    free ( temporario );
    
    return valor;
}

// Função para printar a fila
void printQueue ( Fila * ref ) 
{
    if ( isEmpty ( ref ) ) { printf ( "\n- A fila está vazia.\n" ); return; }
    
    printf ( "- Fila: " );

    Node * atual = ref -> frente;

    while ( atual != NULL ) 
    {
         printf ( "%d ", atual -> valor );
         atual = atual -> proximo;
    }

    printf ( "\n" );
}

int main ( void ) 
{
    // Criamos o TAD fila e em seguida o inicializamos
    Fila queue;
    initQueue ( &queue );

    // Agora fazemos algumas inserções para testarmos se está tudo ok
    enqueue ( &queue , 10 );
    enqueue ( &queue , 20 );
    enqueue ( &queue , 30 );
    enqueue ( &queue , 40 );
    enqueue ( &queue , 50 );
    printQueue ( &queue );
    
    // Por fim vamos remover alguns elementos e ver como ficou a fila
    printf ( "\n- Removido: %d\n", dequeue ( &queue ) );
    printf ( "- Removido: %d\n\n", dequeue ( &queue ) );
    printQueue ( &queue );
}
```

<h3 align="center"> <a href="#filas" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

