Kiểm tra docker đã cài chưa 
$docker --version

để download server nginx
$docker pull nginx

chạy nginx
$docker run -it -p 8080:80 nginx
giúp xem được cả logs bên trong 

truy cập /localhost:8080

cái download gọi là init
còn cái run thì gọi là container

để xem tất cả các container đang chạy 
$ docker ps

để xem image đang có
$docker images

liệt kê tất cả các container kể cả đang chạy và đã dừng 
$ docker ps -a

muốn xóa container
$docker rm <ID container>

chú ý container đang chạy thì không remove được
phải dừng container rồi xóa
$docker stop <ID container>

để xóa image  server nginx
$docker rmi nginx

xóa image bằng ID
$docker rmi <ID>

một lệnh run khác :
$docker run -d -p 8080:80 nginx
(-d : detach  : Run container in background and print container ID 
$docker run --help để xem options)

để chạy lại container
$docker start <name container>

$docker stop <name container>

$docker rm <name container>

kiểm soát tên container
$ docker run -d -p 8080:80 --name mynginx nginx


để vào được bên trong container ( virtual server)
$ docker exec -it mynginx bash

#cat /usr/share/nginx/html         : nội dung của trang chủ nginx

muốn có 1 file html mới 


Khái niệm volume : truyền dữ liệu từ ngoài vào container
$docker run -d -p 8080:80 --name mynginx -v "E:\CLOUD\Docker\html":/usr/share/ngin nginx
(-v : lấy volume từ ngoài vào container cần chạy)
("C:\Users\THE TRONG\Desktop\CLOUD\Docker\html": /usr/share/nginx/html - map file html bên ngoài vào container nginx)
Chú ý : phải dùng git bash mới chạy được 


in ra logs trong container
$docker logs mynginx

muốn lấy ra log của container: 
$docker run -d -p 8080:80 --name mynginx -v "E:\CLOUD\Docker\html":/usr/share/nginx/html -v "E:\CLOUD\Docker\logs": /var/log/nginx nginx
                                        map html từ ngoài vào container                 map ngược lại file log của container vào file tên log bên ngoài
                                                                                        chỉ cần nhập tên file logs tự tạo

map folder

Dockerfile
là một cái hướng dẫn để docker tạo ra 1 image của mình từ một image gốc nào đó
khi tạo xong nó sẽ tự động copy image này luôn

để xây dựng được image này :  image riêng của mình
$ docker build -t my_nginx_vietnam .
( -t: tag  )

run container từ image vừa tạo
$docker build -t nginx-thetrong my_nginx_vietnam
------> docker build -t <hub-user>/<repo-name>[:<tag>]  <----

    (nginx-thetrong : tên container) my_nginx_vietnam : image của container

để đẩy image của mình lên dockerhub

trước tiên phải tag
$docker tag my_nginx_vietnam:1.0 thetrong/my_nginx_vietnam:26.11.21
--------> docker tag <existing-image> <hub-user>/<repo-name>[:<tag>] <-------------

login hub.docker trước khi push
$docker login

để push
----> docker push <hub-user>/<repo-name>:<tag>      <-----------
$docker push thetrong/my_nginx_vietnam:26.11.21

To commit changes
----> docker commit <existing-container> <hub-user>/<repo-name>[:<tag>] <----------
