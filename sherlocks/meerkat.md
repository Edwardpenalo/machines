Buenasssss

La chiva que vamos amarrar hoy es 
![image](https://github.com/user-attachments/assets/bfe8c140-cbec-41ee-ae57-b09ebc7fe531)
Como startup de rápido crecimiento, Forela ha estado utilizando una plataforma de gestión empresarial. Lamentablemente, nuestra documentación es escasa y nuestros administradores no son los más expertos en seguridad. Como nuestro nuevo proveedor de seguridad, nos gustaría que revisara algunos datos de PCAP y registros que hemos exportado para confirmar si hemos sido comprometidos.

La primera pregunta que se nos hace es "Creemos que nuestro servidor de la Plataforma de Gestión Empresarial ha sido comprometido. ¿Podría confirmar el nombre de la aplicación que se está ejecutando?" en el archivo json encontraremos esta info, abrimos y buscamos algo parecido a ejecucion o exploit que era lo que estaba buscando.

![image](https://github.com/user-attachments/assets/611b2636-9657-4cfa-ad34-6a4d99da070d)
encontramos el programa y es "BonitaSoft"

"Creemos que el atacante puede haber utilizado un subconjunto de la categoría de ataque de fuerza bruta: ¿cómo se llama el ataque realizado?" Credential Stuffing,Porque creo esto? porque en nuestros trafico vemos multiples intentos de inicio de sesion a diferentes puertos y muchas conexiones fallidas
![image](https://github.com/user-attachments/assets/b68aef03-ce0d-4a98-a198-9b1e0fc8f469)

"¿La vulnerabilidad explotada tiene un CVE asignado? Y si es así, ¿cuál?" En el mismo json nuevamente buscamoS
![image](https://github.com/user-attachments/assets/e6076f4f-092e-46d0-8114-4cf65944c580)

entonces nos encontramos con cve":["CVE_2022_25237"]}},

"¿Qué cadena se añadió a la ruta URL de la API para evitar el filtro de autorización mediante el exploit del atacante?" Volvemos a revisar el trafico y filtramos por http (haciendo referencia a solicitudes web) y vemos que se hizo un cambio en la ruta

![image](https://github.com/user-attachments/assets/d7648a36-fa0f-4a96-968b-ca3a1059f735)

Con ese mismo filtro de http, vemos que hay muchas solicitudes de inicio de sesion y queremos saber luego de cuantos intentos lograron acceder
![image](https://github.com/user-attachments/assets/259efeb3-973b-4780-b4d2-6fbea61a6520)

Tenemos que cambiar el formato de la colummna para ver los nombres de usuarios, damos click derecho al nombre del usuario y le damos aplicar como colummna
![image](https://github.com/user-attachments/assets/54c375e5-3482-4f1f-94b2-36e8bd1641d3)
esto realmente fue un poco dificil para mi, tuve que voler al terminar el modulo analisis de trafico de red, recurso adicional "https://unit42.paloaltonetworks.com/unit42-customizing-wireshark-changing-column-display/"

La siguiente pregunta es "¿Qué combinación de nombre de usuario y contraseña fue exitosa?"
![image](https://github.com/user-attachments/assets/1ca492b2-3c92-49e6-9d07-341c73997026)
Como ya tenemos el filtro de usuarios se nos hace mas facil encontrar nuevas pistas

Nos preguntan " Si hay alguno, ¿qué sitio para compartir texto utilizó el atacante?" filtramos solo por http y encontramos una solictud web 
![image](https://github.com/user-attachments/assets/cf06b693-8414-494e-b375-ee397c70026b)

la siguiente pregunta se relaciona un poco con la anterior ya que accedemos a ella atraves del la flag anterior "Proporcione el nombre de archivo de la clave pública utilizada por el atacante para obtener persistencia en nuestro host."
![image](https://github.com/user-attachments/assets/49ed7809-e337-499d-ac85-d408ebb0656b)
![image](https://github.com/user-attachments/assets/4a1ce822-a6f3-4661-9342-e72cdb577b53)




