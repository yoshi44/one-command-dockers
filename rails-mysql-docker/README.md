# Create Docker

Set environment variables

As your current directory 
`
export RAILS_MYSQL_DOCKER_PATH=$PWD
`

OR

Your rails project path
`
export RAILS_MYSQL_DOCKER_PATH=${YOUR_PATH}
`

`
docker pull ruby:2.4.0
`

Create Image

```
docker build -t developer_name/"${PWD##*/}" --build-arg RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} .
```
