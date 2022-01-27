## 1.

>docker pull valdis171186/netology-devops-dz-20_1

## 2.

> Высоконагруженное монолитное java веб-приложение;
> > Так как приложение высоконагруженное и монолитное, то я думаю необходмы выделеные ресурсы, поэтому считаю что необходимо использовать VM

>Nodejs веб-приложение;
> > Можно использовать Docker, так как не требуется большое потребления ресурсов и приложение выполняет единствуенную задачу

> Мобильное приложение c версиями для Android и iOS;
> > Использование Docker позволит создавать образы для разных версии ОС

> Шина данных на базе Apache Kafka;
> > Лучше использовать VM, так как шина данных является наиболее узким местом Kafka и требует большое количество ресурсов

> Elasticsearch кластер для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana;
> > Так как каждая из нод будет выполнять только свою определенную задачу, то лучше использовать Docker, что позволит по максимуму использовать ресурсы хост машины.

> Мониторинг-стек на базе Prometheus и Grafana;
> > Если метрик для мониторинга не много, то можно запустить Prometheus в контейнере Docker, так как по дефолту использование контейнера приводит к уменьшению количества хранимой информации.

> > Grafana лучше запускать на отдельной VM, так как помимо веб сервера есть еще БД, что не совсем вписывается в идеологию docker- один контейнер один сервис
 
> MongoDB, как основное хранилище данных для java-приложения;
> > Хранение данных в docker контейнере неприемлема, так как при рестарте данные сотруться, но можно запустить в Docker MongoDB и примонтировать локальное харнилище.

> Gitlab сервер для реализации CI/CD процессов и приватный (закрытый) Docker Registry.
> > для сервера Gitlab можно использовать Docker. для приватного же Docker Registry лучше использвать отдельную VM, так как могут возникнуть проблемы с безопасностью у Docker контейнера, в случае какого то воздействия на хост машину.


## 3.

```commandline
pugachevvv@debian-vlad:~/Документы/Netology/DevOps/dz_№20/zadanie_3$ sudo docker exec -it centos bash
[root@ace1fec39da5 /]# ls
bin  data  dev	etc  home  lib	lib64  lost+found  media  mnt  opt  proc  root	run  sbin  srv	sys  tmp  usr  var
[root@ace1fec39da5 /]# cd data
[root@ace1fec39da5 data]# ls
1  2
[root@ace1fec39da5 data]# touch centos
[root@ace1fec39da5 data]# exit
exit
pugachevvv@debian-vlad:~/Документы/Netology/DevOps/dz_№20/zadanie_3$ sudo docker exec -it debian bash
root@8bd10f9ab459:/# cd data/
root@8bd10f9ab459:/data# ls
1  2  centos
root@8bd10f9ab459:/data# touch debian
root@8bd10f9ab459:/data# exit
exit
pugachevvv@debian-vlad:~/Документы/Netology/DevOps/dz_№20/zadanie_3$ ls /data
1  2  centos  debian
pugachevvv@debian-vlad:~/Документы/Netology/DevOps/dz_№20/zadanie_3$ 


```