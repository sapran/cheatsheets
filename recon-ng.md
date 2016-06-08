## Useful queries

~~~
query select distinct host,ip_address from hosts
~~~

~~~
query select * from hosts where ip_address is NULL and host in (select host from hosts where ip_address is not NULL)
query delete from hosts where ip_address is NULL and host in (select host from hosts where ip_address is not NULL)
~~~

~~~
query select * from hosts where host not like "%.example.com"
query delete from hosts where host not like "%.example.com"
~~~
