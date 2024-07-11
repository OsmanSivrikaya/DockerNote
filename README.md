Çalışan containerları sıralama sudo docker ps 
Aktif olup olmayan containerları sıralama sudo docker ps -a

sudo docker stop 'containerId' - container durdurma
sudo docker rmi IMAGE_ID or IMAGE_NAME - docker image silme
sudo docker container prune - exit olan containerları siler
sudo docker image prune - Kullanılmayan imajları siler
docker system prune - tüm konteynerları ve kullanılmayan imajları siler

docker mongo kurulumu 
mongo indiriyoruz - docker pull mongo
mongoyu ayaklandırıoyurz - docker run -p 27017:27017 mongo:latest 
mongo client container indiriyoruz -  docker pull mongoclient/mongoclient
mongo client container run ediyoruz - docker run -d -p 3000:3000 mongoclient/mongoclient

docker mssql kurulumu
docker pull mcr.microsoft.com/mssql/server:2019-latest - mssql image indiriyoruz
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=MyPassword123!" \
-p 1433:1433 --name sql_server_container \
-d mcr.microsoft.com/mssql/server:2019-latest - image ayaklandırıyoruz
