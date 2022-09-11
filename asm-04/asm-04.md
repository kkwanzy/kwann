“คอนเทนเนอร์” (container) เป็นเทคนิคในการจัดการ package software ประเภทหนึ่ง นิยามของ Containers เปรียบเสมือนตู้ Container ที่อยู่บนเรือที่สามารถยกเข้า/ยกออกได้ เมื่อมีการ build หรือใส่ของเข้าไปเเล้วเราจะไม่สามารถเเก้ไขของข้างในได้สิ่งนี้เรียกว่า “ตัวต้นแบบ” หรือว่า Container Image


https://www.docker.com/resources/what-container/
1ตรวจสอบให้แน่ใจว่าทุกสภาพแวดล้อมเหมือนกัน:คอนเทนเนอร์แก้ไขปัญหาของแอปพลิเคชันที่ทำงานไม่ถูกต้องเมื่อย้ายจากสภาพแวดล้อมหนึ่งไปยังอีกสภาพแวดล้อมหนึ่ง โดยใช้เป็นตัวต้นแบบนั้นไม่สามารถแก้ไขได้

2.ช่วยบรรจุรหัสแอปพลิเคชัน:คอนเทนเนอร์ช่วยรวมโค้ดของแอปพลิเคชันเข้ากับไฟล์การกำหนดค่าและไลบรารีที่เกี่ยวข้อง และมีการพึ่งพาที่จำเป็นสำหรับแอปที่จะเรียกใช้

3 Portable applications:แอปพลิเคชัน การขึ้นต่อกัน และการกำหนดค่าของแอปพลิเคชันนั้นถูกรวมเข้าด้วยกันเป็นอิมเมจคอนเทนเนอร์ อินสแตนซ์อิมเมจคอนเทนเนอร์สามารถปรับใช้กับโฮสต์ OS สำหรับแต่ละสภาพแวดล้อมได้

ตัวอย่าง web application
“static files” ใน term ของ web application (Frontend) => Web browser

1. Client Side Rendering (CSR) ใช้เครื่อง Client ในการ Render .html (ผ่าน browser)

2.Server Side Rendering (SSR) render ที่ server แล้วมีการส่ง .html กลับมา

3. Static Site Generation (SSG) ไม่มีการ render คือเป็น file .html เปล่าๆ

Container Runtime Engine

ตัวที่นิยมใช้ คือ Docker

การสร้าง Container ==>” Containerization “

Concept ของ Docker

1. Dockerfile => ขั้นตอนในการสร้าง container image , โค้ดจะเขียนใน Dockfile ทั้งหมด

2.Image ==> ตัวต้นแบบเมื่อสร้างขึ้นมาเเล้วไม่สามารถแก้โค้ดได้ อ่านได้อย่างเดียว ถ้าต้องการแก้ไขต้องสร้างโค้ดขึ้นมาใหม่

3. Container Instance ==> การสร้างตัวทำงานจาก image หรือตัวต้นแบบ

4. Registry ==> ส่วนกลางที่เอาไว้เก็บ Container Image

Docker Command
- dockerbuild ==> run คำสั่งจาก Dockerfile ให้เป็น Docker image ใน local lmage cache

$docker build -t <image-name>:<tag> <directory>

(-t)=tag: ต้องระบุเสมอ ถ้าเราไม่ระบุมันจะใส่ latest registry

directory: context ที่ dockerfile อยู่

- docker image ==> command ที่โชว์ทุกตัวของ top level images

$ docker images

- Contaner Registry ==> ที่เก็บ image มี 2 ประเภท

1. Local ==> ที่เก็บ image ทั่วไป

2. Public ==> ที่เก็บ image เฉพาะกลุ่ม เช่น Cloud

- docker pull ==> ดึง container image ที่ public registry มาเก็บที่ local registry

$ docker pull python:3.9.6

- docker run ==> ดึง container image มาclone เป็น container instance โดยใช้คำสั้ง run

$ docker run -d -p <server-port>:<container-port> <image-name>:<tag>

(-d) = daemon mode

(-p) = port

- docker push ==> นำข้อมูลไปเก็บบน cloud หรือ public registry

$ docker push <image-name>:<tag>

- docker ps ==> แสดงรายละเอียดของ container instance ที่มีการ start การทำงาน
v
$ docker ps <option>

- docker logs ==>การเช็ค logs ของ application ที่อยู่ใน container

$ docker logs <container-id> <option>

- docker exec ==> ใช้run command ใน container

$ docker exec -it <container-id> <shell>

<shell> คือคำสั่งที่ต้องการเข้าใช้