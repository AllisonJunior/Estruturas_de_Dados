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

**Apesar da analógia não ser tão perfeita, a ideia de pilha é basicamente essa, você irá estacar / empilhar <a href="Pilhas.md" title="valores do tipo inteiro, strings, números reais e até mesmo dados de dados">**dados**</a>** de tal forma que sempre que você desejar acessar uma posição específica caso esteja abaixo de alguma outra, essa outra terá que ser removida da pilha, com o objetivo de acessar aquele dado específico. 

# Pilha Estática

# Pilha Dinâmica


