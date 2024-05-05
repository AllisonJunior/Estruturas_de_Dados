# Pilhas

A linguagem de programação C não possui uma forma padrão de se implementar <a href="Pilhas.md" title="uma coleção linear de elementos vulgo stack">**pilhas**</a>, que seguem o princípio de <a href="Pilhas.md" title="Last In, First Out: o último elemento inserido é o primeiro a ser removido.">**LIFO**</a>, por isso utilizamos um <a href="Pilhas.md" title="Tipo Abstrato de Dado: Struct">**TAD**</a> para chegar a esse resultado, utilizando um modelo de implementação estática ou dinâmica. Portanto abaixo teremos a demonstração de implementações base dessas duas formas de implementação e claro alguns exemplos de utilização, junto a um pequeno sumário abaixo para melhorar sua navegação pela página.

- <a href="#introdução" title="Introdução a pilhas">**Introdução**</a>
- <a href="#pilha-estática" title="Introdução a pilhas estáticas">**Pilha Estática**</a>
- <a href="#pilha-dinâmica" title="Introdução a pilhas dinâmicas">**Pilha Dinâmica**</a>

--- 

# Introdução

A ídeia de pilhas como já discutido anteriormente, consiste no príncipio de <a href="Pilhas.md" title="Last In, First Out: o último elemento inserido é o primeiro a ser removido.">**LIFO**</a>, portanto na sua implementação seja para qualquer tipo de <a href="Pilhas.md" title="uma coleção linear de elementos vulgo stack">**pilha**</a> ( *inteiro*, *caractere*, *string* ) e forma de alocação ( *estática* ou *dinâmica* ), iremos ter a implementação das funções *pop* e *push*, que respectivamente significam *remover* e *adicionar*, além de algumas outras funções como a de *print* para listar todos os elementos da pilha, *is_full* para checar se está cheia e várias outras. Nesse caso aqui iremos focar somente nas funções *pop* e *push* pois as mesmas utilizam o **topo** ou **índice** da pilha como base para executar suas manipulações, portanto vamos seguir com a seguinte ideia:

**Suponhamos um livro "LIVRO 0", como na imagem abaixo ( Esse séria nosso primeiro elemento, o que também indicaria um topo = 0 ):**

![STATE_1](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/c29de8e6-9b40-46dc-adec-41f2b90d7360)

**Como se pode ver, ele está sozinho e caso eu desejasse o pegar não teria complicação alguma ( pois nosso topo é igual ao livro atual ), mas vamos supor que eu empilhei outro livro em cima do "LIVRO 0" no caso o "LIVRO 1" ( aqui temos o uso da função push ), como dá para ver abaixo ( teríamos uma atualização no topo, que de 0 foi para 1 ):**

![STATE_2](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/73e961b0-67a8-41cc-b764-42bb60875c2c)

**Agora temos 2 livros empilhados! Mas vamos supor novamente que eu comprei outro livro "LIVRO 2" e decidi empilhar ele, teríamos o seguinte ( o topo que era 1 virou 2 ):**

![STATE_3](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/7dc0ca73-1b32-4b65-b506-d4881f3745cc)

**Como dá para ver empilhamos 2 livros em cima do "LIVRO 0", mais e aí como eu faço para pegar ele? Eu preciso remover todos os livros que estão em cima dele ( usando a função pop )!**

***1º PASSO - Desejo retirar o "LIVRO 0"***

![STATE_3](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/7dc0ca73-1b32-4b65-b506-d4881f3745cc)

***2º PASSO - Retiro o "LIVRO 2" de cima do "LIVRO 1" pois ele está em cima ( ou pop ( &livros ) ):***

![STATE_2](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/73e961b0-67a8-41cc-b764-42bb60875c2c)

***3º PASSO - Retiro o "LIVRO 1" de cima do "LIVRO 0" ( ou pop ( &livros ) ). Assim conseguimos acessar o "LIVRO 0"!***

![STATE_1](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/c29de8e6-9b40-46dc-adec-41f2b90d7360)

**Apesar da analógia não ser tão perfeita, a ideia de pilha é basicamente essa, você irá estacar / empilhar <a href="Pilhas.md" title="valores do tipo inteiro, strings, números reais e até mesmo dados de dados">**dados**</a> de tal forma que sempre que você desejar acessar uma posição específica diferentemente de um vetor/array, você não poderá acessar aquela posição diretamente e alterar-lá, será necessário remover o último elemento continuamente até chegar na posição desejada, o que basiscamente é o princípio de <a href="Pilhas.md" title="Last In, First Out: o último elemento inserido é o primeiro a ser removido.">**LIFO**</a>.** 

### Para concluir, podemos levantar as seguintes dúvidas: *como posso usar uma pilha no contexto de computação e quais benefícios e desvantagens seu uso trás?*

### **UTILIDADE** 

- **Implementação de Funções Recursivas:** *As pilhas são frequentemente usadas para implementar chamadas de função recursiva. Cada chamada de função é empilhada e processada quando as chamadas recursivas retornam.*
- **Expressões Matemáticas e Avaliação de Expressões Postfixas:** *Pilhas são úteis para a avaliação de expressões postfixas (notação polonesa reversa) e na conversão entre notações infixa, prefixa e postfixa.*
- **Gerenciamento de Memória:** *Em linguagens de programação que não têm coleta de lixo automática, as pilhas são usadas para gerenciar a alocação e desalocação de memória.*
- **Navegação em Profundidade em Estruturas de Dados:** *Ao percorrer estruturas de dados como árvores ou grafos em profundidade, as pilhas podem ser usadas para armazenar os nós que ainda precisam ser explorados.*
- **Desfazer Operações:** *Pilhas são usadas para implementar a funcionalidade "desfazer" em muitos aplicativos, onde as operações são empilhadas conforme são executadas e desempilhadas quando o usuário deseja desfazer uma ação.*

### **BENEFÍCIOS**

- **Simplicidade:** *Pilhas são estruturas de dados simples e fáceis de entender e implementar.*
- **Eficiência de Espaço:** *Elas geralmente usam uma quantidade fixa de memória para armazenar os elementos, tornando o uso de memória eficiente.*
- **Eficiência de Tempo:** *As operações de inserção (push) e remoção (pop) em uma pilha têm complexidade de tempo constante (O(1)), tornando-as rápidas.*
- **Reversão de Ordem:** *A natureza LIFO das pilhas é útil em situações em que a ordem reversa de processamento é necessária.*

### **DESVANTAGENS**

- **Limitação de Capacidade:** *Pilhas têm um tamanho fixo e podem estourar se forem empilhados muitos elementos, levando a problemas de estouro de pilha.*
- **Limitação de Funcionalidade:** *Elas são adequadas apenas para determinados tipos de problemas e podem não ser a estrutura de dados ideal em todas as situações.*
- **Complexidade de Implementação Recursiva:** *Em alguns casos, a implementação de algoritmos recursivos usando pilhas pode ser mais complexa do que uma abordagem iterativa.*
- **Acesso Limitado aos Elementos:** *A menos que você esteja implementando uma pilha com acesso aleatório, como uma pilha vinculada, o acesso aos elementos fora do topo da pilha pode ser limitado.*

### **PILHA ESTÁTICA E DINÂMICA**

A **pilha estática** é implementada usando um vetor de tamanho fixo. A inserção e remoção de elementos ocorrem apenas em uma extremidade da pilha, chamada de topo já no caso da **pilha dinâmica**, os elementos são armazenados em nós encadeados. Cada nó contém um elemento e um ponteiro para o próximo nó na pilha. O topo da pilha é representado pelo primeiro nó. Podemos concluir então o seguinte, enquanto a **pilha estática** é mais simples de implementar e mais eficiente em termos de memória, a **pilha dinâmica** oferece mais flexibilidade em termos de tamanho e é mais adequada para situações em que o tamanho máximo da pilha não é conhecido antecipadamente ou pode variar durante a execução do programa, além de permitir a expansão caso necessário.

# Pilha Estática

### Implementação
```main.c
// Constantes
# define MAX_CAPACITY  4
# define CHEIA         3
# define VAZIA        -1

# include <stdio.h>
# include <stdlib.h>



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

int main ()
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

### Implementação com um menu interativo
```main.c
// Definição de Constantes
# define CAPACIDADE_MAXIMA 4
# define CHEIA             3
# define VAZIA            -1

# include <stdio.h>
# include <stdlib.h>



/*
  TAD: Pilha

  int vetor [ CAPACIDADE_MAXIMA ];
     - Aqui básicamente é onde iremos empilhar
     - nossos valores. 

  int topo; 
     - Aqui é o índice de posicionamento na 
     - pilha, ou seja, o topo;
*/
typedef struct
{
       int vetor [ CAPACIDADE_MAXIMA ];
       int topo;
}
Pilha;


/*
  FUNC: Esta função é uma inicializadora de dado tipo Pilha
        atráves de um dado retornado.
  ---
  S/@PARAM
  ---
  RETURN: Uma pilha criada é retornada.
*/
Pilha init_Pilha ( void )
{
     // Inicializando a pilha diretamente
     Pilha nova_pilha = { { 0 } , -1 };

     // Retornando a pilha criada
     return nova_pilha;
}


/*
  FUNC: Esta função é uma inicializadora de dado tipo Pilha
        atráves de referência direta.
  ---
  @PARAM1: Um ponteiro de dado Pilha.
  ---
  RETURN: nada é retornado.
*/
void new_Pilha ( Pilha * pilha ) 
{
    // Modificando a pilha que foi referênciada
    pilha -> topo = VAZIA; 
}


/*
  FUNC: Esta função faz a inserção de um valor na Pilha.
  ---
  @PARAM1: Um ponteiro de dado Pilha.
  @PARAM2: Um valor do tipo inteiro.
  ---
  RETURN: nada é retornado.
*/
void push ( Pilha * pilha , int valor )
{
    // se a pilha está cheia NÃO adicione!
    if ( pilha -> topo == CHEIA )
    {
      printf ( "\n* A pilha está cheia, libere espaço se quiser adicionar algo!\n\n" );
      system ( "pause" );
      return;   
    }
   
    // Inserção direta na pilha
    pilha -> vetor [ ++ pilha -> topo ] = valor;
    printf ( "\n* Adicionado no índice da pilha %d o valor [ %d ]\n\n" , pilha -> topo , pilha -> vetor [ pilha -> topo ] );
    
    // Pausa
    system ( "pause" );
}


/*
  FUNC: Esta função faz a remoção de um dado da Pilha.
  ---
  @PARAM1: Um ponteiro de dado Pilha.
  ---
  RETURN: nada é retornado.
*/
void pop ( Pilha * pilha )
{ 
    // se a pilha está vazia NÃO remova! 
    if ( pilha -> topo == VAZIA )
    {
      printf ( "* A pilha está vazia, adicione algo para depois remover!\n\n" );
      system ( "pause" );
      return;  
    }
    
    // Remoção de valor da pilha
    printf ( "\n* Removido do índice %d da pilha o valor [ %d ]\n\n" , pilha -> topo , pilha -> vetor [ pilha -> topo ] );
    pilha -> topo --;

    // Pausa
    system ( "pause" );
}


/*
  FUNC: Esta função faz um print da Pilha.
  ---
  @PARAM1: Um ponteiro de dado Pilha.
  ---
  RETURN: nada é retornado.
*/
void print_Pilha ( Pilha * pilha )
{
    // Print do estado da pilha
    printf ( "\n- Estado da pilha:     " );
    if ( pilha -> topo == VAZIA )      printf ( "Vazia\n" );
    else if ( pilha -> topo == CHEIA ) printf ( "Cheia\n" );
    else                               printf ( "Ocupada\n" );
    
    // Print da capacidade da pilha
    printf ( "- Capacidade da pilha: %d\n" , CAPACIDADE_MAXIMA );   
    
    // Print do topo da pilha
    printf ( "- Topo da pilha:       %d" , pilha -> topo );   
    
    // Print dos elementos na pilha
    printf ( "\n- Elementos na Pilha:  [ " );
    for ( int i = 0 ; i < CAPACIDADE_MAXIMA ; i ++ ) printf ( "%d " , pilha -> vetor [ i ] );
    printf ( "]\n\n" );

    // Pause
    system ( "pause" );
}


/*
  FUNC: Esta função limpa tela com base no sistema
       operacional.
  ---
  s/@PARAM
  ---
  RETURN: nada é retornado.
*/
void clear ( void )
{
    # ifdef _WIN32
    system ( "cls" );
    # elif _WIN64
    system ( "cls" ); 
    # else
    system ( "clear" );
    # endif 
}


int main ()
{   
   // Use isso para permitir acentuação no seu console
   // caso esteja usando windows, senão estiver remova  
   system ( "CHCP 65001 > nul" ); 

   // Declaração e inicialização da Pilha
   Pilha pilha = init_Pilha ();

   // Variáveis de suporte
   int user_input = 0;
   int user_push = 0;

while ( 1 )
{
     // Limpa a tela - caso seu local de teste não
     // tenha compatibilidade com limpeza de tela
     // remova!
     clear ();

     // Print do Menu Interativo + input
     printf 
     (
           "[ TESTE DE PILHA ESTÁTICA ]\n\n"
           "1 - Mostrar Pilha.\n"    
           "2 - Adicionar um valor.\n"    
           "3 - Remover um valor.\n"    
           "4 - Encerrar aplicação.\n\n"    
           "--> O que deseja fazer: "
     );
     scanf ( "%d" , &user_input );
     setbuf ( stdin , NULL );
   
     // Gerenciando a escolha do usuário com switch
     // para simplificar o processo de checagem
     switch ( user_input )
     {
           // Mostrar as informações da pilha
           case 1: 

               print_Pilha ( &pilha );
         
           break;
        
           // Execução da função PUSH
           case 2: 

               printf ( "\n- Qual valor você deseja adicionar: " );
               scanf ( "%d" , &user_push );
               setbuf ( stdin , NULL );
             
               push ( &pilha , user_push );

           break;
         
           // Execução da função POP
           case 3: 
             
               pop ( &pilha );      

           break;
         
           // Usuário está encerrando a aplicação
           case 4: 
         
               clear ();
               printf ( "- Obrigado por testar essa aplicação\n" );
               exit ( 0 );

           break; 
   }
}
}
```

# Pilha Dinâmica

### Implementação
```main.c
# include <stdio.h>
# include <stdlib.h>

// Definição da estrutura do nó da pilha
typedef struct Node
{
       int valor;         // Dado a ser armazenado
       struct Node* next; // Ponteiro para o próximo nó
}
Node;

// Definição da estrutura da pilha
typedef struct Stack {
    Node* top;  // Ponteiro para o topo da pilha
} Stack;

// Função para criar um novo nó
Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node)); // Aloca memória para o novo nó
    if (newNode == NULL) {
        printf("Erro: Não foi possível alocar memória.\n");
        exit(EXIT_FAILURE);
    }
    newNode->data = data; // Define o dado do novo nó
    newNode->next = NULL; // Inicializa o próximo como NULL
    return newNode;
}

// Função para inicializar a pilha
Stack* createStack() {
    Stack* stack = (Stack*)malloc(sizeof(Stack)); // Aloca memória para a pilha
    if (stack == NULL) {
        printf("Erro: Não foi possível alocar memória.\n");
        exit(EXIT_FAILURE);
    }
    stack->top = NULL; // Inicializa o topo da pilha como NULL (pilha vazia)
    return stack;
}

// Função para verificar se a pilha está vazia
int isEmpty(Stack* stack) {
    return (stack->top == NULL); // Retorna 1 se a pilha estiver vazia, senão retorna 0
}

// Função para empilhar um elemento na pilha
void push(Stack* stack, int data) {
    Node* newNode = createNode(data); // Cria um novo nó com o dado fornecido
    newNode->next = stack->top; // Define o próximo do novo nó como o antigo topo da pilha
    stack->top = newNode; // Define o novo nó como o topo da pilha
}

// Função para desempilhar um elemento da pilha
int pop(Stack* stack) {
    if (isEmpty(stack)) {
        printf("Erro: Pilha vazia, não é possível desempilhar.\n");
        exit(EXIT_FAILURE);
    }
    int data = stack->top->data; // Armazena o dado do topo da pilha
    Node* temp = stack->top; // Armazena o topo da pilha em um nó temporário
    stack->top = stack->top->next; // Atualiza o topo da pilha para o próximo nó
    free(temp); // Libera a memória do nó desempilhado
    return data; // Retorna o dado desempilhado
}

// Função para visualizar o elemento no topo da pilha
int peek(Stack* stack) {
    if (isEmpty(stack)) {
        printf("Erro: Pilha vazia, não há elementos para visualizar.\n");
        exit(EXIT_FAILURE);
    }
    return stack->top->data; // Retorna o dado do topo da pilha
}

// Função principal
int main() {
    Stack* stack = createStack(); // Cria uma nova pilha

    // Empilhando alguns elementos
    push(stack, 10);
    push(stack, 20);
    push(stack, 30);

    // Visualizando o elemento no topo da pilha
    printf("Elemento no topo da pilha: %d\n", peek(stack));

    // Desempilhando um elemento
    printf("Elemento desempilhado: %d\n", pop(stack));

    // Visualizando o elemento no topo da pilha após a desempilhamento
    printf("Elemento no topo da pilha: %d\n", peek(stack));

    // Liberando a memória da pilha
    free(stack);
}
```

<h3 align="center"> <a href="#pilhas" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

