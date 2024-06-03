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
```

<h3 align="center"> <a href="#filas" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

