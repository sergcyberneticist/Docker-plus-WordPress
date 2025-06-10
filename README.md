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
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data:

5. In PowerShell finding created folder "WordPress" and execute command:
  docker-compose up –d
3. Open a browser and follow the link "http://localhost:8000".
   Complete the installation "WordPress".
