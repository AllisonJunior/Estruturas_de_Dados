# Pilhas

A linguagem de programação C não possui uma forma padrão de se implementar <a href="Pilhas.md" title="uma coleção linear de elementos vulgo stack">**pilhas**</a>, que seguem o princípio de <a href="Pilhas.md" title="Last In, First Out: o último elemento inserido é o primeiro a ser removido.">**LIFO**</a>, por isso utilizamos um <a href="Pilhas.md" title="Tipo Abstrato de Dado: Struct">**TAD**</a> para chegar a esse resultado, utilizando um modelo de implementação estática ou dinâmica. Portanto abaixo estarão disponibilizadas as duas implementações. 

--- 

<h1 align="center"> Pilha Estática </h1>

```main.c
// Constantes
# define MAX_CAPACITY  4
# define CHEIA         3
# define VAZIA        -1

# include <stdio.h>



// Aqui temos a estrutura base de uma pilha
// estática, que contém um topo e um vetor
// para armazenar os elementos.
typedef struct
{
       int vetor [ MAX_CAPACITY ];
       int topo;
}
Pilha;

// Função de inicialização atrávez de retorno
Pilha init_Pilha ( void )
{
     Pilha pilha;
     pilha . topo = VAZIA;

     return pilha;
}

// Função que inicializa a pilha atrávez de referência
void new_Pilha ( Pilha * pilha ) { pilha -> topo = VAZIA; }

// Função que adiciona um valor qualquer no topo atual da pilha
void push ( Pilha * pilha , int valor )
{
    if ( pilha -> topo == CHEIA )
    {
      printf ( "- A pilha está cheia!\n" );
      return;   
    }

    pilha -> vetor [ ++ pilha -> topo ] = valor;
    printf ( "- Adicionado no índice da pilha %d o valor [ %d ]\n" , pilha -> topo , pilha -> vetor [ pilha -> topo ] );
}

// Função que remove o valor do topo da pilha
void pop ( Pilha * pilha )
{
    if ( pilha -> topo == VAZIA )
    {
      printf ( "- A pilha está vazia!\n" );
      return;  
    }

    printf ( "- Removido do índice %d da pilha o valor [ %d ]\n" , pilha -> topo , pilha -> vetor [ pilha -> topo ] );
    pilha -> vetor [ pilha -> topo ] = -999;
    pilha -> topo --;
}

// Função que printa o vetor
void print ( Pilha * pilha )
{
    printf ( "- [ " );
    for ( int i = 0 ; i < MAX_CAPACITY ; i ++ ) printf ( "%d " , pilha -> vetor [ i ] );
    printf ( "]\n" );
}

int main ( void )
{
   // Criação da pilha e inicialização
   Pilha pilha; new_Pilha ( &pilha );

   // Teste de adição e checagem para ver se está cheia 
   push ( &pilha , 44 );
   push ( &pilha , 55 );
   push ( &pilha , 22 );
   push ( &pilha , 11 );
   push ( &pilha , 99 ); // Aqui o programa deve printar um aviso

   // Printando a pilha
   print ( &pilha );

   // Removendo o valor 11
   pop ( &pilha );

   // Adicionando no lugar vázio o valor 77
   push ( &pilha , 77 );

   // Printando a pilha
   print ( &pilha );
}
```

<h1 align="center"> Pilha Dinâmica </h1>

```main.c
# include <stdio.h>
# include <stdlib.h>



// Definição da estrutura do nó da pilha
typedef struct No
{
       int valor;           // Dado a ser armazenado
       struct No * proximo; // Ponteiro para o próximo nó
}
No;

// Definição da estrutura da pilha com um ponteiro para o topo da pilha 
typedef struct { No * topo; } Pilha;

// Função para criar um novo nó
No * criar_No ( int valor )
{
  // Aloca memória para o novo nó ( vulgo node ) e faz a checagem de invalidação de alocação
  No * novo_Node = ( No * ) malloc ( sizeof ( No ) );  
  if ( NULL == novo_Node ) 
  {
    printf ( "- Não foi possível alocar memória para o nó!\n" );
    exit ( EXIT_FAILURE ); // Encerramos a aplicação por ser um erro grave
  }

  // Prosseguimos com a inicialização
  novo_Node -> valor = valor;  // Define o dado do novo nó
  novo_Node -> proximo = NULL; // Inicializa o próximo como NULL
    
  // Retornamos o nó criado / inicializado
  return novo_Node;
}

// Função para inicializar a pilha
Pilha * criar_Pilha ( void ) 
{
     // Aloca memória para a pilha e checa se deu erro
     Pilha * nova_Pilha = ( Pilha * ) malloc ( sizeof ( Pilha ) );
     if ( NULL == nova_Pilha ) 
     {
       printf ( "- Não foi possível alocar memória para a pilha!\n");
       exit ( EXIT_FAILURE ); // Erro grave, portanto encerra o programa
     }
    
     // Inicializa o topo da pilha como NULL (pilha vazia)
     nova_Pilha -> topo = NULL; 

     // Retorna nossa pilha inicializada
     return nova_Pilha;
}

// Função para verificar se a pilha está vazia - 1 está vazia senão 0
int isEmpty ( Pilha * pilha_referenciada ) { return ( pilha_referenciada -> topo == NULL ); }

// Função para empilhar um elemento na pilha
void push ( Pilha * pilha_referenciada , int valor ) 
{
    // Cria um novo nó com o dado fornecido
    No * novo_Node = criar_No ( valor );  

    // Define o próximo do novo nó como o antigo topo da pilha
    novo_Node -> proximo = pilha_referenciada -> topo; 

    // Define o novo nó como o topo da pilha
    pilha_referenciada -> topo = novo_Node; 
}

// Função para desempilhar um elemento da pilha
int pop ( Pilha * pilha_referenciada ) 
{
   // Checagem para ver se a pilha está cheia  
   if ( isEmpty ( pilha_referenciada ) ) 
   {
     printf ( "- Pilha está vazia, não é possível desempilhar.\n");
     return 0;
   }

   // Armazena o dado do topo da pilha
   int valor = pilha_referenciada -> topo -> valor; 

   // Armazena o topo da pilha em um nó temporário
   No * node_temporario = pilha_referenciada -> topo; 
    
   // Atualiza o topo da pilha para o próximo nó
   pilha_referenciada -> topo = pilha_referenciada -> topo -> proximo; 
    
   // Libera a memória do nó desempilhado
   free ( node_temporario ); 

   // Retorna o dado desempilhado
   return valor; 
}

// Função para visualizar o elemento no topo da pilha
int peek ( Pilha * pilha_referenciada ) 
{   
   // Checagem para ver se a pilha está cheia  
   if ( isEmpty ( pilha_referenciada ) ) 
   {
     printf ( "- Pilha está vazia, não é possível visualizar o elemento do topo!\n");
     return 0;
   }

   // Retorna o dado do topo da pilha
   return pilha_referenciada -> topo -> valor; 
}

int main ( void ) 
{  
   // Cria uma nova pilha
   Pilha * stack = criar_Pilha (); 
   
   // Empilhando alguns elementos para testar
   push ( stack , 10 );
   push ( stack , 20 );
   push ( stack , 30 );
   push ( stack , 40 );
   push ( stack , 99 );
   
   // Visualizando o elemento no topo da pilha
   printf ( "- Elemento no topo da pilha: %d\n" , peek ( stack ) );
   
   // Desempilhando um elemento
   printf ( "- Elemento desempilhado:     %d\n" , pop ( stack ) );
   
   // Visualizando o elemento no topo da pilha após a desempilhamento
   printf ( "- Elemento no topo da pilha: %d\n", peek ( stack ) );
   
   // Liberando a memória da pilha
   free ( stack );
}
```

<h3 align="center"> <a href="#pilhas" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

