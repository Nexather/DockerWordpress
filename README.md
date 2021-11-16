# WordPress
Installation guide for my WordPress website

# Installing docker
1.	`sudo apt update`
2.	`sudo apt install docker.io`
3.	`sudo apt install ca-certificates curl gnupg lsb-release`
4.	`curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`
5.  `echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
6.  `sudo apt update`
7.  `sudo apt install docker-ce docker-ce-cli containerd.io`
8.  `sudo usermod -aG docker nexather` (My linux name is nexather)

# Installing Docker Compose
1. `sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
2. `sudo chmod +x /usr/local/bin/docker-compose`
3. Test with `docker-compose --version`
![image](https://user-images.githubusercontent.com/27169767/141956986-6ea68123-1ba5-4cd5-898a-5b8742475bd3.png)


# Installing WordPress
1. Create a directory, I created /my_wordpress/
2. In that directory, create a file named `docker-compose.yml`
3. Fill it with this: 
```
version: "3.9"
    
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
    volumes:
      - wordpress_data:/var/www/html
    ports:
      - "8000:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data: {}
  wordpress_data: {}
  ```
4. Run `sudo docker-compose up -d` from the project directory to build the containers
5. Go to a web browser and enter http://localhost:8000 in the address bar, you should see something like this:
![image](https://user-images.githubusercontent.com/27169767/141958021-6d5807b5-7349-41bb-88a8-d34900cd204b.png)

# Creating the website
1. Select the language
2. Enter information as requested, I chose to discourage search engine indexing
3. You will now see an admin page similar to this:
![image](https://user-images.githubusercontent.com/27169767/141958446-f460155b-9d9f-4ca9-a325-ba9cbe8dc18c.png)

You are now free to customize to your liking!

Sources:
https://docs.docker.com/samples/wordpress/

