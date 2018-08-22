compose-up:
	docker-compose up
.PHONY: compose-up

compose-down:
	docker-compose down
.PHONY: compose-down

create-service:
	curl -X POST \
  --url http://localhost:8001/services/ \
  --data 'name=example-service' \
  --data 'url=http://mockbin.org' | jq
.PHONY: create-service

create-route:
	curl -X POST \
  --url http://localhost:8001/services/example-service/routes \
  --data 'paths[]=/hello' | jq
.PHONY: create-service

add-lambda:
	curl POST http://localhost:8001/plugins/ \
		--data "route_id=$(route_id)" \
    --data "name=aws-lambda" \
    --data-urlencode "config.aws_key=AWS_KEY" \
    --data-urlencode "config.aws_secret=AWS_SECRET" \
    --data "config.aws_region=us-east-1" \
    --data "config.function_name=kong-cincinnati-meetup-8-11-18-dev-hello" | jq
.PHONY: add-lambda

add-basic-auth:
	curl -X POST http://localhost:8001/plugins \
		--data "route_id=$(route_id)" \
    --data "name=basic-auth" \
    --data "config.hide_credentials=true"
.PHONY: add-basic-auth

create-consumer:
	curl http://localhost:8001/consumers \
	--data "username=alois&custom_id=1"
.PHONY: create-consumer

create-credential:
	curl -X POST http://localhost:8001/consumers/alois/basic-auth \
    --data "username=alois" \
    --data "password=password"
.PHONY: create-credential
