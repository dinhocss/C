# Variáveis

> Uma variável representa um espaço na memória que é utilizado para armazenar determinado tipo de dado.

Para declararmos uma variável precisamos indicar seu tipo (int, float, etc.) e o seu nome. Quando definimos um tipo, estamos alocando na memória espaço suficiente para caber determinado tipo. Por exemplo, ao declararmos um float, será criado um espaço na memória de 4 bytes, que será associado a esse float. O nome dado é utilizado como referência, e ele representa o endereço criado para a variável.

## Tipos básicos

A linguagem C oferece alguns tipos básicos. Para armazenar valores inteiros podemos ter *char*, *short int*,*int,* e *long int*.
Segue abaixo uma tabela que indica os valores e quantos valores possíveis podem estar associados a eles:
|Tipo|Tamanho|Representatividade|
|---|---|---|
|char|1 byte|-128 a 127|
|unsigned char|1 byte|0 a 255|
|short int|2 bytes|-32.768 a 32.767|
|unsigned short int|2 bytes|0 a 65.535|
|long int|4 bytes|-2.147.483.648 a 2.147.483.647|
|unsigned long int|4 bytes|0 a 4.294.967.295|
|float|4 bytes||
|double|8 bytes||

# Operadores

## Operadores aritméticos

> São dados por ‘+’, ‘-’, ‘/’, ‘*’ e ‘%’. Sendo este último o resto da divisão dada entre dois operandos.

Os operadores aritméticos são padrões, tendo soma, subtração, multiplicação, divisão e módulo. Esses operadores podem realizar operações sobre números inteiros ou de ponto flutuante, portanto, dependendo da divisão o resultado pode ser diferente. Por exemplo, se atribuirmos uma variável *float a = 1/2*, a divisão será feita entre dois valores inteiros, resultando em um valor inteiro. Ou seja, apesar do resultado real ser 0.5, o resultado guardado por a será 0, que é a parte inteira. Sendo assim, para evitar esse tipo de problema, quando definimos uma variável precisamos ajustá-la, de modo que *float a = 1.0/2.0* faz a divisão de maneira correta.

**OBS:** O operador módulo age sobre dois números inteiros e pode ser usado para verificação de paridade de um número.

## Operadores de atribuição

É dado pelo símbolo ‘=’, e atribui um valor a uma variável. Por exemplo, x = 5 atribui o valor 5 à variável x. Podemos também utilizar os operadores de atribuição compostos, que são da forma **i = i + 2**, podendo ser compactado em i += 2. 

**OBS:** Os operadores de atribuição compostos podem ser utilizados com diferentes tipos de operadores, como i*=2, i-=2, etc.

Uma outra consideração a ser levada em conta é que a expressão dada após o = é envolvida com parênteses. Por exemplo, quando temos **x*=y+1**, na verdade temos **x = x * (y+1)**, e não **x = x*y+1**, pois o resultado seria diferente.

## Operadores de incremento e decremento

É um operador unário que serve para incrementar ou decrementar uma unidade nos valores armazenados nas variáveis. Geralmente, utilizamos a notação a++ ou ++a, onde a diferença entre eles é o uso da variável a antes (a++) de ser incrementada ou depois (++a) de ser incrementada. Por exemplo, considere o seguinte caso:

```
int a = 3;
int b = a++ * 2;
```
A variável a recebe 3 em um primeiro momento. Após isso, a variável b é inicializada e utiliza o valor de a (3) para realizar a operação. O resultado é 6, e a variável a é incrementada de 3 para 4. Valores finais: a = 4; b = 6.

Agora considere o seguinte caso:
```
int a = 3;
int b = ++a * 2;
```
No exemplo acima, a variável b primeiramente incrementa o valor de a e após isso realiza a operação. Valores finais: a = 4; b = 8.

**OBS:** No exemplo acima, a variável b primeiramente incrementa o valor de a e após isso realiza a operação. Valores finais: a = 4; b = 8.

## Operadores relacionais e lógicos

### Operadores relacionais

Os operadores relacionais são utilizados para comparar dois valores. Os seguintes operadores relacionais são utilizados em C:
|Operador|Descrição|
|---|---|
|<|menor que|
|>|maior que|
|<=|menor ou igual a|
|>=|maior ou igual a|
|==|igual a|
|=!|diferente de|

**OBS**: Em C não temos o tipo booleano indicando verdadeiro ou falso. A verificação é feita através de 0, que simboliza falso, e através de qualquer outro valor diferente de 0, que simboliza verdadeiro. O retorno dos operadores relacionais é 0 ou 1.

### Operadores lógicos

Os operadores lógicos servem para combinar expressões booleanas. A linguagem C oferece os seguintes tipos de operadores lógicos:
|Operador|Descrição|
|---|---|
|&&|Operador binário E(AND)|
|\|\||Operador binário OU(OR)|
|!|Operador unário de negação(NOT)|

**OBS**: Recomenda-se o uso de parênteses em expressões que combinem operadores lógicos e relacionais.

## Operador sizeof e conversão de tipo

O operador sizeof nos fornece o número de bytes de determinado tipo. Por exemplo, se quisermos saber o número de byte que o tipo float possui, podemos utilizar a seguinte expressão: `int a = sizeof(float)`

A expressão acima retorna o valor 4, que é o número de bytes que o tipo float possui.

Já a conversão do tipo é utilizada quando queremos converter determinado valor explicitamente para um outro tipo. Isso é feito através do operador *cast*. Por exemplo, são válidos:
```
int a, b;
a = (int)3.5;
b = (int)3.5 % 2;
```

# Entradas e saídas básicas

> A linguagem C não possui comandos de entrada e saída padrão. Para utilizá-los é necessário importar a biblioteca <stdio.h>

Além dos comandos permitindo entrada e saída de dados, a biblioteca stdio.h possui diversas outras funções, como funções matemáticas, funções para manipulação de cadeia de caracteres, entre outros. 

## Função printf

A função printf permite a saída de valores (constantes, variáveis ou resultados de expressões). Geralmente, a forma da função é dada por: **printf(”formato”, lista de constantes, variáveis, expressões);**

O primeiro parâmetro, denominado formato, informa o tipo de saída das constantes, ou variáveis. Dependendo do tipo de variável, teremos um tipo diferente de caractere que representa o valor desejado. Os tipos são:
|Formato|Descrição|
|---|---|
|%c|Especifica um char|
|%d|Especifica um int|
|%u|Especifica um unsigned int|
|%f|Especifica um double (ou float)|
|%e|Especifica um double (ou float) no formato científico|
|%g|Especifica um double (ou float) no formato mais apropriado| 
|%s|Especifica uma cadeia de caracteres|

Alguns outros caracteres especiais são utilizados no formato da saída, sendo eles:
| Caracteres | Descrição               |
|------------|-------------------------|
| `\n`       | Caractere de nova linha  |
| `\t`       | Caractere de tabulação   |
| `\r`       | Caractere de retrocesso  |
| `\"`       | O caractere `"`          |
| `\\`       | O caractere `\`          |
| `%%`       | O caractere `%`          |

**OBS**: Podemos definir o numero de casas decimais adicionando um .(n° de casas). Por exemplo, %.2d exibirá algo com precisão de 2 casas decimais.

## Função scanf

Permite capturar valores fornecidos via teclado e guardá-los em variáveis. Sua forma geral é dada por: `scanf(formato, lista de endereços das variáveis…);`

O formato deve conter especificadores já citados anteriormente, porém com distinção entre o tipo float e double. Segue abaixo uma tabela representando os tipos possíveis de formatos:
|Formato|Descrição|
|---|---|
|%c|Especifica um char|
|%d|Especifica um int|
|%u|Especifica um unsigned int|
|%f, %e, %g|Especifica um float|
|%lf, %le, %lg|Especifica um double|
|%s|Especifica uma cadeia de caracteres|

Além de indicar o formato, precisamos também indicar o endereço da variável. Isso é feito para podermos atribuir o valor inserido pelo usuário à variável definida anteriormente. Por exemplo:

```
int n;
scanf("%d",&n);
```

O código acima irá receber um valor inteiro do usuário (%d especifica um inteiro), e o valor será guardado na variável dada pelo endereço de n (n é um endereço de memória que guarda 4 bytes para possibilidade de valores).





