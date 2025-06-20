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

