# Arrays

A linguagem de programação C possui duas formas distintas de se criar um <a href="" title="Ou em português vetor">**array**</a>, sendo primeiramente de forma <a href="" title="o vetor possui um tamanho máximo fixo">**estática**</a> e a outra de forma <a href="" title="o vetor pode ser expandido ou reduzido">**dinâmica**</a>. Portanto em resumo aqui serão apresentadas ambas as formas de como os <a href="" title="ou em português vetores">**arrays**</a> podem ser implementados e utilizados, incluindo algumas dicas de programação.


# Static Array

### Declaração e Inicialização
```main.c
/*
  Aqui está sendo utilizado um vetor do tipo inteiro, mas poderia
  ser um 'char', 'float', 'double' e até mesmo um TAD.
*/

// Declaração de vetor não preenchido 
int vetor [ 5 ];

// Declaração de vetor preenchido
int vetor [] = { 0 , 1 , 2 , 3 , 4 };

// Declaração de vetor preenchido por zeros
int vetor [ 5 ] = { 0 };
```

### Formas de Preenchimento
```main.c
/*
  Aqui está sendo considerado um vetor do tipo inteiro, que
  não está preenchido e possui um tamanho total de 5.
*/

// Preenchimento de forma manual
vetor [ 0 ] = 9;
vetor [ 1 ] = 8;
vetor [ 2 ] = 7;
vetor [ 3 ] = 6;
vetor [ 4 ] = 5;

// Preenchimento utilizando um for loop
for ( int i = 0 ; i < 5 ; i ++ )
   vetor [ i ] = i + 1;

// Preenchimento utilizando um while loop
int i = 0;
while ( i < 5 )
{
     vetor [ i ] = i + 1;
     i ++; 
}

// Preenchimento utilizando um do while
int i = 0;
do
{
  vetor [ i ] = i + 1;
  i ++;  
}
while ( i < 5 );
```

# Dinamic Array

### Declaração 
```main.c

```

<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title=""> Retornar a página principal </a> </h3>
