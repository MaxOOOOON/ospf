# ospf

## ДЗ

    Поднять три виртуалки
    Объединить их разными vlan
    поднять OSPF между машинами на базе Quagga;
    изобразить ассиметричный роутинг;
    сделать один из линков "дорогим", но что бы при этом роутинг был симметричным.

---

## Выполнение      

### Топология сети      

![](https://github.com/MaxOOOOON/ospf/blob/main/pictures/image.png)    


1. Изобразить ассиметричный роутинг 

Необходимо измененить стоимость интерфейса eth2 на r1   

![](https://github.com/MaxOOOOON/ospf/blob/main/pictures/Screenshot_20211104_231700.png)    

2. Сделать один из линков "дорогим", но что бы при этом роутинг был симметричным.   

Так же необходимо изменить стоимость на другой стороне vlan ( r3 , интерфейс eth1 )     

![](https://github.com/MaxOOOOON/ospf/blob/main/pictures/Screenshot_20211104_233953.png)  

![](https://github.com/MaxOOOOON/ospf/blob/main/pictures/Screenshot_20211115_002118.png)  

Заметки:    
Для того чтобы выполнить сохранение конфигурации, необходимо перевести zebra_write_config в состояние On либо отключить selinux и выполнить в vtysh     

    copy  running-config  startup-config
