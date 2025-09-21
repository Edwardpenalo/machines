BUENAS
Aqui realizando el sherlock Neurosync el cual se encuentra en la categoria DFIR de hack the box nivel easy


<img width="1431" height="524" alt="image" src="https://github.com/user-attachments/assets/daa9f7f6-03f8-4e41-9515-24d8e86c325a" />

Aqui podemos encontrar la version de Nextjs y el puerto local el cual corre la misma

<img width="1386" height="420" alt="image" src="https://github.com/user-attachments/assets/5ace3f3a-ee76-4a15-b017-e65320ed1a62" />

Aqui tenemos la vulnerabilidad CVE-2025-29927 esta se aprovecha de Se debe a una confianza inadecuada en el encabezado aqui el recurso "https://www.offsec.com/blog/cve-2025-29927/" 

<img width="1225" height="783" alt="image" src="https://github.com/user-attachments/assets/9a8ea57d-a647-448e-8b0d-e7d13b984cf5" />


Los archivos ennumerados por el atacante encontramos a main-app.js
<img width="1679" height="710" alt="image" src="https://github.com/user-attachments/assets/d0696e0c-a5a4-4d65-8849-f74fbf472aa5" />

El endpoint abusado es donde se encuentra la api de esta misma
<img width="1504" height="707" alt="image" src="https://github.com/user-attachments/assets/e43577d8-1ebf-492f-9cdd-8c3266de8787" />
 respuesta exitosa del punto final vulnerable
<img width="1223" height="85" alt="image" src="https://github.com/user-attachments/assets/480db6ca-0226-46ba-b9c3-603ee48ab738" />
Las solicitudes al endpoint como rechazadas

<img width="1231" height="695" alt="image" src="https://github.com/user-attachments/assets/499b11cf-3625-4cc8-a8e0-97396f4e7ad9" />

El atacante inicia un ataque de fuerza bruta para encontrar endpoints vulnerables en la API aqui tenemos "logs" que el atacante abusa de esta
<img width="1262" height="692" alt="image" src="https://github.com/user-attachments/assets/5c2350b4-d614-4bdb-80ac-a3066fd0faa8" />

La vulnerabilidad funciona de esta forma
<img width="1198" height="865" alt="image" src="https://github.com/user-attachments/assets/b1664954-f7df-4ead-bee4-aa41d3f1270a" />

el nombre del archivo que fue atacado la última vez
<img width="1192" height="671" alt="image" src="https://github.com/user-attachments/assets/861ead1a-c17f-4c3e-9124-517f9bb2d640" />

el atacante utiliza la información confidencial obtenida previamente para crear un comando especial que le permite realizar una inyección de Redis y obtener RCE en el sistema y lo vemos aqui presente
<img width="1229" height="501" alt="image" src="https://github.com/user-attachments/assets/82e00194-b199-471f-83b9-e0098d77a4b3" />

Luego de decodificar el comando utilizado es este
<img width="1238" height="476" alt="image" src="https://github.com/user-attachments/assets/19c695ca-f7b6-40b7-bf7c-08dbe76fcbdd" />

Logramos completar este sherlock

<img width="704" height="716" alt="image" src="https://github.com/user-attachments/assets/b0821c4e-2972-42a2-a93c-5989af1e720e" />



El Sherlock NeuroSync-D permitió entender la forma en la que un atacante puede aprovechar configuraciones inseguras y vulnerabilidades conocidas en aplicaciones modernas como Next.js. La explotación de CVE-2025-29927, sumada a la exposición indebida de endpoints, condujo a un RCE vía Redis, mostrando la importancia de:

Mantener frameworks actualizados.

Restringir el acceso a archivos de cliente y rutas internas.

Implementar monitoreo y rate limiting en APIs.

Revisar periódicamente logs para detectar comportamientos anómalos.
