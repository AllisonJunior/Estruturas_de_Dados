# Arrays

A linguagem de programação C possui duas formas distintas de se criar um <a href="Arrays.md" title="vetor ou uma matriz">**array**</a>, sendo primeiramente de forma <a href="Arrays.md" title="o vetor/matriz possui um tamanho máximo fixo">**estática**</a> e a outra de forma <a href="Arrays.md" title="o vetor/matriz pode ser expandido ou reduzido">**dinâmica**</a>. Portanto em resumo aqui serão apresentadas ambas as formas de como os <a href="Arrays.md" title="vetores/matrizes">**arrays**</a> podem ser implementados e utilizados, junto a um pequeno sumário abaixo para melhorar sua navegação pela página.

- <a href="#introdução" title="Introdução a arrays">**Introdução**</a>
- <a href="#static-array" title="Vetor estático">**Static Array**</a>
- <a href="#dinamic-array" title="Direto">**Dinamic Array**</a>
- <a href="#bidimensional-static-array" title="Direto">**Bidimensional Static Array**</a>
- <a href="#bidimensional-dinamic-array" title="Direto">**Bidimensional Dinamic Array**</a>

---

# Introdução

### *Vetores/Arrays*
```main.c
# include <stdio.h>



int main ( void )
{
   // Declaração não inicializada
   int vetor [ 10 ];
   char vetor [ 20 ];
   struct qualquer vetor [ 10 ]; // struct qualquer { int v1; char v2; };
   Pilha vetor [ 10 ];
   char * vetor [ 10 ];
   int * vetor; 

   // Declaração inicializada
   int vetor [] = { 1 , 2 , 3 , 4 , 5 , 6 , 7 , 8 , 9 , 10 };
   char vetor [ 10 ] = { '#' , '#' , '@' , '!' , '*' , '$' , '%' , '+' , '-' , '^' };
   struct qualquer vetor [ 2 ] = { { 1 , 'c' } , { 2 , 'd' } }; // struct qualquer { int v1; char v2; };
   Pilha vetor [ 2 ] = { { 0 } , { 0 } }; // Inicializando as duas posições zeradas
   char * vetor [ 3 ] = { "The"  , "song of" , "my life!" };
   int * vetor = ( int * ) malloc ( sizeof ( int ) * quantidade_de_elementos );
}
```

### *Matrizes/Bidimensional Arrays*
```main.c
# include <stdio.h>



int main ( void )
{
   // Declaração não inicializada
   int matr [ 3 ] [ 2 ];
   char matr [ 4 ] [ 20 ]; // Aqui temos um vetor de strings, funciona similar a char * matr [ 20 ] e char ** matr;
   struct qualquer matr [ 2 ] [ 3 ];
   Pilha matr [ 3 ] [ 5 ];
   char * matr [];

   // Declaração inicializada
   int matr [ 3 ] [ 2 ] = { { 1 , 2 } , { 3 , 4 } , { 5 , 6 } };
   char matr [ 3 ] [ 20 ] = { { "Robson" } , { "Adair" } , { "Cleusa" } };
   struct qualquer matr [ 2 ] [ 3 ] =
   {
         { { 1 , 'a' } , { 2 , 'b' } , { 3 , 'c' } },
         { { 4 , 'd' } , { 5 , 'e' } , { 6 , 'f' } }
   };
   Pilha matr [ 2 ] [ 2 ] = { { { 0 } , { 0 } } , { { 0 } , { 0 } } };
   char * matr [] = { "Allowed" , "Proihibited" , "Unknow" };
}
```


# Static Array

### Exemplo 1: *Soma de valores em um vetor*
```main.c
// Criação de constante
# define TAMANHO_DO_VETOR 5

# include <stdio.h>



int main ( void )
{
   // Declaração do vetor estático sem preencher
   int vetor [ TAMANHO_DO_VETOR ];

   // Preenchendo o vetor com valores fornecidos pelo usuário
   printf ( "[ MENU INTERATIVO - SOMA DE NÚMEROS DE UM VETOR ]\n\n" );
   for ( int i = 0 ; i < TAMANHO_DO_VETOR ; i ++ )
   {
      printf ( "- Digite o valor do %dº número: " , i + 1 );
      scanf ( "%d" , &vetor [ i ] );
      setbuf ( stdin , NULL ); // Similar ao fflush ( stdin );
   }
   
   // Imprimindo os elementos do vetor
   printf ( "\n- Os números digitados foram: [ " );
   for ( int i = 0 ; i < TAMANHO_DO_VETOR ; i ++ ) 
      printf ( "%d " , vetor [ i ] );
   printf ( "]\n" );

   // Calculando a soma dos elementos do vetor
   int soma = 0;
   for ( int i = 0 ; i < TAMANHO_DO_VETOR ; i ++ ) 
      soma += vetor [ i ];
   printf ( "\n- A soma dos números é: %d\n" , soma );
}
```
### Exemplo 2: **
```main.c
```

### Exemplo 3: **
```main.c
```

### Exemplo 4: **
```main.c
```

# Dinamic Array
```main.c
```

# Bidimensional Static Array
```main.c
```

# Bidimensional Dinamic Array
```main.c
```

<h3 align="center"> <a href="#arrays" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

