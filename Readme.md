# IWNO3 Первый контейнер

## Цель работы

Данная лабораторная работа знакомит с основами контейнеризации и подготавливает рабочее место для выполнения следующих лабораторных работ.

## Задание

Установить Docker Desktop и проверить его работоспособность.

### Шаг 1 Установка Docker Desktop
Устанавливаю с сайта https://www.docker.com/
### Шаг 2 Создать репозиторий `containers02` и склонировать его на компьютер.
Cоздаю на github новый репозиторий https://github.com/ShiroyamaY/usm_containers_02

Так как я изначально сделал работу а потом запушил на репозиторий, я выполнил следующие команды для:
	 `git init` -  для создания репозитория
	`git remote add origin {link}` -  для связывания локального репозитория с удаленным.
	`git add . ` - для индексирования всех изменений
	`git commit -m "{name of commit}"` - для названия коммита

### Шаг 3. Создать папку `site` и файл `index.html`.

### Шаг 4. Создать Dockerfile со следующим содержимым
```Dockerfile
FROM debian:latest
COPY ./site/ /var/www/html/
CMD ["sh", "-c", "echo hello from $HOSTNAME"]
```
- **`FROM debian:latest`**
    
    - Указывает базовый образ, `debian:latest` — последняя доступная версия операционной системы Debian, этот образ предоставляет минимальную среду Debian
- **`COPY ./site/ /var/www/html/`**
    
    - Копируем содержимое локальной папки `site` в директорию `/var/www/html/` внутри контейнера.

- **`CMD ["sh", "-c", "echo hello from $HOSTNAME"]`**
    
    - Это команда которая будет выполнена при запуске контейнера, тоесть `sh -c "echo hello from $HOSTNAME"` выполняет команду `echo`, которая выводит строку `"hello from {container_name}"`.
    - `$HOSTNAME` — это переменная среды, которая содержит имя текущего контейнера.
### Шаг 5. Выполнена команда сборки образа:
    
    ```
    docker build -t containers02 .
    ```
    
- Время создания образа: **17.4s**
### Шаг 6. Запуск контейнера из собранного образа:

```
	root@1e2cf75cf40e:/var/www/html# exit
	exit
```
### Шаг 7. Проверка содержимого `/var/www/html/`

- Удаление контейнера:
    
    ```
    docker rm containers02
    ```
    
- Запуск контейнера в интерактивном режиме:
    
    ```
    docker run -ti --name containers02 containers02 bash
    ```
    
- Внутри контейнера выполнены команды:
    
```
    root@1e2cf75cf40e:/# cd /var/www/html/
    root@1e2cf75cf40e:/var/www/html# ls -l 
```
    
- Вывод в консоли: **(указать содержимое каталога)**.
```
	 total 0
	-rwxr-xr-x 1 root root 0 Mar  1 07:56 index.html
```
- Выход из контейнера командой `exit`. 
```
	root@1e2cf75cf40e:/var/www/html# exit
	exit
```

## Выводы

В ходе работы были освоены базовые принципы контейнеризации с Docker, а также выполнены операции по созданию образов и контейнеров, копированию файлов в контейнер, работе внутри контейнера и его управлению.

## Используемые источники

1. [Docker docs](https://docs.docker.com/)
    
2. [Moodle lab info](https://moodle.usm.md/mod/assign/view.php?id=282116).
    

## Представление

Rep link: **https://github.com/ShiroyamaY/usm_containers_02**.
