# Docker-1

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7faa18fd-d3cd-4bdb-8b94-c9440bb72bbb/Untitled.png)

- Docker, bir uygulamanın çalışması için gerekli olan tüm kaynakları (örneğin, işletim sistemi, kitaplıklar, dosyalar) ve bağımlılıkları içeren "konteyner"lar oluşturmanıza ve dağıtmanıza olanak tanıyan bir araçtır. Bu sayede uygulamaların farklı ortamlarda ve farklı sistemlerde sorunsuz bir şekilde çalışmasını sağlar.
- Docker’a neden ihtiyaç var?
    - virtual machine ve docker yapıları benzer ama amaçları farklı
- Docker: An isolated env for apps
- VM: An abstarction of a machine(physical hardware)
- Eğer yapılan değişiklikler containerda çalışıyorsa productionda da çalışacaktır.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4757d92a-c1b8-42eb-a6d4-7feca93a2c89/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f37cbe60-c085-4e61-a7ca-4b67ca27cfdf/Untitled.png)

- VMs lerin ayağa kalkması uzun sürerken Container daha hızlı .
- Container daha az yer kaplar

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b7350be3-9e15-4543-b5e7-e5c0ca68c06a/Untitled.png)

- noktaları takip et!!
- herkes için ortak env oluşturmak
- mikroservis mimarisi
- 

### Docker File

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6f758b09-9c1d-4d53-94ec-3983702a5c51/Untitled.png)

- Docker File : Oluşturulacak imageın Blue printi
- Aslınnda Docker Image da Containerın blue printi

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/63d22a35-9079-4a95-afe7-1a137399b2ed/Untitled.png)

- İlk  amaç Development’ ta yazılan kodun productionda çalışmasını sağlamak.
- Herkes için same env sağlamak
- Hatalara daha hızlı response göstermek
- Birçok container oluşturup farklı containerlarda farklı hizmetler sunulabiliyor.

# Lesson-2

- Create [apps.py](http://apps.py) //”print(”hello world”)
- create a dockerfile

```docker
FROM python:alpine3.17
WORKDIR /app # app diye bi klasör oluşturup kaydet
COPY . .
RUN # build aşamasında kullanılan komut
CMD # build bittikten sonra
```

- docker build . ile build işlemi
- docker images or docker image ls ile oluşturulan image ları gösterir
- docker build -t hello-world:1 . ile hello world adında image create ettik
- docker rm hello-world:1 for delete an image
- docker container prune stop eden containerları siler

## SUMMARY

- create a docker file :from python
- WORKDIR oluştur
- COPY . .           ilk kısım localdeki filelar ikinci kısım container
- CMD  python [apps.py](http://apps.py)  apps.py ile çalışması isteniyor
- *docker build .* ile create docker
- *docker build -t hello-world:1* create image  as a hello-world
- *docker image* or *docker image ls*  show all images
- *docker run hello-world:11* ile oluşturulan image’dan container create
- *docker ps* ile çalışan container görünür
- *docker ps -a* ile çalışan çalışmayan tüm containerlar görünür
- *docker run -it hello-world:11* sh ile oluşturulan containerda işlem yapılabilir
- *docker rmi (-f) hello-world:11* ile sil , -f ile force et
- *docker container prune* all unwork cont delete

# Lesson-3

- create a repository in docker hub
- pull işlemiyle oluşturulan repoyu kendi PC mizde çalıştırabiliriz
- docker tag hello-world:1 onarman/hello-world:2
- *docker tag hello-world:1 onarman/hello-world:2*
- *docker push onarman/hello-world:2* ile tekrar push ettik
- *docker pull onarman/hello-world:2* ile locale çektik
- *docker run onarman/hello-world:2* ile cont ayağa kaldırdık