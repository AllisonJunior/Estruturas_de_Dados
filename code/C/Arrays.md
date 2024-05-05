# Arrays

A linguagem de programação C possui duas formas distintas de se criar um <a href="." title="Ou em português vetor">**array**</a>, sendo primeiramente de forma <a href="" title="o vetor possui um tamanho máximo fixo">**estática**</a> e a outra de forma <a href="" title="o vetor pode ser expandido ou reduzido">**dinâmica**</a>. Portanto em resumo aqui serão apresentadas ambas as formas de como os <a href="" title="ou em português vetores">**arrays**</a> podem ser implementados e utilizados, incluindo algumas dicas de programação.


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

### Algumas Usabilidades
```main.c

/*
  FUNÇÃO:      Essa função printa todos os elementos de um vetor
  @parâmetro1: O vetor que terá seus elementos printados
  @parâmetro2: O tamanho do vetor
*/
void print_Array ( int vetor [] , int tamanho )
{
    for ( int i = 0 ; i < tamanho ; i ++ )
       printf ( "%d " , vetor [ i ] ); 
}

/*
  FUNÇÃO:      Essa função retorna a soma de todos os elementos do vetor
  @parâmetro1: O vetor que terá seus elementos somados
  @parâmetro2: O tamanho do vetor
*/
int sum_Array ( int vetor [] , int tamanho )
{
   int soma = 0;

   for ( int i = 0 ; i < tamanho ; i ++ )
      soma += vetor [ i ];

   return soma;  
}

/*
  FUNÇÃO:      Essa função retorna o maior número presente em um vetor
  @parâmetro1: O vetor que terá seus elementos checados
  @parâmetro2: O tamanho do vetor
*/
int higher_value ( int vetor [] , int tamanho )
{
   int maior = vetor [ 0 ];

   for ( int i = 0 ; i < tamanho ; i ++ )
      if ( maior < vetor [ i ] ) maior = vetor [ i ];

   return maior; 
}
```

# Dinamic Array

### Declaração e Inicialização
```main.c
/*
   Aqui só estão expostas como esse tipo de vetor dinâmico pode
   ser inicializado, portanto a explicação detalhada está na próxima
   sessão, explicando passo a passo.
*/

// Declaração de vetor não inicializado
int * vetor;

// Declaração de vetor nulado
int * vetor = NULL;

// Declaração inicializada para um vetor de 5 posições
int * vetor = ( int * ) malloc ( sizeof ( int ) * 5 ); 
```

### Alocação e Formas de Preenchimento
```main.c
/*
  Como funciona o processo de alocação de memória para um dado qualquer em C?
  Utilizando as funções da biblioteca stdlib.h, no caso as funções malloc ();
  e free (); Para respectivamente alocar memória e liberar memória, como será
  discutido e mostrado abaixo;

  1 - Definimos o tipodo nosso ponteiro
  int * vetor;

  2 - Iniciamos o processo de alocação, fazendo um casting para o tipo definido anteriormente
  int * vetor = ( int * )

  3 - Continuamos agora utilizando a função malloc
  int * vetor = ( int * ) malloc ();

  4 - Em seguida preenchemos o parâmetro da função malloc, que é basicamente o tamanho de memória
  que será alocado, no caso 'sizeof ( int )'
  int * vetor = ( int * ) malloc ( sizeof ( int ) );

  5 - Por fim definimos a quantidade de espaços que serão alocados, no caso 4, que pode ser traduzido
  como a criação de um vetor com 4 posições.
  int * vetor = ( int * ) malloc ( sizeof ( int ) * 4 );

  6 - Seguindo fazemos uma checagem para ver se o sistema conseguiu alocar corretamente, que é básicamente
  checar se a alocação resultou em NULL
  int * vetor = ( int * ) malloc ( sizeof ( int ) * 4 );
  if ( NULL == vetor )
  {
    printf ( "- O vetor não foi alocado com sucesso!" );
    exit ( 1 ); 
  }

  7 - Por fim após terminarmos de utilizar esse vetor, podemos liberar a memória
  int * vetor = ( int * ) malloc ( sizeof ( int ) * 4 );
  if ( NULL == vetor )
  {
    printf ( "- O vetor não foi alocado com sucesso!" );
    exit ( 1 ); 
  }

  ...

  free ( vetor ); 


A forma de preenchimento, permanece a mesma da discutida no vetor estático
mas, precisa-se ressaltar o seguinte detalhe abaixo, não só no preenchimento
manual do vetor dinâmico. Em todas as outras formas de preenchimento já
apresentadas, precisa se levar em conta o seguinte:

    // Alocando memória para SÓ PARA 4 ESPAÇOS
    int * vetor = ( int * ) malloc ( sizeof ( int ) * 4 );       

    vetor [ 0 ] = 9;
    vetor [ 1 ] = 8;
    vetor [ 2 ] = 7;
    vetor [ 3 ] = 6;
    vetor [ 4 ] = 5; // Preenchendo memória não alocada
    vetor [ 5 ] = 4; // Preenchendo memória não alocada

    // Aqui teremos o print até a sessão que não foi alocada corretamente
    for ( int i = 0 ; i < 6 ; i ++ ) printf ( "%d " , vetor [ i ] );
 
Note que nada me impede de adicionar vetor [ 4 ] = 5, ou até mesmo vetor [ 5 ] = 4,
portanto tome muito cuidado com a forma que você está preenchendo, e sempre verifique
para o usuário ou o próprio programador não causar um problema de buffer overflow.

O importante a ressaltar aqui é que fazer o que foi feito acima pode ou não resultar em
problemas ao próprio sistema operacional, pois o buffer overflow é basicamente substituição
ou subescrever sobre um campo de memória não alocado, então tenha muito cuidado ao trabalhar
com ponteiros na linguagem C. 
*/
```

### Algumas Usabilidades
```main.c
```

# Algumas Dicas

<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title=""> Retornar a página principal </a> </h3>
