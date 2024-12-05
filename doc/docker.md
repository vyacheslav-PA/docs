## Docker
###### Dockerfile
```
    FROM ubuntu:latest  
    RUN apt update -y
    LABEL "PWA"
    RUN apt install -y nginx php php-fpm php-mysqli
    RUN apt clean all
    RUN echo "daemon off;" >> /etc/nginx/nginx.conf
    RUN mkdir /run/php-fpm
    COPY . /usr/share/nginx/html/
    CMD php-fpm -D ; nginx
    EXPOSE 80
```
| Comand     |   Description                                |
|:---|:---|
|FROM        |задает базовый образ                              |
|LABEL       |задает метаданные(автор, версия, ...)      |
|ENV         |задает постоянные среды                     |
|RUN         |выполняет команду при настройке образа, создает слой|
|COPY        |копирование в контейнер|
|ADD         | копирует файлы и папки в контейнер, может распаковывать локальные .tar-файлы.             |
|CMD            | описывает команду с аргументами, которую нужно выполнить когда контейнер будет запущен. Аргументы могут быть переопределены при запуске контейнера. В файле может присутствовать лишь одна инструкция CMD             |
|WORKDIR            | задаёт рабочую директорию для следующей инструкции             |
|ARG  | задаёт переменные для передачи Docker во время сборки образа                         |
|ENTRYPOINT       |  предоставляет команду с аргументами для вызова во время выполнения(задает команду по умолчанию)              |
|EXPOSE            |     указывает на необходимость открыть порт         |
|VOLUME        | создаёт точку монтирования для работы с постоянным хранилищем             |

###### Команды docker
| Comand     |   Description                                |
|:---|:---|
docker ps |список контейнеров
 docker rm \<container\>	|удалить контейнер   
  docker pull pwaawp/docsify	|скачать образ  
docker push example.com:5000/my_image	|загрузить образ в репозиторий
docker images	|список образов
docker tag <existing image name> <new image name>	|переименовать образ
docker rmi <image>	|удалить образ
docker system prune	|удалить остановленные контейнеры
docker build . -t my-app	|собрать свой образ
docker run -it my-calendar	|запуск контейнера из образа
docker build . -t my-calendar:2.0.0	|сборка новой версии
docker inspect docerimage |подробнее рассказывает о выбранном контейнере
docker rm containername | удаляет выбранный контейнер (он должен быть выключен, чтобы команда сработала).
docker image build | создать образ 
docker login| войти в докерхаб
docker search nameimage| поиск образа в репозитории




















