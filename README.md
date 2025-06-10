# Docker-plus-WordPress
notes to myself

Creating project in Windows 10 or later:

1. Starting PowerShell in admin mode.
  Installing WSL 2
  input command: wsl --install
2. Installing "Docker desktop"
   from "https://docs.docker.com/desktop/setup/install/windows-install/" and run it.
3. In any convenient location creating folder "WordPress"
   in this folder creating file "docker-compose.yml" with content:

```yaml
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
      - "8080:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data:
```

4. In PowerShell finding created folder "WordPress" and execute command:
  docker-compose up –d
5. Open a browser and follow the link "http://localhost:8080".
   Complete the installation "WordPress".
