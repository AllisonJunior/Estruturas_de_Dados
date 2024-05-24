# Arrays

A linguagem de programação C possui duas formas distintas de se criar um <a href="Arrays.md" title="vetor ou uma matriz">**array**</a>, tanto na forma <a href="Arrays.md" title="o vetor/matriz possui um tamanho máximo fixo">**estática**</a> como na forma <a href="Arrays.md" title="o vetor/matriz pode ser expandido ou reduzido">**dinâmica**</a>.

---

# Vetores

# Variáveis Primitivas
```main.c
```

# Estruturas/TADs
```main.c
```

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

   // Para alterar o vetor, basta seguir o exemplo abaixo, onde o que está dentro do colchete é o índice do vetor:
   int vetor [] = { 1 , 2 , 3 };
   vetor [ 2 ] = 34;
   vetor [ 0 ] = 12;
}
```

# Matrizes

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

   // Para alterar a matriz assim como no vetor, como no exemplo abaixo basta,
   // definir nos colchetes as linhas e colunas que serão preenchidas:
   int vetor [ 2 ] [ 2 ];
   vetor [ 0 ] [ 0 ] = 1; // 1 0  0 0 
   vetor [ 0 ] [ 1 ] = 2; // 1 2  0 0
   vetor [ 1 ] [ 0 ] = 3; // 1 2  3 0  
   vetor [ 1 ] [ 1 ] = 4; // 1 2  3 4
}
```

<h3 align="center"> <a href="#arrays" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

