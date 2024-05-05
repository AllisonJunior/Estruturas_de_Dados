# Arrays

A linguagem de programação C possui duas formas distintas de se criar um <a href="Arrays.md" title="vetor ou uma matriz">**array**</a>, sendo primeiramente de forma <a href="Arrays.md" title="o vetor/matriz possui um tamanho máximo fixo">**estática**</a> e a outra de forma <a href="Arrays.md" title="o vetor/matriz pode ser expandido ou reduzido">**dinâmica**</a>. Portanto em resumo aqui serão apresentadas ambas as formas de como os <a href="Arrays.md" title="vetores/matrizes">**arrays**</a> podem ser implementados e utilizados. 

- <a href="#static-array" title="Vetor estático">**Static Array**</a>
- <a href="#dinamic-array" title="Direto">**Dinamic Array**</a>
- <a href="#bidimensional-static-array" title="Direto">**Bidimensional Static Array**</a>
- <a href="#bidimensional-dinamic-array" title="Direto">**Bidimensional Dinamic Array**</a>

---

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

