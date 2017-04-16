# 

`
export RAILS_MYSQL_DOCKER_PATH=$PWD
`

`
docker pull ruby:2.4.0
`

`
docker build -t developer_name/"${PWD##*/}" .
`
