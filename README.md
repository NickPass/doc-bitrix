Base bitrix Shop on docker.

- Створити каталог проекту.
- git init
- git clone git@github.com:NickPass/doc-bitrix.git
- Перейменувати контейнери у файлі docker-compose.yml та замінити порти
- sudo docker-compose up -d
- http://localhost:номер порта/bitrixsetup.php
- В підключені БД в бітріксі замість localhost прописати db
- логин пароль и назва бд - dev

XDebug
- изменить docker/php71/conf.d/xdebug.ini 
-- xdebug.remote.host = 172.20.0.1 (можно узнать командой docker inspect <containerNameOrId> - поле "Gateway")
-- xdebug.remote_port = 9130 в настройках ПХПШторма должен совпадать 
- https://blog.denisbondar.com/post/phpstorm_docker_xdebug как настроить
