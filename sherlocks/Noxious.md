Buenasss
![image](https://github.com/user-attachments/assets/278b7e42-fded-4759-8206-7f9671247b28)
El dispositivo IDS nos alertó sobre un posible dispositivo no autorizado en la red interna de Active Directory. El Sistema de Detección de Intrusiones (IDS) también indicó indicios de tráfico LLMNR, lo cual es inusual. Se sospecha que se produjo un ataque de envenenamiento de LLMNR. El tráfico LLMNR se dirigió a Forela-WKstn002, cuya dirección IP es 172.17.79.136. Nuestro experto en análisis forense de redes le proporciona una captura de paquetes limitada del tiempo circundante. Dado que esto ocurrió en la VLAN de Active Directory, le sugerimos que realicemos una búsqueda de amenazas de red teniendo en cuenta el vector de ataque de Active Directory, centrándonos específicamente en el envenenamiento de LLMNR.

Este sherlock es AD estoy estudiando sobre el tema, en algunos foros lo recomiendan si quieres hacer la CDSA

![image](https://github.com/user-attachments/assets/a2f59275-62fd-4f58-a69a-6aba59589969)
Lo primero que hago es buscar en internet en que puerto corre este servicio para asi filtrar en nuestro trafico

![image](https://github.com/user-attachments/assets/b089034f-4c5e-4c80-9c42-ff7002096ab6)
