# Xilften

Xilften (perdão pelo trocadilho) é uma aplicação para recomendação de filmes criada para aprender e aplicar conceitos/tecnologias como:
+ React + Redux
+ Filas + Redis + Background Jobs
+ Recomendação de filmes usando Filtragem Colaborativa
+ Docker

Foi usado um [dataset](https://grouplens.org/datasets/movielens/100k/) do MovieLens com cerca de 100.000 avaliações de 1.000 usuários em 1.700 filmes para criar uma base para a recomendação. Ao avaliar um filme, a recomendação para o usuário é refinada por meio de *filtragem colaborativa* ([veja](https://lamfo-unb.github.io/2018/09/29/Sistemas-de-Recomenda%C3%A7%C3%A3o-usando-Collaborative-Filtering/)). A recomendação para os usuários é recalculada diariamente para refletir o estado atual da base de dados. Os refinamentos são colocados em fila no *Redis* e processados em *background jobs*.

![GIF](https://drive.google.com/uc?export=view&id=1USvy1063TnkOsbbV6kmIkUOHbZXIj-2z)

## Rodando a aplicação

### Com Docker

No diretório raiz da aplicação, execute:

1. `docker-compose build`
2. `docker-compose up`

### Sem Docker

Caso queira executar sem o Docker, você deverá instalar o *Node, Redis, MongoDB* na sua máquina. Após isso, 
1. Certifique-se de que o Redis e o Mongo estejam em execução
2. Na pasta `Backend`:
   - Crie um arquivo `.env`, usando como base o `.env.sample` e preenchendo os valores de porta, senha e host do redis e mongo, além do secret
   - Execute `npm install`
   - Em seguida, `npm run dev`
3. Na pasta `xilften`, execute: `npm install` e `npm run start`

## Acessando a aplicação 

Após isso, a aplicação estará disponível no endereço `http://localhost:3000`. A api estará escutando a porta `3333`. Para acessar a página de monitoramento dos *Jobs*, acesse `http://localhost:3333/admin/queues`.