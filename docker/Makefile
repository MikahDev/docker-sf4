PHP_SERVICE := dsa_php
COMPOSER_ARGS ?= install
 
build:
	@docker-compose up -d
 
composer:
	@docker-compose exec -T $(PHP_SERVICE) composer $(COMPOSER_ARGS)
 
database:
	@docker-compose exec -T $(PHP_SERVICE) bin/console doctrine:schema:update
 
test:
	@docker-compose exec -T $(PHP_SERVICE) vendor/bin/php-cs-fixer fix src --rules=@PSR2 --using-cache=no --dry-run --verbose --diff
	@docker-compose exec -T $(PHP_SERVICE) bin/console security:check
 
down:
	@docker-compose down --volumes
	@make -s clean
 
clean:
	@docker system prune --volumes --force
 
all:
	@make -s build
	@make -s composer
	@make -s database
	@make -s test
	@make -s down
	@make -s clean