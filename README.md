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
1. 
