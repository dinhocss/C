# Importância da linguagem C

A linguagem C segue um paradigma imperativo e estruturado, onde o programador lida diretamente com os aspectos de alocação de memória e controle do fluxo do programa. Podemos destacar algumas características a respeito dessa linguagem, sendo elas:

- **Imperativas**: O código é escrito como uma sequência de instruções que modificam o estado do programa.
- **Gerenciam memória explicitamente**: O programador precisa alocar e liberar memória manualmente.
- **Baixo nível de abstração:** O acesso à memória e aos recursos do hardware é mais direto, permitindo um maior controle e eficiência sobre os dados, porém a programação torna-se mais complicada.

## Organização de um computador

Pelo fato da linguagem C ser de baixo nível, é importante conhecer um pouco sobre como o computador funciona. A imagem abaixo representa os principais componentes de um computador, onde eles se comunicam via um canal de comunicação chamado BUS:

![image](https://github.com/user-attachments/assets/5f9c44f4-e735-48af-a76c-67384832f667)

A CPU é o cérebro do computador. Nela são realizadas as operações sobre os dados. A CPU pode se comunicar diretamente com a memória principal. A memória principal é uma memória volátil, ou seja, quando o programa é fechado todo conteúdo da memória será perdido. Uma outra característica da memória é que ela é randômica. Todo programa é armazenado na memória secundária, que pode ser um HD ou um SSD. Ao abrirmos um programa, a memória principal resgata partes desse programa que serão importantes para sua execução, e conforme o programa for rodando, essas partes podem entrar ou sair da memória principal. Já dispositivos de entrada e saída são dispositivos que permitem enviar dados para a CPU ou resgatar dados da CPU.

## Armazenando dados e programas na memória

O computador só processa valores de 0 e 1. Esses valores são mapeados de acordo com a necessidade do programador, de modo que uma ação pode ser associada a determinado byte. Para processar texto, temos um mapeamento feito de acordo com a tabela ASCII, onde cada letra representa um número. Por exemplo, o número 65 (01000001) quando definido como inteiro pelo programa, representa o próprio número. Porém, se definirmos a variável que armazena 65 como char, ela associará a letra A. 

**OBS:** Cada endereço de memória é associado com 1 byte (8 bits). Cada bit armazena somente 0 ou 1. Portanto, para cada byte, temos 2^8 possibilidades de números diferentes, que vão de 0 a 255.

## Compilação de programas

Os processadores não entendem diretamente instruções de alto nível, como é o caso da linguagem C. Portanto, é necessário ter um compilador que será responsável por transformar as instruções dadas por um código-fonte em C. O compilador irá traduzir o código para uma linguagem no qual o processador consegue entender, isto é, em valores binários que são representados por 1 ou 0. Quando um compilador cria um programa objeto, esse programa contém as instruções no qual o sistema operacional será responsável por alocá-los na memória, e assim possibilitando o processador de ler essas instruções. Um esquema de como ocorre essas operações é dado abaixo:

![image](https://github.com/user-attachments/assets/64c4bcd4-db27-426d-a9ce-215f9d47a4e4)

**OBS**: O processador entende apenas operações, atribuições, entre outros. Ele não entende diretamente o que os dados significam. Os sinais elétricos são responsáveis pela parte física da execução das instruções.

## Algumas outras características

Um programa em C é exemplificado abaixo:
```
#include <stdio.h>

float converte(float c){
	float f;
	f = 1.8*c + 32;
	return f;
}

int main(void){
	float t1;
	float t2;
	
	printf("Digite a temperatura em Celsius:");
	scanf("%f, &t1);
	t2 = converte(t1);
	printf("Temperatura em Fahrenheit: %f\n",t2);
	return 0;
}
```

Os programas em C são feitos por diversas pequenas funções, e cada função pode ter suas próprias variáveis, sendo essas variáveis locais, que só funcionam no escopo da função. A variável f criada dentro da função converte é um exemplo de variável local. O mesmo ocorre com as variáveis t1 e t2, que só funcionarão no escopo da função main. 
**OBS**: Podemos inserir comentários através de /*comentário*/.

A função main é a principal função. O código é compilado a partir dessa função, e a partir dai as outras funções vão sendo chamadas e executadas.

Para escrever programas em C precisamos de um editor de texto e um compilador. O editor de texto será responsável por criar as instruções do programa e terá o formato .c. Após o compilador traduzir as instruções para linguagem de máquina será gerado um arquivo com o formato tipo o, que é o código-objeto. Esse código-objeto é transformado em um executável através dos ligadores. Quando o executável é aberto, o programa é carregado para a memória, permitindo que o processador acesse essas instruções.

