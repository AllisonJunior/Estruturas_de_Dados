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
      
   // Vetor de TAD sem typedef
   struct Pint random_test [ 10 ];
   struct Pint random_vars [] = 
   { 
         { 202200132 , 14 , 22 }, 
         { 231002202 , 33 , 32 } 
   };

   // Preenchendo o TAD clientes
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
*/
```

### Variáveis Primitivas
```main.c
```

### Estruturas/TADs
```main.c
```

### Ponteiros
```main.c
```

<h3 align="center"> <a href="#arrays" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

