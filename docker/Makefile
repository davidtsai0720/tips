.PHONY: create-db
create-db: 
	@docker run --name postgres -itd --restart always \
        --publish 5432:5432 \
        -v ${PWD}/pg-data:/var/lib/postgresql/data \
        -e POSTGRES_PASSWORD=postgres \
        -e POSTGRES_USER=postgres \
        -e POSTGRES_PORT=5432 \
        -e POSTGRES_DB=db \
        postgres:14.2-alpine
