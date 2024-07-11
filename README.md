- **Ubuntu - ubuntu kurulumu**
- wsl --install -d 
- grep -E 'sudo|wheel' /etc/group - sudo kullanıcısını tanımlama
- sudo grep -E '%sudo|%wheel' /etc/sudoers - tanımlandımı diye kontrol etmek için %sudo ALL=(ALL:ALL) ALL yazması gerek
- sudo apt update && sudo apt upgrade - güncellemeleri yapıyoruz
- sudo apt install docker.io - docker ubunutya indirmek için

- docker network ls - dockerda olan ağları listeler
- docker network create mynetwork - ağ oluşturur
- sudo docker ps - Çalışan containerları sıralama 
- sudo docker ps -a - Aktif olup olmayan containerları sıralama
- sudo docker stop 'containerId' - container durdurma
- sudo docker rmi IMAGE_ID or IMAGE_NAME - docker image silme
- sudo docker container prune - exit olan containerları siler
- sudo docker image prune - Kullanılmayan imajları siler
- docker system prune - tüm konteynerları ve kullanılmayan imajları siler
- sudo apt remove docker docker-engine docker.io containerd runc - önceki docker kurulumları varsa kaldırır

- **docker mongo kurulumu**
- mongo indiriyoruz - docker pull mongo
- mongoyu ayaklandırıoyurz - docker run -p 27017:27017 mongo:latest 
- mongo client container indiriyoruz -  docker pull mongoclient/mongoclient
- mongo client container run ediyoruz - docker run -d -p 3000:3000 mongoclient/mongoclient

- **docker mssql kurulumu**
- docker pull mcr.microsoft.com/mssql/server:2019-latest - mssql image indiriyoruz
- docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyPassword123!" \
- -p 1433:1433 --name sql_server_container \
- -d mcr.microsoft.com/mssql/server:2019-latest - image ayaklandırıyoruz

- **redis kurulumu**
- docker pull redis - redis image indirir
- docker run --name some-redis -d redis - redis containerını ayağa kaldırır
- sudo docker exec -it 254df redis-cli - redis'e redis-cli ile bağlanma
- PING / PIN "MESAJ" - ping atıldığında PONG veya mesaj dönüyorsa redis sunucusu sorunsuz çalışıyor 
- sudo docker pull redis/redisinsight - redis arayüz image indirir
- sudo docker run -d --name redisinsight -p 5540:5540 redis/redisinsight:latest - redis arayüz container ayaklandırır
