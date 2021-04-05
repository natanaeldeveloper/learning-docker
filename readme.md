* O `Dockerfile` é um arquivo de texto contendo os comandos para construir uma imagem Docker.

~~~Dockerfile
#Arquivo Dockerfile

FROM php:5.6-apache
RUN docker-php-ext-install mysqli
~~~

* No `FROM` apontamos qual a imagem que será usanda como base.

* No `RUN` vamos executar um comando de modo que a extensão mysqli será instalada.

~~~yml
#Arquivo docker-compose.yml

php:
  build: .
  ports:
   - "80:80"
   - "443:443"
  volumes:
   - ./www:/var/www/html
~~~

* Na primeira linha vai o nome do nosso container, `php`.

* No `build` é o arquivo com os dados da imagem que iremos utilizar. Queremos utilizar uma nova imagem como base no Dockerfile que acabamos de criar.

* Em `ports` vamos definir o mapeamento das portas. Para o nosso servidor web desejamos que as portas 80 e 443 estejam disponíveis. Vamos vincular os portas do container com as do hospedeiro, por exemplo, “host port:container port”. Se a posta 80 já está sendo utilizada no seu host, pode ser mapeada outra porta.

* Como etapa final, mas não menos importante, será feito o mapeamento de um volume para o container.
A linha `./www:/var/www/html` significa que ligará a pasta “./www” no host para a pasta `/var/www/html` em nosso container.

* Agora execute `docker-compose up`
e a imagem será construída e executada. E, então, utilize o navegador para acessar o IP do servidor, e vamos ver a página phpinfo. Ao finalizar a construção da imagem será exibido o IP da mesma para acesso.

### Referencias

[criando-um-ambiente-de-desenvolvimento-php-com-docker-compose](https://medium.com/@FernandoDebrand/criando-um-ambiente-de-desenvolvimento-php-com-docker-compose-a7cad3373df0)