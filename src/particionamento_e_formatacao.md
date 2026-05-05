# Particionamento e formatacao dos discos

Bom, o void nao eh exatamente a ponto de nao vir com `fdisk` na iso, e foi ele mesmo que eu utilizei para particionar o disco.

Antes de particionar o disco precisamos entender o que eh um `Sistema De Arquivos`, de forma estupidamente resumida um sistema de arquivos eh uma forma de organizar os arquivos para que o computador possa manipulalos, encontrar tal arquivos e coisas do tipo.

Link util: [https://guialinux.uniriotec.br/sistemas-de-arquivos/](https://guialinux.uniriotec.br/sistemas-de-arquivos/)

## Identificando o seu dispositivo de armazenamento

Sim, eu falei "dispositivo de armazenamento" porque dependendo do seu computador ele pode variar. Podemos identificar o nosso device usando o comando `lsblk` que serve para nos listar e mostrar informacoes sobre dispositivos de armazenamento conectados no nosso computador.

Em SSDs modernos sera algo como `nvme0n1` e HDs "velhos" `sda`, para que voce entenda melhor da que pra frente eh preciso ter lido o link util que eu escrevi ali em cima.

## Usando fdisk para criar as particoes

> versao 2.40.2

Antes de iniciar eu queria dar um aviso sobre o `fdisk`, o `fdisk` apaga TODOS os dados do device que voce for particionar, por exemplo, se voce tem o Windows dentro de uma particao e quiser "cortar" um pedaco dela, o seu Windows vai sumir (🙏), entao tome cuidado.

Apos voce identificar o seu device, use o comando `fdisk <name_your_device>` para entrar no `fdisk`.

Use `m` para help se precisar, nos vamos usar primeiro a letra `g` para criar uma nova tabela de particoes GPT (se o seu computador for UEFI). Uma tabela de particoes eh um metadado gravado no comeco e no fim do disco, ela guarda informacoes como: quantidade de particoes, inicio e fim de cada particao, flags de boot, etc.

Apos criar uma Tabela de particoes GPT use `n` para criar uma nova particao, nas duas primeiras opcoes deixe como default e na ultima escreva `+512M` para `512 MegaBytes` que sera a primeira particao do disco onde guarda o bootloader.
