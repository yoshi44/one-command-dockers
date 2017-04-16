# Create Docker

`
export RAILS_MYSQL_DOCKER_PATH=$PWD
`

`
docker pull ruby:2.4.0
`

Create Image

`
docker build -t developer_name/"${PWD##*/}" --build-arg RAILS_MYSQL_DOCKER_PATH=${RAILS_MYSQL_DOCKER_PATH} .
`
