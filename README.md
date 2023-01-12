# prueba-tecnica

[![Diagrama-de-Red.png](https://i.postimg.cc/6qbbTpwG/Diagrama-de-Red.png)](https://postimg.cc/7J7nWD5x)

<h1>Diagrama de red de una app web</h1>

 <h2>Se creó un diagrama de red utilizando microservicios esenciales de AWS, de acuerdo a los requerimientos solicitados. El cual describo a continuación:</h2>

<p> 1. Se inició con una VPC ubicada en una región, la cual abarca tres zonas de disponibilidad, para garantizar una alta disponibilidad a la aplicación web. Cada zona es una réplica de la otra, siendo la AZ 1a la Master.

2. Se creó una DB Private Subnet en donde se alojarán las bases de datos, agregando Amazon RDS para las relacionales, y Amazon DynamoDB, para las no relacionales. Está subnet se encuentra separada, debido a que es contenido crítico.

3. En otra Private Subnet, llamada App Private Subnet, se alojó el backend de la aplicación, la cual se comunica con un NAT Gateway para que pueda tener acceso a Internet, y de esta manera se conecte a los microservicios externos a través del Direct Connect, el cual posibilita conectar la Data Center a AWS, permitiendo así un entorno híbrido.

4. En la Public Subnet se encuentra el frontend de la aplicación, junto al NAT Gateway anteriormente mencionado. Las instancias situadas en esta subnet utilizan Elastic Load Balancing para distribuir automáticamente el tráfico entrante.

5. Se incorporó un Auto Scaling entre la Public Subnet y la App Private Subnet, que ejecuta una administración de instancia, creando o removiendo según sea la necesidad.

6. Todos los recursos estarán almacenados en un Bucket de S3.</p>

