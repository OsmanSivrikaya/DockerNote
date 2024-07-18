# Docker Notları

## Ubuntu Kurulumu
### 🐧 Ubuntu - Ubuntu Kurulumu
- `wsl --install -d ubuntu` - Ubuntu'yu WSL üzerinde kurar.
- `grep -E 'sudo|wheel' /etc/group` - `sudo` kullanıcısını tanımlama.
- `sudo grep -E '%sudo|%wheel' /etc/sudoers` - Tanımlandı mı diye kontrol etmek için `%sudo ALL=(ALL:ALL) ALL` yazması gerek.
- `sudo apt update && sudo apt upgrade` - Güncellemeleri yapar.
- `sudo apt install docker.io` - Docker'ı Ubuntu'ya indirir.

## Docker Komutları
### 🌐 Docker Ağ Yönetimi
- `docker network ls` - Docker'da olan ağları listeler.
- `docker network create mynetwork` - Ağ oluşturur.

### 📋 Docker Container Yönetimi
- `sudo docker ps` - Çalışan containerları sıralar.
- `sudo docker ps -a` - Aktif olup olmayan containerları sıralar.
- `sudo docker stop 'containerId'` - Container durdurur.
- `sudo docker rmi IMAGE_ID or IMAGE_NAME` - Docker image siler.
- `sudo docker container prune` - Exit olan containerları siler.
- `sudo docker image prune` - Kullanılmayan imajları siler.
- `docker system prune` - Tüm konteynerları ve kullanılmayan imajları siler.
- `sudo apt remove docker docker-engine docker.io containerd runc` - Önceki docker kurulumları varsa kaldırır.
- `docker inspect -f "{{.NetworkSettings.IPAddress}}" container-name` - Container IP adresini verir.

## Docker Kurulumları
### 📦 Docker MongoDB Kurulumu
- `docker pull mongo` - MongoDB image indirir.
- `docker run -p 27017:27017 mongo:latest` - MongoDB container ayaklandırır.
- `docker pull mongoclient/mongoclient` - MongoDB client container indirir.
- `docker run -d -p 3000:3000 mongoclient/mongoclient` - MongoDB client container ayaklandırır.

### 📦 Docker MSSQL Kurulumu
- `docker pull mcr.microsoft.com/mssql/server:2022-latest` - MSSQL image indirir.
- `docker run --name sqlserver_container -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=StrongPassword123!' -e 'MSSQL_PID=Developer' -p 1433:1433 -h sqlServer2022 -d mcr.microsoft.com/mssql/server:2022-latest` - MSSQL container ayaklandırır.

### 📦 Docker DBeaver Kurulumu
- `docker run -d -p 8080:8978 --name dbeaver dbeaver/cloudbeaver:latest` - DBeaver container ayaklandırır (username/pass: cbadmin/StrongPassword123!).

### 📦 Docker Redis Kurulumu
- `docker pull redis` - Redis image indirir.
- `docker run --name some-redis -d redis` - Redis containerını ayağa kaldırır.
- `sudo docker exec -it 254df redis-cli` - Redis'e redis-cli ile bağlanma.
- `PING / PIN "MESAJ"` - Ping atıldığında PONG veya mesaj dönüyorsa Redis sunucusu sorunsuz çalışıyor.
- `sudo docker pull redis/redisinsight` - Redis arayüz image indirir.
- `sudo docker run -d --name redisinsight -p 5540:5540 redis/redisinsight:latest` - Redis arayüz container ayaklandırır.
- `sudo docker run -d --name redis-stack -p 1453:6379 -p 8001:8001 redis/redis-stack:latest` - Redis DB ve arayüz ayaklandırma.
- `--raw` - Redis'e bağlandığında Türkçe bağlanmak için.
- `docker exec -it redis-slave redis-cli slaveof MasterRedisIp MasterRedisPort` - Master Redis'ten bir slave oluşturur.
