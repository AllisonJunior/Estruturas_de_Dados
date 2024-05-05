# Pilhas

A linguagem de programação C não possui uma forma padrão de se implementar <a href="Pilhas.md" title="uma coleção linear de elementos vulgo stack">**pilhas**</a>, que seguem o princípio de <a href="Pilhas.md" title="Last In, First Out: o último elemento inserido é o primeiro a ser removido.">**LIFO**</a>, por isso utilizamos um <a href="Pilhas.md" title="Tipo Abstrato de Dado: Struct">**TAD**</a> para chegar a esse resultado, utilizando um modelo de implementação estática ou dinâmica. Portanto abaixo teremos a demonstração de implementações base dessas duas formas de implementação e claro alguns exemplos de utilização, junto a um pequeno sumário abaixo para melhorar sua navegação pela página.

- <a href="#introdução" title="Introdução a pilhas">**Introdução**</a>
- <a href="#pilha-estática" title="Introdução a pilhas estáticas">**Pilha Estática**</a>
- <a href="#pilha-dinâmica" title="Introdução a pilhas dinâmicas">**Pilha Dinâmica**</a>

--- 

# Introdução

A ídeia de pilhas como já discutido anteriormente, consiste no príncipio de <a href="Pilhas.md" title="Last In, First Out: o último elemento inserido é o primeiro a ser removido.">**LIFO**</a>, portanto na sua implementação seja para qualquer tipo de <a href="Pilhas.md" title="uma coleção linear de elementos vulgo stack">**pilha**</a> ( *inteiro*, *caractere*, *string* ) e forma de alocação ( *estática* ou *dinâmica* ), iremos seguir a seguinte ideia: 

**Suponhamos um livro "LIVRO 0", como na imagem abaixo:**

![STATE_1](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/c29de8e6-9b40-46dc-adec-41f2b90d7360)

**Como se pode ver, ele está sozinho e caso eu desejasse o pegar não teria complicação alguma, mas vamos supor que eu empilhei outro livro em cima do "LIVRO 0" no caso o "LIVRO 1", como dá para ver abaixo:**

![STATE_2](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/73e961b0-67a8-41cc-b764-42bb60875c2c)

**Agora temos 2 livros empilhados! Mas vamos supor novamente que eu comprei outro livro "LIVRO 2" e decidi empilhar ele, teríamos o seguinte:**

![STATE_3](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/7dc0ca73-1b32-4b65-b506-d4881f3745cc)

**Como dá para ver empilhamos 2 livros em cima do "LIVRO 0", mais e aí como eu faço para pegar ele? Eu preciso remover todos os livros que estão em cima dele!**

***1º PASSO - Desejo retirar o "LIVRO 0"***

![STATE_3](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/7dc0ca73-1b32-4b65-b506-d4881f3745cc)

***2º PASSO - Retiro o "LIVRO 2" de cima do "LIVRO 1" pois ele está em cima:***

![STATE_2](https://github.com/AllisonJunior/Estruturas_de_Dados/assets/114815898/73e961b0-67a8-41cc-b764-42bb60875c2c)

***3º PASSO - Retiro o "LIVRO 1" de cima do "LIVRO 0". Assim conseguimos acessar o "LIVRO 0"!***

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

# Pilha Estática

### Implementação
```main.c
```

# Pilha Dinâmica
```main.c
```

<h3 align="center"> <a href="#pilhas" title="Voltar ao topo"> Retornar ao topo </a> </h3>
<h3 align="center"> <a href="https://github.com/AllisonJunior/Estruturas_de_Dados" title="Voltar ao menu principal"> Retornar a página principal </a> </h3>

