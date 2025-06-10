# Docker-plus-WordPress
notes to myself

Creating progect in Windows 10 or later:

1. Starting PowerShell in admin mode.
  Installing WSL 2
  input command: wsl --install
2. Installing "Docker desktop"
   from "https://docs.docker.com/desktop/setup/install/windows-install/" and run it.
4. In any convenient location creating folder "WordPress"
   in this folder creating file "docker-compose.yml" with content:
version: '3.3'
services:
  wordpress:
    image: wordpress:latest
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user
      WORDPRESS_DB_PASSWORD: password
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wordpress_data:/var/www/html

  db:
    image: mysql:5.7
    restart: always
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: user
      MYSQL_PASSWORD: password
      MYSQL_ROOT_PASSWORD: rootpassword
    volumes:
      - db_data:/var/lib/mysql

volumes:
  wordpress_data:
  db_data:

5. In PowerShell finding created folder "WordPress" and execute command:
  docker-compose up –d
3. Open a browser and follow the link "http://localhost:8000".
   Complete the installation "WordPress".
