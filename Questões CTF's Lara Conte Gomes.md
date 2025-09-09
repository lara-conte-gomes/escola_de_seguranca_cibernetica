# PicoCTF - Questões 1, 2, 3 e 4 
## _Feito por: Lara Conte Gomes_

## PicoCTF
É uma plataforma online que contém diversos desafios de cibersegurança desenvolvida pela Carnegie Mellon University. Foi criada para, quem está começando na área de segurança de redes, começar a se familiarizar com alguns temas.
Ela possui diversos exercícios chamados CTFs (Capture The Flag), que são desafios onde o usuário precisa encontrar as 'flags' em cada desafio, utilizando diversos conhecimentos em cibersegurança.
Abaixo estão 4 questões pedidas para a documentação, bem como o que foi feito para se conseguir cada flag.

## Questão 1
A primeira questão chama-se 'Cookie Monster Secret Recipe', [link da questão](https://play.picoctf.org/practice/challenge/469). O objetivo era encontrar os cookies de um site. Descobrindo onde se encontram esses cookies pode-se descobrir algumas informações para descobrir a flag.

![Enunciado](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture2.png?raw=true)

#### _O que são Cookies?_
São arquivos de texto com alguns fragmentos de dados, como por exemplo nome do usuário ou senha, que são usados para identificar o computador do usuário quando se acessa uma rede. São específicos para cada pessoa, melhorando a navegação na Web. Eles salvam informações sobre a navegação de cada um, assim, ao entrar novamente no site, pode-se ter a recuperação de seus dados de suas sessões anteriores.

Fonte: https://www.kaspersky.com.br/resource-center/definitions/cookies

### Resolução 
Ao apertar o botão 'Launch Instance', ele mostra uma nova linha oculta onde se tem um link. Ao clicar nele, abre-se um site web.

![Página Web](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture4.png?raw=true)

Para descobrir onde estão os cookies, pensei em Inspecionar o site para ver o código fonte por trás dele. Para Inspecionar, cliquei com o botão direito do mouse em qualquer lugar da tela do site. Ao fazer isso, abre-se uma janela.

![Botão Inspecionar](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture5.png?raw=true)

No fim dessa janela tem Inspecionar.
Depois, abriu-se uma nova janela no próprio site com o código fonte por trás dele.

![Janela Inspecionar](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture6.png?raw=true)

Dando uma olhada nessa nova janela, inspecionando o site, encontrei um campo escrito 'Application'. Nesse campo, tinha um local escrito Cookie, ao clicar nele eu vi 'secret_recipe' escrito e, junto dele, uma string.

![Local Cookies](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture7.png?raw=true)

![Mensagem secreta](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture8.png?raw=true)

Depois, pedi ajuda para o ChatGPT sobre o que seria esse tipo de string, pois nunca tinha visto algo assim. Ele me informou que, ao clicar em uma caixinha que tinha em cima da string, poderia ser mostrado a URL decodificada, como está abaixo.

![Caixa para decodificar a mensagem](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture9.png?raw=true)

> cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzc4QjRDMzkwfQ==

Com a URL decodificada, eu reconheci que se tratava de uma string que precisava ser decodificada pela Base64, porque ela utiliza certos caracteres específicos e '=' no final.
Logo em seguida, abri o site [Base64](https://base64.guru/converter), coloquei a string e obtive a flag.

![Flag questão 1](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture10.png?raw=true)

Retornei ao PicoCTF, coloquei a flag e resolvi a questão 1.

![Resolução com sucesso](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture3.png?raw=true)

## Questão 2
A segunda questão chama-se 'Flag Hunters', [link da questão](https://play.picoctf.org/practice/challenge/472). Nela, se tem um link em que se pode baixar um código que possui a letra de uma música. O objetivo é fazer com que um refrão secreto aparecesse utilizando os conceitos de Injeção de Código.

![Questão 2](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture11.png?raw=true)

#### _O que é Injeção de Código?_
É um tipo de ataque cibernético onde os invasores utilizam as vulnerabilidades presentes em aplicativos para injetar algum tipo de código malicioso em um sistema. Aproveita-se das deficientes validações de entrada e codificações inseguras, a fim de obter acesso, manipular ou exportar informações confidenciais.

Fonte: https://www.sentinelone.com/cybersecurity-101/cybersecurity/code-injection/

### Resolução
Ao baixar o código, abri ele no VSCode (Visual Studio Code), um editor de código-fonte, onde pode-se programar em diversas linguagens de programação.

![Código baixado](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture17.png?raw=true) 

![VSCode](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture12.png?raw=true) 

Para rodar o código, utilizei o WebShell do próprio PicoCTF. Ao clicar no botão  ‘Launch Instance’, ele me deu um comando que coloquei no WebShell:

> nc verbal-sleep.picoctf.net 59410

Ao fazer isso, a letra da música começou a aparecer. Ele mostrou o primeiro verso e depois o refrão, quando terminou o refrão apareceu 'Crowd: ', e estava esperando uma entrada do usuário, ou seja, eu devia digitar algo.
Tentei apenas dar Enter no teclado mas o código apenas continuou a letra e não me mostrou a flag.
Conversei com duas pessoas do time de Cibersegurança. Um deles me orientou a olhar atentamente o código para encontrar algo nele que pudesse me ajudar a resolver a questão.
Não encontrando nada de errado, perguntei para o segundo integrante do time e ele me orientou em como resolver a questão.
Eu devia olhar o seguinte trecho de código:

![Trecho código](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture13.png?raw=true)  

Olhando esse trecho, ele me disse que, uma das formas de fazer com que o trecho secreto fosse mostrado, seria escrever algo, como por exemplo 'teste', mas que eu devia colocar ';' e escrever' RETURN 0(zero)' depois, pois assim eu iria conseguir fazer com que o código retornasse ao início que estava oculto.

![Música no WebShell](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture14.png?raw=true)  

![Flag na música](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture15.png?raw=true)   

Ao colocar isso, a flag apareceu e consegui resolver a questão 2.

![Resolução correta](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture16.png?raw=true)  

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

## Questão 4
A quarta questão chama-se 'RED', [link da questão](https://play.picoctf.org/practice/challenge/460).

![Questão 4](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture29.png?raw=true)  

O objetivo é baixar a imagem red.png e tentar descobrir a flag.
Para essa questão, tive ajuda de um dos integrantes do time de Cibersegurança. Ele me orientou a pesquisar sobre esteganografia e algumas ferramentas, com foco especial na ferramenta zsteg.

#### _O que é esteganografia?_
É a prática de ocultar informações dentro de uma mensagem ou objeto físico para que não seja detectado algo. Ela pode ser utilizada pra ocultar qualquer tipo de conteúdo digital, no caso da questão é uma imagem png (Portable Network Graphics (Gráficos Portáteis de Rede), um tipo de formato de imagem).

#### _O que é zsteg?_
É uma ferramenta de código aberto que serve para detectar e extrair dados ocultos em imagens em formato PNG e BMP.

### Resolução
Para resolver a questão, utilizei o WebShell do PicoCTF. Carreguei a imagem nele.

![WebShell PicoCTF Print1](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture25.png?raw=true)   

Depois utilizei o seguinte comando, que está no print, para que se pudesse detectar o que se tem oculto na imagem.

![WebShell PicoCTF Print2](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture26.png?raw=true)  

No segundo 'text', observei uma string. No fim dela tinha '==', logo pensei que devia decodificá-la com a Base64.
Só que eu havia copiado tudo, e na verdade estava ocorrendo repetições da mesma string. Ao apagar uma boa parte, e mantendo apenas o necessário, descobri a flag e resolvi a questão 4.

![Base64](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture27.png?raw=true)   

![Resolução](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture28.png?raw=true)    

