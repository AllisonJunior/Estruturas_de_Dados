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

--------------------------------------------------------------

  COMO USAR/MANIPULAR:

  *Um vetor pode ser utilizado/manipulado das seguintes formas:

  1 - Acesso direto.
  2 - Loops de iteração.
  3 - Referência.
  
  *Onde, acesso direto se refere a ação de se alterar diretamente
  um índice do vetor, como abaixo:

  int vetor_de_int [ 4 ];
  vetor_de_int [ 0 ] = 12;
  vetor_de_int [ 1 ] = 18;
  vetor_de_int [ 2 ] = 10;
  vetor_de_int [ 3 ] = 14;

  *Já os loops de iteração, são basicamente o uso de 'while', 'for'
  'do while', com uma variável auxiliar, como nos exemplos abaixo:

  // Vetor de exemplo
  int vetor_de_int [ 4 ];
  int tamanho_do_vetor = 4;
   
  // Utilizando um loop do tipo for
  for ( int i = 0 ; i < tamanho_do_vetor ; i ++ ) vetor_de_int [ i ] += 1;

  // Utilizando um loop do tipo while
  int i = 0;
  while ( i < tamanho_do_vetor ) vetor_de_int [ i ] += 1;

  // Utilizando um do tipo do while
  int i = 0;
  do
  {
    vetor_de_int [ i ] += i;
  }
  while ( i < tamanho_do_vetor )

  *Por fim temos a manipulação por referência, que se trata
  do uso de um vetor como parâmetro de uma função:

  void print_vetor ( int vetor [] , int tamanho_do_vetor )
  {
      for ( int i = 0 ; i < tamanho_do_vetor ; i ++ ) printf ( "%d " , vetor [ i ] );
  }

  // Função que soma +1 para cada elemento do vetor
  void do_stuff ( int vetor [] , int tamanho_do_vetor )
  {   
      for ( int i = 0 ; i < tamanho_do_vetor ; i ++ ) vetor [ i ] ++;
  }   

  int main ( void )
  { 
     int vetor_de_int [ 4 ];

     // Print inicial
     print_vetor ( vetor_de_int , 4 ); 

     // Modificando
     do_stuff ( vetor_de_int , 4 );
   
     // Print após modificação
     print_vetor ( vetor_de_int , 4 );  
  }
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

# Matrizes

### Sintaxe
```main.c
/*
  Para se fazer qualquer declaração de uma matriz em c, seguimos
  a seguinte ideia:

  <tipo> <nome_da_matriz> <[linhas_da_matriz]> <[colunas_da_matriz]>

  isso é válido para qualquer tipo de dado que venha a se tornar
  uma matriz, como no exemplo abaixo:
*/

double matriz_de_doubles [ 2 ] [ 2 ];
gwyin matriz_de_gwyins [ 32 ] [ 10 ];
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

