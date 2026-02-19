# Experiência Com o Void Linux

Entrando no site oficial do void linux na parte de downloads já me deparei com os tipos de ISOs disponíveis, eu irei instalar para a arquitetura x86_64.

Temos as seguintes opções:

- Base:
    - 1. live image com glibc
    - 2. live imagem com musl
    - 3. rootfs tarball com glibc
    - 4. rootfs tarball com musl

- xfce:
    - live image com glibc
    - live image com musl

Explicação:

> Eu vou abordar aqui uma visão mais conceitual sobre cada uma das bibliotecas (glibc e musl)

**Base:**

Vem com a base do sistema pronta e sem interface gráfica, a ISO com glibc significa GNU C library que é uma das bibliotecas padrão no mundo linux, quando seus programas rodam eles não falam diretamente com o kernel mas sim através de uma **Biblioteca Padrão** a libc, que é uma camada intermediária entre o kernel e seus programas.

A libc é um conjunto de funções que todo programa em C e outras linguagens utilizam para executar certas coisas como:

- Abrir arquivos(`fopen`)
- Escrever na tela(`printf`)
- Alocar memória(`malloc`)
- Criar threads(`pthread_create`)
- Fazer requisições de redes(`socket`)

Funciona como uma "ponte" entre seus programas/softwares e o kernel, quando um programa chama um `printf` a lib processa e vê se é necessário executar uma chamada de kernel para aquela operação.

**Resumindo:** A libc é o tradutor universal que todo programa usa para pedir coisas ao sistema operacional.

<hr>

Tá, já tive uma visão bem rasa do que é uma libc, mas e a glibc e musl?


## GNU LIB C (glibc)
A glibc como já dito anteriormente é uma libc, porém desenvolvida pela GNU e é uma das bibliotecas padrão de C mais usadas em distros linux (Exemplo: Debian, Fedora, Ubuntu, Mint, etc).

Ela prioriza compatibilidade e desempenho entre os desktops/servidores, implementa muitas extenções além dos padrões (extenções da GNU), e seu alocador de memória é muito otimizado para programas com muitas threads, porém a glibc é mais pesada que a musl fazendo com que ela ocupe mais espaço na RAM e em Disco, seu código por ser antigo sendo assim mais difícil de ler.

## MUSL
Musl é uma lib moderna, criada para ser simples e eficiênte, ela evita complexidade tendo suas funções implementadas de forma minimalista, seus pontos fortes é ser bem leve consumindo pouca RAM, como o seu código é simples isso facilita a correção de bugs e melhorias, e também o que eu achei interessante foi que o seu alocador de memória tem proteções contra ataques de heap.

Por ser uma lib nova não existem suportes oficiais e isso causa uma falta de compatibilidade com alguns softwares e drivers, falta de suporte para outros idiomas e seu desempenho em alocações de memória pode daixar a desejar em casos de muita concorrência entre threads.
