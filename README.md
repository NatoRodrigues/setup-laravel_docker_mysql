<h1>Setup Projeto Laravel com Docker e MySQL</h1>
<br>


<center>
<div style="display: flex; align-items: center; justify-content: center;">
    <img src="https://laravel.com/img/logomark.min.svg" alt="Logo do Laravel" width="160">
    <img src="https://www.mysql.com/common/logos/logo-mysql-170x115.png" alt="Logo do MySQL" width="160">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" width="160">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nginx/nginx-original.svg" width="160" />
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/redis/redis-original-wordmark.svg" width= "160"/>      
</div>
</center>
<br>
<br>
Este repositório contém instruções e scripts para configurar um ambiente de desenvolvimento Laravel utilizando Docker, MySQL, com servidor proxy reverso nginx e redis. Essas etapas ajudarão você a iniciar rapidamente um projeto Laravel em um ambiente isolado usando contêineres Docker.
<br>
<h1>Pré-requisitos:</h1>

Certifique-se de ter as seguintes ferramentas instaladas em sua máquina antes de prosseguir:

    Git
    Docker
    Docker Compose

Passos de Instalação

Clone o repositório para o seu sistema:

    git clone https://github.com/NatoRodrigues/setup-laravel_docker_mysql.git

Crie um novo projeto Laravel dentro do diretório clonado:

    composer create-project laravel/laravel demo

Obs: como o repositório já possui um projeto Laravel na pasta demo, podemos passar para a próxima etapa.

Agora, você estará pronto para construir e executar os contêineres Docker para o ambiente Laravel:

    docker-compose up -d --build


Verifique os contêineres ativos:

    docker container ls



Configuração do Ambiente Laravel

Execute os seguintes comandos dentro do contêiner PHP para configurar o ambiente Laravel:

Atualiza a configuração em cache do Laravel para melhorar o desempenho:

    docker exec setup-php php artisan config:cache

Instala as dependências do projeto Laravel usando o Composer. O Composer é um gerenciador de pacotes PHP amplamente utilizado:

    docker exec setup-php composer install

Executa as migrações do banco de dados definidas no projeto Laravel. Isso cria as tabelas e relacionamentos no banco de dados configurado:

    docker exec setup-php php artisan migrate



Uso e Desenvolvimento

Depois de completar os passos acima, seu ambiente de desenvolvimento Laravel estará em execução dentro dos contêineres Docker. Você pode acessar seu aplicativo Laravel no navegador usando o endereço http://localhost. Qualquer alteração que você fizer no código do projeto será refletida no ambiente imediatamente. Lembre-se de que os arquivos do seu projeto Laravel estarão localizados dentro do diretório demo neste repositório.
Encerrando o Ambiente

Quando você terminar de trabalhar, certifique-se de encerrar corretamente o ambiente:

    docker-compose down

Isso desligará os contêineres Docker e liberará os recursos da sua máquina.
