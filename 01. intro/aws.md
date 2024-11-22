# AWS

## Qué es?

- Amazon Web Services (aws) es un provedor de nube.
- Ofrecen sus servers y servicios para que los usemos on demand y podamos escalar facilmente.

## Lo que aprendemos

![Servicios](../docs/01.%20intro/lo_que_aprenderemos.png)


## AWS Historia

- 2002: lanzado internamente
- 2003: Idea de lanzar su infra al mercado
- 2004: Lanzan su infra publica con SQS
- 2006: relanzamiento con S3, EC2 Y SQS
- 2007: Lanzado en Europa
- 2007 hasta ahora: dropbox, netflix, lo usan

## AWS Infraestructura global

- AWS regions
- AWS Availability zones
- AWS Data centers
- AWS Edge Locations / Points of presence


Vamos a explicar cada uno de estos basandonos en la Región de **São Paulo (sa-east-1)**. 

### AWS regions

- AWS tiene regiones alrededor del mundo
- Es una ubicación geografica
- Ejmplos del nombre: us-east-1, eu-west-3, sa-east-1, etc
- Una región es un cluster de datacenters (un conjunto de datacenters).
- A su vez, una región está compuesta por multiples AZ

#### Ejemplo:
- **São Paulo (sa-east-1)** esta región tiene sus principales servicios en ejecución aquí.

#### ¿Cómo elegir una region?

Factores para elegir una región:
- Cumplimiento con el gobierno de datos y requisitos legales.
- Proximidad a los clientes.
- Servicios disponibles
- Precio


### AWS Availability zones (az)

- Cada region tiene muchas zonas de disponibilidad (Normalmente 3, minimo 3, maximo 6)

![Regiones](../docs/01.%20intro/regiones.png)

- Cada AZ es uno o más **data centers** con energía redundante.
- AZ están sepradas entre ellas (ubicaciones geograficas distintas), para aislarlas de desastres.
- Tienen conexión entre ellas con altisima banda ancha, con latencia ultra baja en la red.
- Redundancia y alta disponibilidad
- Sirve para la tolerancia a fallos, no para escalabilidad (cuando se configura multi az en servicios donde su DataPlane no es distribuido automaticamente).

*Nota: **São Paulo (sa-east-1)** tiene multiples AZ, no necesariamnete están en la misma ciudad o ubicación exacta de Sao Paulo. AWS las separa fisicamente para mitigar riesgos de desatres naturales o interrupciones* 

#### Ejemplo:
- Si tengo una instancia EC2 en la región sa-east-1, aws replicara automaticamente el control plane entre las 3 AZ, pero mi instancia fisicamente estará en una sola AZ (yo soy quien debe garantizar la replica de mi instancia, es decir el Data Plane).

### AWS Edge Locations / Points of presence

- AWS tiene más de 400 points of presence (400+ Edge locations y más de 10 Regional Caches) en más de 90 ciudades en más de 40 paises. 
- Se entrega contenido al usuario final con baja latencia. 
- no forman parte de una región específica. En cambio, están diseñadas para acercar contenido (como archivos cacheados de CloudFront) a los usuarios finales.
- Aunque São Paulo es una region de AWS (la región base en América del Sur), las Edge Locations están distribuidas en diferentes ciudades para ofrecer una experiencia de baja latencia.

#### Ejemplo
- Si un usuario en Medellin solicita un archivo que está cacheado, el archivo será entregado desde la Edge Location más cercana en Bogotá, en lugar de desde São Paulo.

### Regional Caches
- Una Regional Cache es una capa adicional de almacenamiento intermedio utilizada por CloudFront para mejorar el rendimiento.
- Se encuentra en la región principal más cercana (São Paulo, en este caso) y sirve para:
    - Reducir la carga en los servidores de origen.
    - Almacenar contenido que no está presente en una Edge Location, pero que es solicitado frecuentemente.

#### Ejemplo:
- Si desde medellin solicito un archivo, y no está en la Edge Location más cercana (Bogotá), la solicitud se envia a la Regional Cache en Sao Paulo. Supongamos que tampoco está en la Regional Cache, entonces toca ir hasta el servidor de origen, por ejemplo S3 en Sao Paulo.  

### Ejemplo America del Sur

La nube de AWS en América del Sur tiene tres zonas de disponibilidad distribuidas en una región geográfica, así:

**Region:** sa-east-1

**AZs:** sa-east-1a, sa-east-1b, sa-east-1c

**Edge Locations:**: Bogotá, Colombia; Buenos Aires, Argentina; Fortaleza, Brasil; Lima, Perú; Río de Janeiro, Brasil; São Paulo, Brasil; Santiago de Chile, Chile

**Regional Caches:** São Paulo, Brasil


## Breve Tour de aws

### Servicios Globales (funcionan en todas las regiones)
- IAM (Identity and access management)
- Route 53 (DNS service)
- CloudFront (Content delivery network)
- WAF (Web Application Firewall)

### La mayoría de servicios aws tiene un ambito regional:

La mayoría de servicios tienen ambito regional, lo que significa que están disponibles para ciertas regiones. 

- EC2
- Lambda
- Rekognition

### Servicios aws por region

[Servicios por region (click aquí)](https://aws.amazon.com/es/about-aws/global-infrastructure/regional-product-services/)

### Infra global

[Infra global (click aquí)](https://aws.amazon.com/es/about-aws/global-infrastructure)



