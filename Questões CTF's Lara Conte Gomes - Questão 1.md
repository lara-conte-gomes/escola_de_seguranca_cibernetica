# PicoCTF - Questão 1
## _Feito por: Lara Conte Gomes_

## PicoCTF
É uma plataforma online que contém diversos desafios de cibersegurança desenvolvida pela Carnegie Mellon University. Foi criada para, quem está começando na área de segurança de redes, começar a se familiarizar com alguns temas.
Ela possui diversos exercícios chamados CTFs (Capture The Flag), que são desafios onde o usuário precisa encontrar as 'flags' em cada desafio, utilizando diversos conhecimentos em cibersegurança.
Abaixo está a primeira questão pedida para a documentação, bem como o que foi feito para se conseguir a flag. As outras 3 questões se encontram em documentos separados.

## Questão 1
A primeira questão chama-se 'Cookie Monster Secret Recipe', [link da questão](https://play.picoctf.org/practice/challenge/469). O objetivo era encontrar os cookies de um site. Descobrindo onde se encontram esses cookies pode-se descobrir algumas informações para descobrir a flag.

![Enunciado](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture2.png?raw=true)

#### _O que são Cookies?_
São arquivos de texto com alguns fragmentos de dados, como por exemplo nome do usuário ou senha, que são usados para identificar o computador do usuário quando se acessa uma rede. São específicos para cada pessoa, com o objetivo de melhorar a navegação na Web. Eles salvam informações sobre a navegação de cada um, assim, ao entrar novamente no site, pode-se ter a recuperação dos dados de suas sessões anteriores.

Fonte: https://www.kaspersky.com.br/resource-center/definitions/cookies

### Resolução 
Ao apertar o botão 'Launch Instance', mostra-se uma nova linha oculta onde se tem um link. Ao clicar nele, abre-se um site web.

![Página Web](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture4.png?raw=true)

Para descobrir onde estão os cookies, pensei em inspecionar o site para ver o código fonte por trás dele. Para inspecionar, cliquei com o botão direito do mouse em qualquer lugar da tela do site. Ao fazer isso, abre-se uma janela.

![Botão Inspecionar](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture5.png?raw=true)

No fim dessa janela tem escrito 'Inspecionar'.
Depois, abriu-se uma nova janela no próprio site com o código fonte por trás dele e mais algumas informações.

![Janela Inspecionar](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture6.png?raw=true)

Dando uma olhada nessa nova janela, encontrei um campo escrito 'Application'. Nesse campo, tinha um local escrito Cookie, e, ao clicar nele, vi 'secret_recipe' escrito e, junto dele, uma string.

#### _O que é uma string?_
É uma sequência de caracteres (letras, números e/ou símbolos) muito utilizada em programação.

Fonte: https://www.alura.com.br/artigos/strings-com-javascript-o-que-sao-e-como-manipular?srsltid=AfmBOoqrSgbcDq_psB5cK2vSOVAzGOjOSoExSjnryK7qMnluuZ8PjmND

![Local Cookies](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture7.png?raw=true)

![Mensagem secreta](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture8.png?raw=true)

Depois, pedi ajuda para o ChatGPT sobre o que seria esse tipo de string, pois nunca tinha visto algo assim. Ele me informou que, ao clicar em uma caixinha que tinha em cima da string, poderia ser mostrado a URL decodificada, como está abaixo.

![Caixa para decodificar a mensagem](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture9.png?raw=true)

> cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzc4QjRDMzkwfQ==

Com a URL decodificada, reconheci que se tratava de uma string que precisava ser decodificada pela Base64, porque ela utiliza certos caracteres específicos e '=' no final.
Logo em seguida, abri o site [Base64](https://base64.guru/converter), coloquei a string no site e obtive a flag.

![Flag questão 1](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture10.png?raw=true)

Retornei ao PicoCTF, coloquei a flag e resolvi a questão 1.

![Resolução com sucesso](https://github.com/lara-conte-gomes/escola_de_seguranca_cibernetica/blob/main/prints/Picture3.png?raw=true)

