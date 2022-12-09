# Como utilizar o InertiaJS para criar projetos Laravel+React

## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/windows8/windows8-original.svg"> Para PCs Windows
### Para os computadores de SO Windows, será necessário a instalação de uma distribuição Linux
De forma simples, a instalação de um terminal Linux pode ser feito por meio da Microsoft Store, a loja de aplicativos padrão do SO Windows. Para instalar, basta pesquisar por "Ubuntu" na aba de pesquisa, e instalar a versão da imagem:

![image](https://user-images.githubusercontent.com/90472705/205295249-a4514154-4e06-4f91-9266-b6269d462166.png)

Após isso, pode-se seguir para os próximos passos normalmente.

## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg"> Instalação do Docker
### O Docker virtualiza os arquivos em containers, como se rodasse a parte cada arquivo do projeto
O download pode ser feito no [site](https://www.docker.com/products/docker-desktop/) oficial do Docker
![image](https://user-images.githubusercontent.com/90472705/205301743-ab3f1965-a6f3-4150-b834-36afe477e2fa.png)

### Configuração do Docker
É necessário habilitar o WSL Integration para o Ubuntu (Já instalado anteriormente).
![image](https://user-images.githubusercontent.com/90472705/205302187-c9796598-e494-4a28-b5ff-2217fc3f0ed9.png)

Para acessar opção basta acessar ``Configurações > Resources > WSL Integration`` e ativar as opções.
![image](https://user-images.githubusercontent.com/90472705/205303414-1606572c-6870-407e-bdd8-d509b54733a0.png)

Obs.: Caso a instalação tenha sido feita, mas a opção não esteja aparecendo, verificar se a sua máquina está configurada para a utilização do WSL 2.
## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-plain.svg"> Criação de um projeto Laravel
### É necessário a inicialização do Ubuntu para criar o projeto Laravel
Todo o processo e explicação da criação de um projeto Laravel pode ser visto na [documentação oficial](https://laravel.com/docs/9.x/installation), mas também será apresentado aqui.

- 1 - Abra o terminal Ubuntu
- 2 - Abra o diretório da sua preferência: ``cd nomediretorio``
- 3 - Execute o seguinte comando: ``composer create-project laravel/laravel <nomeseuprojeto>`` 
- 4 - Entre no diretório: ``cd nomeseuprojeto``

## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-plain.svg"> Configuração do projeto Laravel
### Instalando php 8.1 e a ext. Pode ser visto na [documentação oficial](https://whimsical.com/iniciar-novo-projeto-com-laravel-e-react-8ot7mgpn6YVubrt6tuU9UJ)
![image](https://user-images.githubusercontent.com/90472705/205307898-b5b0edf5-0438-403a-9ab7-eb006c756e41.png)
Abra o terminal do Ubuntu, e dentro da pasta do projeto execute os seguintes comandos:
- ``sudo apt install software-properties-common``
- ``sudo add-apt-repository ppa:ondrej/php``
- ``sudo apt update``
- ``sudo apt install php8.1``
- ``sudo apt install php8.1-mbstring php8.1-xmlrpc php810-soap php8.1-gd php8.1-xml php8.1-cli php8.1-zip php8.1-bcmath php8.1-tokenizer php8.1-intl``
- ``sudo apt install php8.1-sqlite3`` 

Após isso, o projeto está pronto para ser configurado de forma padrão

## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg"> Configuração o InertiaJS
### Agora inicia-se a configuração do InertiaJS para o uso do React. A documentação pode ser vista na [documentação oficial](https://inertiajs.com/server-side-setup).
![image](https://user-images.githubusercontent.com/90472705/205308969-50764d98-1821-403d-ac15-95f14f00bb73.png)

### Lado do servidor
Dentro do Ubuntu, no diretório do projeto, execute o comando de instalação das dependências
``composer require inertiajs/inertia-laravel``

Então abra o seu editor de código e em ```resources > views > welcome.blade.php``` altere o HTML para o seguite:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0" />
    <link href="{{ mix('/css/app.css') }}" rel="stylesheet" />
    <script src="{{ mix('/js/app.js') }}" defer></script>
    @inertiaHead
  </head>
  <body>
    @inertia
  </body>
</html>
```

ele deve ficar desta forma:
![image](https://user-images.githubusercontent.com/90472705/205310395-81ec3dbe-3da5-41e5-8edc-f29fd24b7899.png)

entao, no terminal Ubuntu, execute os seguintes comandos: 
- ```sail up -d```
- ```sail php artisan inertia:middleware```

Dentro do seu editor de códigos, visualize em ```App\Http\Kernel``` a parte ```web```. Então no final introduza a seguinte linha de código:
```php
\App\Http\Middleware\HandleInertiaRequests::class,
```

ele deve ficar desta forma:
![image](https://user-images.githubusercontent.com/90472705/205311433-3500d011-7748-4aca-8724-f107ce6fe445.png)


### Lado do cliente
Execute o seguinte comando no terminal do Ubuntu:
```
npm install @inertiajs/inertia @inertiajs/inertia-vue3
```

Abra o editor de código e procure por ```resources > js > app.js```, e então (dentro do arquivo app) cole o seguinte trecho de código:
```js
import React from 'react'
import { render } from 'react-dom'
import { createInertiaApp } from '@inertiajs/inertia-react'

createInertiaApp({
  resolve: name => require(`./Pages/${name}`),
  setup({ el, App, props }) {
    render(<App {...props} />, el)
  },
})
```

seu código deve ficar desta forma:
![image](https://user-images.githubusercontent.com/90472705/205312617-3a8ac9d5-2143-4082-bda1-0e233d17de6f.png)

Antes de seguir com a instalação, verifique qual meio será utilizado para a criação de arquivos durante a realização do projeto, se ele será utilizando containers do Docker, ou se será apenas utilizados instalações feitas em sua máquina sem a utilização dos containers.

Caso seu projeto seja necessário a utilização de containers, será necessário a instalação do Sail no seu projeto, e ele pode ser feito pelo seguinte comando:
``` 
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php81-composer:latest \
    composer install --ignore-platform-reqs
```

Os comandos a seguir já utilizão o conceito de que foi instalado o Sail, no caso de não ter sido instalado, os comandos relacionados ao Artisan utilizarão o php no lugar do sail e não será utilizado o sail dos outros comandos.

## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg"> Configurando o Breeze
Dentro do terminal Ubuntu, execute os seguintes comandos:
- ```sail composer require laravel\breeze --dev```
- ```sail artisan breeze:install react```
- ```sail npm install```


por último, altere o endereço localhost em ```public > hot ```. Apague os endereço e deixe apenas ```http://localhost:5173```, assim:

![image](https://user-images.githubusercontent.com/90472705/205315996-ab193efa-5dc4-4254-8630-259adffeb881.png)


para rodar o projeto basta executar ```sail npm run dev```
