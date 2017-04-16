# Create Docker

### 1. Set environment variables

  - #### As your current directory

```
export RAILS_MYSQL_DOCKER_PATH=$PWD && echo "Your rails project path is ${RAILS_MYSQL_DOCKER_PATH}"
```

  OR

  - #### Your rails project path

```
export RAILS_MYSQL_DOCKER_PATH=${YOUR_PATH}
```

### 2. Docker pull ruby

`
docker pull ruby:2.4.0
`

### 3.Create Image

  * create image
  
    ```
    docker build -t developer_name/${PWD##*/} --build-arg RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} . && docker images
    ```

### 4. Create Rails

```
docker run --rm -it -v "$PWD":${RAILS_MYSQL_DOCKER_PATH} developer_name/${PWD##*/} rails new . -BT
```

```
Overwrite /${HOME}/.../${RAILS_PROJECT_NAME}/.gitignore? (enter "h" for help) [Ynaqdh] Y
    conflict  Gemfile
```
-> Enter `N`

### 5. Start application

```
#docker run -d -p 3000:3000 -v "$PWD":${RAILS_MYSQL_DOCKER_PATH} developer_name/${PWD##*/} && docker ps && open http://localhost:3000
```

### 6. Re-build for docker-compose

  - update `docker-compose` to `1.12.0`

```
curl -L https://github.com/docker/compose/releases/download/1.12.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

`
cp database.yml config
`

```
docker-compose build --build-arg RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} app
```

### 7. Start docker-compose

```
docker-compose down && docker-compose up && docker-compose ps
```

### 8. Create database

```
RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} docker-compose run --rm app rake db:create
```

### 9. create model

```
RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} docker-compose run --rm app rails generate model Appricant user_name:string
```

### migrate
```
RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} docker-compose run --rm app rake db:migrate
```

  
  
