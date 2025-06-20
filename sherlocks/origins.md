Buenasss
Sherlock Hack The box origins
![image](https://github.com/user-attachments/assets/f86be3f4-9896-4a1a-9770-fb647959beb6)

Recientemente se produjo un incidente grave en Forela. Se robaron aproximadamente 20 GB de datos de buckets S3 internos y los atacantes ahora están extorsionando a Forela. Durante el análisis de la causa raíz, se sospechó que un servidor FTP era el origen del ataque. Se descubrió que este servidor también se vio comprometido y se robaron algunos datos, lo que provocó nuevas infracciones en todo el entorno. Se le proporciona un archivo PCAP mínimo. Su objetivo es encontrar evidencia de fuerza bruta y exfiltración de datos.

Como se menciona que posiblemente el ataque proviene de un servidor ftp (protocolo de transferencia de archivos) realizamos la busqueda con este filtro "ftp-data'
![image](https://github.com/user-attachments/assets/0ba23514-6b7b-4386-bac5-c491f616aac3)
La siguienta pregunta es de que ciudad es esta ip
![image](https://github.com/user-attachments/assets/52ade47e-1846-433b-9229-43bdb66a803a)

La siguiente pregunta es "Que aplicacion utilizo el servidor de respaldo" y nuevamente filtramos ahora solo por fpt
![image](https://github.com/user-attachments/assets/783c5540-217b-421d-9c1e-ff361e8f70cf)

Nos preguntan a que hora se inicio el ataque de fuerza bruta, no es dificil identificar ya que podemos ver todas las solicitudes desde admin
![image](https://github.com/user-attachments/assets/d8a6fef1-0cb9-47c7-82cb-d362224f66bb)

La siguiente pregunta es cuales fueron las credenciales correctas con las que logro entrar, podemos filtramos por el resquest PASS,pero con el ftp nos encontramos el usuario que logro iniciar luego de muchos intentos fallidos
![image](https://github.com/user-attachments/assets/71615c4e-6694-4a13-9552-54c838207148)

Nos piden el comando que se utilizo para descargar archivos remotos, esto lo podemos ver al momento que se hace una solicitud a un archivo pdf
![image](https://github.com/user-attachments/assets/c5abee4b-409b-4676-a8c2-319673bf2f95)

Indican que se comprometieron las credenciales de un servicio ssh y cuales fueron esta, esto los vemos en el pdf indicado anteriormente,exportamos el paquete
![image](https://github.com/user-attachments/assets/bc85e101-cb02-48aa-8e87-5c6b941000da)

Lo siguiente que se nos pregunta es la url para el archivo de datos y eso lo encontramos en el s3 que es un txt
![image](https://github.com/user-attachments/assets/c99665a6-d0f7-49cc-86ad-de54ddbf35de)

la ultima pregunta es cual es la direccion de correo electronico que uso el atacante y la vemos el emismo archivo que exportamos
![image](https://github.com/user-attachments/assets/fc086572-69dc-4225-9266-0282afd39a41)

Amarramos 
![image](https://github.com/user-attachments/assets/3dd95b6a-e0aa-44ad-af79-a18efe33bab5)
