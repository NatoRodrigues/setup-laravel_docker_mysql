<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            line-height: 1.6;
        }
        h1, h2, h3 {
            color: #333;
        }
        code {
            background-color: #f4f4f4;
            padding: 5px;
            border: 1px solid #ddd;
            display: block;
        }
        pre {
            background-color: #f4f4f4;
            padding: 10px;
            border: 1px solid #ddd;
            overflow-x: scroll;
        }
    </style>
</head>
<body>
    <h1>Setup do Projeto Laravel com Docker e MySQL</h1>
    <p>Este repositório contém instruções e scripts para configurar um ambiente de desenvolvimento Laravel utilizando Docker e MySQL. Essas etapas ajudarão você a iniciar rapidamente um projeto Laravel em um ambiente isolado usando contêineres Docker.</p>
    
    <h2>Pré-requisitos</h2>
    <p>Certifique-se de ter as seguintes ferramentas instaladas em sua máquina antes de prosseguir:</p>
    <ul>
        <li>Git</li>
        <li>Docker</li>
        <li>Docker Compose</li>
    </ul>
    
    <h2>Passos de Instalação</h2>
    <div>
        <p>Clone o repositório para o seu computador:</p>
        <pre><code>git clone https://github.com/seu-usuario/setup-laravel_docker_mysql.git</code></pre>
    </div>
    <div>
        <p>Crie um novo projeto Laravel dentro do diretório clonado:</p>
        <pre><code>composer create-project laravel/laravel demo</code></pre>
        <p><em>Obs: como o repositório já possui um projeto Laravel na pasta demo, podemos passar para a próxima etapa.</em></p>
    </div>
    
    <div>
        <p>Agora, você estará pronto para construir e executar os contêineres Docker para o ambiente Laravel:</p>
        <pre><code>docker-compose up -d --build</code></pre>
    </div>
    
    <div>
        <p>Verifique os contêineres ativos:</p>
        <pre><code>docker container ls</code></pre>
    </div>
    
    <h2>Configuração do Ambiente Laravel</h2>
    <div>
        <p>Execute os seguintes comandos dentro do contêiner PHP para configurar o ambiente Laravel:</p>
        <pre><code># Atualiza a configuração em cache do Laravel para melhorar o desempenho.
docker exec setup-php php artisan config:cache</code></pre>
        <pre><code># Instala as dependências do projeto Laravel usando o Composer.
# O Composer é um gerenciador de pacotes PHP amplamente utilizado.
docker exec setup-php composer install</code></pre>
        <pre><code># Executa as migrações do banco de dados definidas no projeto Laravel.
# Isso cria as tabelas e relacionamentos no banco de dados configurado.
docker exec setup-php php artisan migrate</code></pre>
    </div>
    
    <h2>Uso e Desenvolvimento</h2>
    <p>Depois de completar os passos acima, seu ambiente de desenvolvimento Laravel estará em execução dentro dos contêineres Docker. Você pode acessar seu aplicativo Laravel no navegador usando o endereço <a href="http://localhost">http://localhost</a>. Qualquer alteração que você fizer no código do projeto será refletida no ambiente imediatamente.</p>
    <p>Lembre-se de que os arquivos do seu projeto Laravel estarão localizados dentro do diretório <code>demo</code> neste repositório.</p>
    
    <h2>Encerrando o Ambiente</h2>
    <p>Quando você terminar de trabalhar, certifique-se de encerrar corretamente o ambiente:</p>
    <pre><code>docker-compose down</code></pre>
    <p>Isso desligará os contêineres Docker e liberará os recursos da sua máquina.</p>
</body>
</html>
