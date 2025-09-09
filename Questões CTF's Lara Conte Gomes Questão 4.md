# PicoCTF - Questão 4 
## _Feito por: Lara Conte Gomes_

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

