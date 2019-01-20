## Links
[Как установить Nginx в Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/nginx-ubuntu-18-04-ru)  
[Как настроить брандмауэр с UFW в Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04)  

## Commands
### установить nginx
`sudo apt update`  
`sudo apt install nginx`  

если какой-то процесс слушает порт 80, установка закончится неудачей.  
значит нужно убить процессы слушающие порт 80 и повторить установку

- узнать что слушает порт 80  
  `sudo netstat -tulpn | grep --color :80`  
- узнать PID слушающих порт 80  
  `sudo fuser 80/tcp`
- убить все эти процессы  
  `sudo kill -9 <PID>`
- повторить установку  
  `sudo apt install nginx`



### проверка файрвола  
`sudo ufw app list`  
`sudo ufw allow 'Nginx HTTP'`
`sudo ufw enable`  
`sudo ufw status`  

### проверить работает ли сервер  
`systemctl status nginx`  

### узнать свой IP  
`curl -4 icanhazip.com`  

`sudo systemctl stop nginx`  
`sudo systemctl start nginx`  
`sudo systemctl restart nginx`  
`sudo systemctl reload nginx`  
`sudo systemctl disable nginx`  
`sudo systemctl enable nginx`  
