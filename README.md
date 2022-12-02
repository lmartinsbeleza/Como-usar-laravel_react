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
É necessário habilitar o WSL Integration para o Ubuntu (Já instalado anteriormente)
![image](https://user-images.githubusercontent.com/90472705/205302187-c9796598-e494-4a28-b5ff-2217fc3f0ed9.png)

Para acessar opção basta acessar ``Configurações > Resources > WSL Integration`` e ativar as opções.
![image](https://user-images.githubusercontent.com/90472705/205303414-1606572c-6870-407e-bdd8-d509b54733a0.png)

## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-plain.svg"> Criação de um projeto Laravel
### É necessário a inicialização do Ubuntu para criar o projeto Laravel
Todo o processo e explicação da criação de um projeto Laravel pode ser visto na [documentação oficial](https://laravel.com/docs/9.x/installation), mas também será apresentado aqui.

- 1 - Abra o terminal Ubuntu
- 2 - Abra o diretório da sua preferência: ``cd nomediretorio``
- 3 - Execute o seguinte comando: ``composer create-project laravel/laravel nomeseuprojeto`` 
- 4 - Entre no diretório: ``cd nomeseuprojeto``

## <img align="center" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-plain.svg"> Configuração do projeto Laravel
