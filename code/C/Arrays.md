# Arrays

A linguagem de programação C possui duas formas distintas de se criar um <a href="Arrays.md" title="vetor ou uma matriz">**array**</a>, tanto na forma <a href="Arrays.md" title="o vetor/matriz possui um tamanho máximo fixo">**estática**</a> como na forma <a href="Arrays.md" title="o vetor/matriz pode ser expandido ou reduzido">**dinâmica**</a>. Um <a href="Arrays.md" title="vetor ou uma matriz">**array**</a> nada mais é do que uma coleção de variáveis do mesmo tipo que são acessadas atráves de um índice (*índice esse que sempre começa a partir de zero!*), ou seja, é muito útil para armazenar dados de uma maneira sequencial. 

---

# Vetores

### Sintaxe
```main.c
/*
  DECLARAÇÃO:

  *Para se fazer qualquer declaração de vetor em c, seguimos
  a seguinte ideia:

  <tipo> <nome_do_vetor> <[tamanho_do_vetor]>

  *Isso é válido para qualquer tipo de dado que venha a ser 
  um vetor, como no exemplo abaixo:

  int vetor_de_inteiros [ 4 ];
  blob vetor_de_blobs [ 3 ];
*/
```

### Variáveis Primitivas
```main.c
// Declaração
int vetorI [ 3 ];
char vetorC [] = { '#' , '#' , '#' , '!' };
float vetorF [ 5 ] = { 1.2 , 3.4 , 2.1 , 9.2 , 5.6 };
double vetorD [ 10 ];

// Preenchendo um vetor de 'inteiros'
for ( int i = 0 ; i < 3 ; i ++ ) vetorI [ i ] += 1;

// Printando o vetor de 'caracteres'
for ( int i = 0 ; i < 4 ; i ++ ) printf ( "%c " , vetorC [ i ] );

// Printando o vetor de 'floats'
for ( int i = 0 ; i < 5 ; i ++ ) printf ( "%.1f " , vetorF [ i ] ); 

// Preenchendo um vetor de 'doubles'
for ( int i = 0 ; i < 10 ; i ++ ) vetorD [ i ] = i + ( 0.45 * i );
```

### Estruturas/TADs
```main.c
// TAD: Representação de um ponto
typedef struct { int x; int y; } Point;

// TAD: Dados de uma pessoa
struct Pint { int id; int valor; int capacity; };



int main ( void )
{
   // Vetor de TAD com typedef 
   Point cursor [ 4 ] = { 0 };
   Point pixels [] = { { 0 , 1 } , { 10 , 3 } };

   // Preenchendo o TAD cursor
   for ( int i = 0 ; i < 4 ; i ++ )
   {
      cursor [ i ] . x = i + 1;
      cursor [ i ] . y = i * 2;
   }

   // Printando o TAD pixels
   for ( int i = 0 ; i < 2 ; i ++ )
      printf ( "%d -> [%0.2d,%0.2d]\n" , i , pixels [ i ] . x , pixels [ i ] . y );

   // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

   // Vetor de TAD sem typedef
   struct Pint random_test [ 10 ];
   struct Pint random_vars [] = 
   { 
         { 202200132 , 14 , 22 }, 
         { 231002202 , 33 , 32 } 
   };

   // Preenchendo o TAD random_test
   for ( int i = 0 ; i < 10 ; i ++ )
   {
      random_test [ i ] . id = 202200000 + ( i * 32 );
      random_test [ i ] . valor = i * ( 100 + 32 );
      random_test [ i ] . capacity = i * 10;
   }   

   // Printando o TAD random_vars
   for ( int i = 0 ; i < 2 ; i ++ )
      printf ( "{%d %d %d}\n" , random_vars [ i ] . id , random_vars [ i ] . valor , random_vars [ i ] . capacity );
}
```

### Ponteiros
```main.c
/* ALOCAÇÃO DE PONTEIRO PARA VETOR DE INTEIROS */

int main ( void )
{
   // Quantidade de elementos do vetor
   int elements = 5;

   // Ponteiro de inteiro que será alocado para um vetor
   int * vetor;

   // Inicializando um vetor de inteiros com 5 elementos
   // e fazendo a checagem de erro
   vetor = ( int * ) malloc ( sizeof ( int ) * elements );
   if ( NULL == vetor ) exit ( 1 );

   // Preenchendo o nosso vetor
   vetor [ 0 ] = 10;
   vetor [ 1 ] = 20;
   vetor [ 2 ] = 30;
   vetor [ 3 ] = 40;
   vetor [ 4 ] = 50;

   // Podemos printar para testar
   for ( int i = 0 ; i < elements ; i ++ ) printf ( "%d " , vetor [ i ] );

   // Após utilizarmos o nosso vetor, o desalocamos para liberar
   // memória ( sempre faça isso quando alocar )
   free ( vetor );
}
```
```main.c
/* ALOCAÇÃO DE PONTEIRO PARA VETOR DE STRING ( char ** ) */

void adiciona_string ( char * texto_pra_adicionar , char * destino_de_adicao )
{
    strncpy ( destino_de_adicao , texto_pra_adicionar , 20 );
}

void printa_strings ( char ** vetor_de_strings , int tamanho )
{
    for ( int i = 0 ; i < tamanho ; i ++ )
       printf ( "{%d} - %s\n" , i , vetor_de_strings [ i ] );
}

int main ( void )
{
   // Como sabemos uma string é um vetor de caracteres, portanto
   // um vetor de strings seria uma matriz de caracteres ou vetor
   // de vetor de caracteres, em um contexto de ponteiros teriamos
   // a seguinte notação
   char ** strings;
   int elements = 5;
   int max_size = 20;

   // Fazemos a alocação para 5 strings no nosso vetor de strings
   // e claro, fazemos a checagem de erro
   strings = ( char ** ) malloc ( sizeof ( char * ) * elements );
   if ( NULL == strings ) exit ( 1 );

   // Agora alocamos o tamanho máximo de caracteres para cada índice
   // do nosso vetor de strings
   for ( int i = 0 ; i < elements ; i ++ )
   {
      strings [ i ] = ( char * ) malloc ( sizeof ( char ) * ( max_size + 1 ) );
      if ( NULL == strings [ i ] ) exit ( 1 );
   }

   // Agora utilizando a função 'adiciona_string' iremos inserir
   // as strings para cada índice do vetor
   adiciona_string ( "Roberto Almeida Costa" , strings [ 0 ] );
   adiciona_string ( "Almeida Lima" , strings [ 1 ] );
   adiciona_string ( "Aldemir Roberto Silva" , strings [ 2 ] );
   adiciona_string ( "Valentina Cobra Dutra" , strings [ 3 ] );
   adiciona_string ( "Ofensa Total Escola" , strings [ 4 ] );   

   // Agora vamos ver todas as strings salvas, lembrando que só
   // é salvo até 20 caracteres da string que foi passada por 
   // causa da função 'strncpy', por questões óbvias de segurança
   printa_strings ( strings , elements ); 

   // Após utilizarmos o nosso vetor, o desalocamos para liberar
   // memória ( sempre faça isso quando alocar )
   free ( strings );
}
```

# Matrizes

### Sintaxe
```main.c
/*
  Para se fazer qualquer declaração de uma matriz em c, seguimos
  a seguinte ideia:

  <tipo> <nome_da_matriz> <[linhas_da_matriz]> <[colunas_da_matriz]>

  isso é válido para qualquer tipo de dado que venha a se tornar
  uma matriz, como no exemplo abaixo:

  double matriz_de_doubles [ 2 ] [ 2 ];
  gibba matriz_de_gibba [ 32 ] [ 10 ];

  * LEMBRE-SE: Na declaração em c de uma matriz, se não for definido
  a quantidade de linhas, no mínimo deve ser inserida a quantidade de
  colunas, como nos dois exemplos abaixo:

  - ERRADO -
  int matriz [] [] = { { 1 , 2 } , { 3 , 4 } };
 
  - CORRETO -
  int matriz [] [ 2 ] = { { 1 , 2 } , { 3 , 4 } };

  O que acontece é que na declaração de uma matriz o compilador sempre
  requisita a quantidade de colunas que cada linha tera, por isso não
  podemos deixar ambos sem valor e preencher diretamente!
*/
```

### Variáveis Primitivas
```main.c
// Declaração
int matrizI [ 3 ] [ 10 ]; 
char matrizC [] [ 4 ] = { '#' , '#' , '#' , '!' };
float matrizF [ 5 ] [ 2 ] = { { 1.2 , 3.4 } , { 2.1 , 9.2 } , { 5.6 , 3.4 } , { 47.2 , 1.2 } , { 2.9 , 1.8 } };
double matrizD [ 2 ] [ 10 ];

// Preenchendo uma matriz de 'inteiros'
for ( int l = 0 ; l < 3 ; l ++ ) for ( int c = 0 ; c < 10 ; c ++ )
   matrizI [ l ] [ c ] = c * 2; 

// Printando o vetor de 'caracteres'
for ( int c = 0 ; c < 4 ; c ++ ) printf ( "%c " , matrizC [ 0 ] [ i ] );

// Printando o vetor de 'floats'
for ( int l = 0 ; l < 5 ; l ++ ) for ( int c = 0 ; c < 2 ; c ++ )
   printf ( "%.1f " , matrizF [ l ] [ c ] ); 

// Preenchendo um vetor de 'doubles'
for ( int l = 0 ; l < 2 ; l ++ ) for ( int c = 0 ; c < 10 ; c ++ )
   matrizD [ l ] [ c ] = 0.45 * c;
```

### Estruturas/TADs
```main.c
// TAD: Representação de um ponto
typedef struct { int x; int y; } Point;

// TAD: Dados de uma pessoa
struct Pint { int id; int valor; int capacity; };



int main ( void )
{
   // Matriz de TAD com typedef 
   Point cursor [ 2 ] [ 4 ] = { 0 };
   Point pixels [] [ 3 ] = { { 1 , 2 , 3 } , { 40 , 100 } };

   // Preenchendo o TAD cursor
   for ( int l = 0 ; l < 2 ; l ++ ) for ( int c = 0 ; c < 4 ; c ++ )
   {
      cursor [ l ] [ c ] . x = c + 1;
      cursor [ l ] [ c ] . y = c * 33;
   }

   // Printando o TAD pixels
   for ( int l = 0 ; l < 2 ; l ++ ) for ( int c = 0 ; c < 3 ; c ++ )
      printf ( "%d -> [%0.2d,%0.2d]\n" , l , pixels [ l ] [ c ] . x , pixels [ l ] [ c ] . y );

   // - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

   // Vetor de TAD sem typedef
   struct Pint random_test [ 1 ] [ 2 ];
   struct Pint random_vars [ 3 ] [ 2 ] = 
   { 
         { { 202200111 , 12 , 33 } , { 202200132 , 14 , 22 } }, 
         { { 202200077 , 67 , 21 } , { 202200131 , 44 , 82 } },
         { { 202200001 , 85 , 81 } , { 202200147 , 32 , 98 } }
   };

   // Preenchendo o TAD random_test
   for ( int c = 0 ; c < 2 ; c ++ )
   {
      random_test [ 0 ] [ c ] . id = 202200000 + ( c * 32 );
      random_test [ 0 ] [ c ] . valor = c * ( 100 + 32 );
      random_test [ 0 ] [ c ] . capacity = c * 10;
   }   

   // Printando o TAD random_vars
   for ( int l = 0 ; l < 3 ; l ++ ) for ( int c = 0 ; c < 2 ; c ++ )
      printf ( "{%d %d %d}\n" , random_vars [ l ] [ c ] . id , random_vars [ l ] [ c ] . valor , random_vars [ l ] [ c ] . capacity );
}
```

<h3 align="center"> <a href="#arrays" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

