# laradock
Settings for install Laravel in docker.
# First Step
Install Docker

# Second Step
Install the Laravel version you need.
After run command - docker run --rm -v $(pwd):/app composer install
After edit permissions app directory 
sudo chown -R $USER:$USER ~/laravel-app

# Third Step
Edit docker-compose.yml
After run docker-compose up -d
Edit .env file
  DB_CONNECTION=mysql
  DB_HOST=db
  DB_PORT=3306
  DB_DATABASE=your_database
  DB_USERNAME=your_user_from_docker_compose_yml
  DB_PASSWORD=your_laravel_db_password_from_docker_compose_yml
  
  Run docker-compose exec app php artisan key:generate
  Run docker-compose exec app php artisan config:cache
  
  # Fourth Step
  You need create user, which register in container
   docker-compose exec db bash
   mysql -u root -p
   "Enter password from docker-compose.yml"
   Create user - GRANT ALL ON laravel.* TO 'user'@'%' IDENTIFIED BY 'your_laravel_db_password';
   Run FLUSH PRIVILEGES; to save changes
