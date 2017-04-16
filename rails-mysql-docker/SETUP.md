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
    docker build -t developer_name/"${PWD##*/}" --build-arg RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} .
    ```

### 4. Create Rails

```
docker run --rm -it -v "$PWD":${RAILS_MYSQL_DOCKER_PATH} developer_name/${PWD##*/} rails new . -BT
```

```
Overwrite /${HOME}/.../${RAILS_PROJECT_NAME}/.gitignore? (enter "h" for help) [Ynaqdh] Y
    conflict  Gemfile
```
-> Enter `Y`

### 5.

```
docker run -d -p 3000:3000 -v "$PWD":${RAILS_MYSQL_DOCKER_PATH} developer_name/${PWD##*/}
```
