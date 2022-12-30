+++
title = "velvet"
date = 2022-12-16
+++

Em dezembro do ano passado, em um hotel, eu tive uma ideia. Era um momento de relaxamento e calma: eram as férias. Mesmo assim, essa ideia consumiu meus pensamentos e eu não consegui esperar. Eu instalei o [Obsidian](https://obsidian.md/) no celular para documentar o projeto do início ao fim.

A ideia veio da dificuldade de administrar os diversos mods de Minecraft que são comumente instalados para lidar com o desempenho do jogo. Quem jogou Minecraft moderno sabe que além de instalar o Fabric, é necessário manter-se informado sobre o ecossistema de mods de otimização do jogo, principalmente após a queda do OptiFine. Para pessoas que querem apenas jogar o jogo, essa dinâmica não é ideal. 

O objetivo principal era instalar o Fabric e organizar os mods em pastas separadas pela versão do jogo para que o usuário possa, simultaneamente, manter diversas instalações com suas respectivas pastas de mod.

No início, eu não tinha acesso ao computador e não podia testar código algum ou colocar meus pensamentos em prática. Uma consequência interessante disso foi que pude conceitualizar o projeto inteiro antes de escrever o código.

Eu sabia que queria os meus mods na estrutura `.minecraft/.woven/mods/<versão>`. O nome do subdiretório `.woven` é derivado de Fabric: um nome apropriado para o projeto.

O Fabric sempre lê os mods na pasta `.minecraft/mods`, então teria que ser modificado para lidar com a pasta de mods dinamicamente. Daí veio a primeira dificuldade: programar em Java. Eu tenho pouca experiência com Java, mas como seria um pequeno _patch_ no código, eu pensei que seria simples o suficiente.

Meus três objetivos iniciais foram definidos: modificar o Fabric, instalá-lo e baixar os mods.

Uma vantagem de dividir as etapas antes de começar a programar é que você fica preso às ideias originais e não começa a adicionar funções novas com o tempo.
# Em prática
Eu comecei a programar o programa em Rust, essa escolha foi definida desde o início do projeto. Modificar o Fabric seria simples. Em sua inicialização, ele já sabe a versão na qual o jogo está rodando. O maior problema foi na instalação.

O launcher do Minecraft trabalha com JSON. A biblioteca [serde](https://serde.rs/) possui todas as ferramentas necessárias para lidar com as principais estruturas de dados. Porém, eu senti medo porque todos os exemplos da biblioteca tinham muitas coisas que eu ainda não havia aprendido. Por causa disso, eu deixei o projeto de lado.

Em novembro, pouco mais de nove meses depois, eu lembrei do projeto e continuei de onde tinha parado. Porém, pelo intervalo de tempo, algumas coisas mudaram.

Primeiro, um _fork_ do Fabric, [Quilt](https://quiltmc.org), implementou a função a passar uma pasta de mods dinâmica usando apenas opções da JVM. Por causa disso, eu optei pelo Quilt porque, então, não precisaria manter minha própria modificação do Fabric e um Maven para distribuição.

Segundo, eu descobri um projeto com o nome "[WovenMC](https://github.com/WovenMC)" e decidi mudar para "Velvet".

Por fim, eu escrevi toda a instalação do Quilt e usei a biblioteca [ferinth](https://crates.io/crates/ferinth) para comunicar com o API do Modrinth, uma plataforma de mods que amadureceu durante o ano, e instalar os mods.
# Conclusão
É interessante pensar que eu demorei quase um ano para trazer uma pequena ideia à vida. Às vezes, abandonamos projetos porque nos vemos longe demais de concluí-los.

Meu principal relato é que o sentimento de retomar um projeto com conhecimento e energia suficiente para terminá-lo é muito gratificante.

Por causa disso, documentar o processo é uma etapa importante. A principal vantagem dessa experiência foi manter comigo minhas anotações do início até o final.

O código do projeto está disponível [aqui](https://github.com/derspyy/velvet).