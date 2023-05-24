# Projeto Shiny Charmanders (NFT Collection)
Construído na rede Mumbai

Site disponível em [https://nft-bootcamp-front.jg-lembo.repl.co/](https://nft-bootcamp-front.jg-lembo.repl.co/) através do Replit.

## A Plataforma

A plataforma do projeto tem como funcionalidade permitir que o usuário gere uma NFT exclusiva de um Charmander Shiny com cores aleatórias.

Caso o usuário conectado já possua um Charmander, o botão de Cunhar NFT torna-se um botão para redirecionar o usuário à página da OpenSea com o seu Charmander. Isso garante que o usuário tenha apenas uma NFT, permitindo que mais pessoas possam gerá-las, já que há um limite de 1000.

Por fim, a plataforma contém um botão para exibir a coleção completa na OpenSea e um contador que mostra quantos dos 1000 Charmanders disponíveis já foram gerados.

## O Contrato

O contrato contém o código necessário para execução das funcionalidades da plataforma, principalmente a geração dos Charmanders aleatórios e os cunhos das respectivas NFTs.

O construtor do contrato não realiza nenhuma operação, já que a parte importante do contrato encontra-se diretamente na função _makeAnEpicNFT_.

A função é responsável por gerar as cores aleatórias, o SVG com elas e, enfim, a NFT de fato, cunhando-a para o usuário que invocou a função. A função verifica também que ainda não foram cunhadas 1000 NFTs, e que o endereço que invocou a função não é dono de uma NFT dessa coleção.

Para gerar as cores aleatórias, é utilizada a função _generateSVGColors_, que gera o código hexadecimal de 3 cores diferentes. Cada uma delas é criada sorteando-se 6 caracteres entre 0 e E, através das funções _generateColors_ e _pickRandomByte_. 

Além disso, o contrato possui as funções _isOwner_ e _getOwnerToken_, para identificar se aquele endereço é dono de uma NFT e qual o ID do token de um endereço, respectivamente. Essas funções tem como objetivo fazer com que o frontend possa descobrir que o usuário conectado já possui uma NFT, e então recuperar o token ID, para que possa fornecer o link para a NFT na OpenSea.

Por fim, para a geração do SVG, é utilizada a library SVGGenerator. Ela consiste de uma única função, _generateSVG_, que recebe as cores aleatórias e as insere no SVG de um Charmander, alterando as cores de seu corpo, barriga, e olhos.