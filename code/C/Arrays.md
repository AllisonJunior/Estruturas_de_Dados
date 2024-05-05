# Arrays

A linguagem de programação C possui duas formas distintas de se criar um <a href="Arrays.md" title="Ou em português vetor">**array**</a>, sendo primeiramente de forma <a href="Arrays.md" title="o vetor possui um tamanho máximo fixo">**estática**</a> e a outra de forma <a href="Arrays.md" title="o vetor pode ser expandido ou reduzido">**dinâmica**</a>. Portanto em resumo aqui serão apresentadas ambas as formas de como os <a href="Arrays.md" title="ou em português vetores">**arrays**</a> podem ser implementados e utilizados. 


# Static Array

### Exemplo 1: *Soma de valores em um vetor*
```main.c
// Criação de constante
# define TAMANHO_DO_VETOR 5

# include <stdio.h>



int main ( void )
{
   // Declaração do vetor estático
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

# Dinamic Array
```main.c
```

# Bidimensional Static Array
```main.c
```

# Bidimensional Dinamic Array
```main.c
```

<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title=""> Retornar a página principal </a> </h3>
