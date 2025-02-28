> Controle de fluxo permite a manipulação do fluxo de execução do programa, baseado em estruturas auxiliares, como decisões condicionais (if-else e switch), laços de repetição(for e while) e comandos de controle (break e continue)

# Tomada de Decisão

## if/elseif/else

O comando if é o comando básico para codificar uma tomada de decisão em C. Seu escopo pode ser dado por:

```
if(expressao){
	bloco de comando 1;
}else{
	bloco de comando 2;
}
```

Para simbolizar o escopo que o comando if terá, delimitamo-nos através do uso de chaves { }. Porém, se houver apenas uma linha de comando, o uso de chaves pode ser dispensado. Outra coisa a ser levado em consideração é que podemos ter mais de dois blocos apenas. Caso a gente precise escolher entre mais de um bloco de comando, podemos utilizar o comando else if. Segue abaixo dois exemplos completos utilizando if-else e if-else if-else:

```
#include <stdio.h>

void parOuImpar(int numero){
    if(numero%2==0)
        printf("%d é par",numero);
    else
        printf("%d é ímpar",numero);
}

int main()
{
    parOuImpar(32);
    return 0;
}
```

No exemplo acima nós criamos uma função que recebe um número como parâmetro e retorna uma mensagem diferente, baseando-se na paridade do número. Note que não utilizamos { } para delimitar o escopo do if-else, pois só há uma linha de comando.

```
#include <stdio.h>

void quenteOuFrio(int temperatura){
    if(temperatura<20){
        printf("Muito frio!");
    }else if(temperatura >= 20 && temperatura < 30){
        printf("Agradável!");
    }else{
        printf("Muito quente!");
    }
}

int main()
{
    quenteOuFrio(2144);
    return 0;
}
```
No exemplo acima utilizamos um bloco else-if, intermediário entre o if e else. Podemos ter quantos blocos else-if forem necessários.

### Operador condicional

Um operador condicional pode ser utilizado no lugar de blocos if-else, de modo a tornar o código mais compacto. O escopo de um operador condicional é dado por: *condição ? expressão 1: expressão 2;*

Segue abaixo um exemplo da comparação entre dois números, tendo como retorno o maior número:
```
int maior(int a, int b){
    int maior = (a>b)?a:b; /*Aqui verifica-se se a>b, se sim (a expressão é 0) retornamos a, senão retornamos b*/
    return maior;

}

int main()
{
    printf("Maior:%d",maior(4131,31134));
    return 0;
}
```

## Seleção

>Seleciona um valor dentro de um conjunto de valores possíveis.

O escopo da estrutura de seleção (switch) é dado por:
```
switch(expressao){
	case 1:
		/*bloco_de_comando se expressão == 1*/
		break;
	case 2:
		/*bloco_de_comando se expressão == 2*/
		break;
	case 3:
		/*bloco_de_comando se expressão == 3*/
		break;
	default:
		/*bloco_de_comando se não for nenhuma das opções acima*/
		break;
}
```

Para exemplificar o uso da estrutura switch segue uma mini calculadora que recebe dados do usuário e exibe um menu, possibilitando-o realizar operações matemáticas básicas:

```

#include <stdio.h>

void menu(int a, int b){
    printf("Bem vindo ao Claudio Calculador\n");
    printf("Os valores selecionados são %d e %d\n",a, b);
    printf("1 - Somar\n2 - Subtrair\n3 - Multiplicar\n4 - Dividir\n5 - Exibir menu\n0 - Sair\n");
}

void calculadora(int a, int b){
    int op = 1;
    menu(a,b);
    while(op!=0){
        printf("Digite a opção desejada:");
        scanf("%d",&op);  
        
    switch(op){
        case 1:
            printf("\nSomando %d + %d = %d\n",a,b,a+b);
            break;
        case 2:
            printf("\nSubtraindo %d - %d = %d\n",a,b,a-b);
            break;
        case 3:
            printf("\nMultiplicando %d x %d = %d\n",a,b,a*b);
            break;
        case 4:
            if(b==0){
                printf("\nDivisão por 0 é impossível");
                break;
            }
            printf("\nDividindo %d/%d = %d\n",a,b,a/b);
            break;
        case 5:
            menu(a,b);
            break;
        default:
            printf("Digite uma opção válida.\n");
            break;
    }    
    }
    
}


int main()
{   
    int a, b;
    printf("Digite os valores de a e b:");
    scanf("%d %d",&a,&b);
    calculadora(a,b);
    return 0;
}
```

**OBS**: É necessário utilizar o break, pois caso contrário o código continuará executando no próximo case.

# Construções com laços

> Permite que um determinado bloco de código seja executado em um número definido de vezes.

## Laço while

O escopo do laço while é dado por:
```
while(expressao booleana){
	bloco-de-codigo;
	expressão de incremento;
}
```

O bloco while será executado enquanto a expressão for verdadeira, portanto é necessário tomar cuidado para não criar loopings infinitos. Geralmente utiliza-se uma condição de parada que vai analisar se o bloco de código ainda deve ser executado. 

Segue abaixo um exemplo da utilização do laço while através de uma função que calcula o fatorial de um número:

```
#include <stdio.h>

int fatorial(int n){
    int total = 1;
    while(n>0){
        total = total*n;
        n--;
    }
    return total;
}
int main()
{
    int total;
    total = fatorial(4);
    printf("%d",total);
    return 0;
}
```

## Laço for

O escopo do laço for é dado por:

```
for(expressao inicial;expressão booleana;expressão de incremento){
	bloco de comando;
}
```

No caso do laço for não há a necessidade de se preocupar com as expressões de incremento, uma vez que elas estão dentro das expressões necessárias para a função for.

Segue abaixo o mesmo exemplo de fatorial, porém agora utilizando o laço for:

```
#include <stdio.h>
void fatorial(int n){
    int total = 1;
    printf("%d! = ",n);
    for(int i=n;i>0;i--){
        total = total*i;
        if(i==1){
            break;
        }
        printf("%d x ",i);
    }
    printf("1 = %d",total);
}

int main()
{
    fatorial(5);
    return 0;
}
```

**OBS**: Tanto o laço for quanto o laço while analisam a expressão booleana antes da execução do bloco de código. Por exemplo, se o exemplo acima resultasse falso na expressão booleana i>0, o bloco de código não seria executado nenhuma vez.

## Laço do-while

O laço do-while é utilizado quando queremos que o bloco de código execute antes da verificação da expressão booleana. Seu escopo é dado por:

```
do{
	bloco_de_codigo;
}while(expressão_booleana);
```
Neste caso, o bloco de código sempre será executado ao menos uma vez, já que a expressão booleana é verificada ao final do bloco. Segue abaixo um exemplo do cálculo de fatorial, agora levando em consideração do laço do-while:

```

#include <stdio.h>

void fatorial(int n){
    int total = 1;
    int i = n;
    printf("%d! = ",n);
    do{
        total = total*i;
        if(i==1){
            break;
        }
        printf("%d x ",i);
        i--;
    }while(i>0);
    printf("1 = %d",total);
}

int main()
{
    fatorial(5);
    return 0;
}
```

## Interrupções com Break e Continue

São palavras-chave utilizadas para modificar o fluxo de um código. A maior diferença entre elas é que quando utilizamos *break* nós interrompemos o laço atual e executamos o código logo após o laço. Já *continue* interrompe apenas o fluxo atual do código, porém o bloco dentro do laço continua sendo executado. 

Segue abaixo duas funções que exemplificam o uso de break e continue, explicitando suas diferenças:

```

#include <stdio.h>

void testandoBreak(){
    int a=0;
    while(a<10){
        printf("%d ",a);
        a++;
        if(a==5){
            break;
        }
    }
}

void testandoContinue(){
    int a = 0;
    while(a<10){
        if(a==5){
            a++;
            continue;
        }
        printf("%d ",a);       
        a++;
    }
}

int main()
{
    testandoBreak();
    printf("\n");
    testandoContinue();
    return 0;
}
```

A primeira função testandoBreak imprime a saída “0 1 2 3 4”. Isso por que quando i = 5 o laço é interrompido e o código continua após o laço. Já na função testandoContinue, a saída impressa será “0 1 2 3 4 6 7 8 9”. Isso ocorre pois quando i = 5, teremos um continue, fazendo com que somente aquela iteração seja desconsiderada, enquanto as outras serão executadas normalmente. 








