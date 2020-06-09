# Resumo-Aloca-o-Pilhas-e-Listas

Alocação de Memória

Alocação de memória é um passo crucial para que um programa seja executado. Logo em sua execução, o programa inicia a requisição de memória ao SO para que possa ser executado. Por vezes a requisição inicial torna-se insuficiente durante a execução, então o programa faz nova alocação.
Em C existem as alocações estática e dinâmicas de memória.

Na alocação estática, as reservas de memória são efetuadas durante a compilação e, portanto não podem ser alteradas durante sua execução.
Este tipo de alocação é efetuado quando se sabe antecipadamente a quantidade de memória que será utilizada para cada tipo de variável.

Já na alocação dinâmica, a definição do espaço a ser utilizado pelas variaveis é definido durante a execução, ou seja, ocorre quando não se tem pré-definido a memória necessaria para a execução do programa e este ocorre a medida em que houver necessidade.

Em C temos 4 principais funções padrão para a alocação dinâmica da memória:
Malloc()
Calloc()
Realloc()
Free()

Sendo malloc() e free() as mais utilizadas. Todas pertencem a biblioteca <stdlib.h>.

Malloc()
Sua sintaxe é definida da seguinte forma:
void *malloc(size_t num_bytes);

Onde:
num_bytes representa a quantidade que se deseja alocar;
syze_t corresponde a um inteiro
Na sintaxe retorna um ponteiro de tipo void, que pode ser atribuido a qualquer tipo de ponteiro.

Exemplo:
int *vetor; //definido o tipo e o ponteiro
vetor = malloc(10); //aloca a memoria dinamicamente de 10 bytes

Desta forma a biblioteca C recebe memoria de uma reserva livre (não utilizada) denominada HEAP.

A partir do ponteiro do tipo void, precisamos converter (cast) para o tipo desejado e alocar um espaço determinado como destino. Portanto precisa seguir a seguinte forma:

vetor = (int *) malloc (10*sizeof(int));//converte para o tipo int e alocará o tamanho do parametro informado

Para verificar se a Heap possui memória disponivel e assim evitar problemas podemos fazer o seguinte teste:

vetor = (int *) malloc (10*sizeof(int));
if(vetor == NULL){
  printf("Memória insuficiente para alocação");
  exit(1);
}

Ocorre que nas situações onde o malloc não conseguir alocação de memória na Heap, retornara NULL como indicativo de negação da alocação. Em caso positivo, retornará o ponteiro para a memória alocada.

Free()
A função free() possui sintaxe:
void free (void *ptr);

Nas circunstancias em que o programa não necessita mais de memória alocação pelo malloc, esta função deve ser utilizada para liberação do espaço reservado.
Na sintaxe acima, ptr corresponde ao ponteiro da memória a ser liberada.

Alocações estaticas, portanto, são definidas durante a compilação quando ja se tem ideia do espaço que irão ocupar e as dinâmicas ocorrem durante sua execução.
O tipo de reserva estatica tem por vantagem a organização da memoria uma ao lado do outro de forma linear e sequencial o que facilita a localização e manipulação, mas precisa ser previamente definido o tamanho, o que pode resultar em espaço sub utilizado ou o estouro da memória (stackoverflow). 

Já com a alocação dinâmica, seu uso é feito durante a execução e tem-se a quantidade necessaria, o que permite otimizar o uso da memória. Seu uso como descrito anteriormente é a partir de funções de alocação e liberação da memória.

Pilhas

Uma pilha é uma estrutura de dados onde se pode inserir e remover objetos. A pilha possui definição de uso de regra que sempre que houver uma remoção, esta sera a que esta a menos tempo na estrutura. Ou seja, segue a relação LIFO (Last In First Out), onde o primeiro objeto da estrutura é o ultimo a ser removido.
Para remover um elemento, ou desempilhar, a operação é chamada "pop".
Logo, para se inserir um elemento, a operação é "push".

Listas

Uma lista é uma sequencia de objetos todos do mesmo tipo que são armazenados em sequencia. As listas possuem o endereço da proxima célula (ou nó) para o objeto subsequente, então denomina-se a lista como encadeada. Tem se a impressão de que a alocação ocorre em posições consecutivasa, porém, as alocações são efetuadas de forma espalhada, mas com o registro do endereçamento para acesso pela aplicação. Uma lista esta vazia se o endereçamento é = NULL.
Em uma lista a primeira célula é conhecida por cabeça (head), seguido por seu conteúdo e seguido pelo ponteiro para o próximo nó da lista. 
