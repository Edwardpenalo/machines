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
