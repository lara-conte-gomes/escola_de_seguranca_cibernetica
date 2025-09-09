# PicoCTF - Questão 3
## _Feito por: Lara Conte Gomes_

## Questão 3
A terceira questão chama 'interencdec', [link da questão](https://play.picoctf.org/practice/challenge/418). 

![Questão 3](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture18.png?raw=true) 

Nela tem um link que, quando se clica nele, baixa um arquivo.

![Documento baixado](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture19.png?raw=true)  

Ao abrir o arquivo, encontrei uma string.

> YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==

Reconheci, pelo final dele, que devia decodificá-lo com a Base64.
Abrir o site que decofica em Base64 e coloquei a string lá.

![Print site](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture20.png?raw=true)   

Depois eu recebi uma nova string:

> b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='

Com a ajuda do ChatGPT, descobri que deveria retirar o ' b'' ', pois é apenas uma notação em Python indicando que a variável é do tipo bytes.

Coloquei a nova string novamente na Base64.

![Print site2](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture21.png?raw=true)    

E recebi: wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}
Novamente, com a ajuda do ChatGPT, descobri que poderia decodificá-lo com a Cifra de César, pois a flag estava começando a ficar no formato desejado.

#### _O que é Cifra de César?_
É um antigo e simples método de criptografia, onde, cada letra de uma mensagem, é substituída por uma outra letra que encontra-se em um número fixo de posições na frente ou atrás no alfabeto.

Utilizando da imagem abaixo, descobri que o deslocamento devia ser 7.

![Cifra de Cesar](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture23.png?raw=true)  

![Cifra de Cesar site](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture22.png?raw=true)  

Fazendo isso, descobri a flag e resolvi a questão 3.

> picoCTF{caesar_d3cr9pt3d_78250afc}

![Resolução Questão](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture24.png?raw=true)  

