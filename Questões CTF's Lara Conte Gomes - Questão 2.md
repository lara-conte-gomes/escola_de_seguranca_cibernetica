# PicoCTF - Questão 2 
## _Feito por: Lara Conte Gomes_

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

Para rodar o código, utilizei o WebShell do próprio PicoCTF. 

#### _O que é um WebShell do PicoCTF?_
É um ambiente de desenvolvimento shell Linux (interface Linux (Sistema Operacional) onde se pode colocar diversos comandos) baseado na Web, ou seja, não é necessário a instalação do Sistema Operacional Linux no computador, o acesso é feito por meio da Web. Muito utilizado para se resolver os desafios de CTF's.

Fonte: https://status.picoctf.org/affected/webshell/

Ao clicar no botão  ‘Launch Instance’, ele me deu um comando que coloquei no WebShell:

> nc verbal-sleep.picoctf.net 59410

Ao fazer isso, a letra da música começou a aparecer. Ele mostrou o primeiro verso e depois o refrão. Quando terminou o refrão, apareceu 'Crowd: ', e estava esperando uma entrada do usuário, ou seja, eu devia digitar algo.
Tentei apenas dar Enter no teclado mas o código apenas continuou a letra e não me mostrou a flag.

Conversei com duas pessoas do time de Cibersegurança do Inatel (Instituto Nacional de Telecomunicações). Um deles me orientou a olhar atentamente o código para encontrar algo nele que pudesse me ajudar a resolver a questão.
Não encontrando nada de errado, perguntei para o segundo integrante do time e ele me orientou em como resolver a questão.
Eu devia olhar o seguinte trecho de código:

![Trecho código](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture13.png?raw=true)  

Olhando esse trecho, ele me disse que, uma das formas de fazer com que o trecho secreto fosse mostrado, seria escrever algo, como por exemplo 'teste', mas que eu devia colocar ';' e escrever' RETURN 0(zero)' depois, pois assim eu iria conseguir fazer com que o código retornasse ao início, que estava oculto anteriormente.

![Música no WebShell](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture14.png?raw=true)  

![Flag na música](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture15.png?raw=true)   

Ao colocar isso, a flag apareceu e consegui resolver a questão 2.

![Resolução correta](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture16.png?raw=true)  

