Buenasss
![image](https://github.com/user-attachments/assets/278b7e42-fded-4759-8206-7f9671247b28)
El dispositivo IDS nos alertó sobre un posible dispositivo no autorizado en la red interna de Active Directory. El Sistema de Detección de Intrusiones (IDS) también indicó indicios de tráfico LLMNR, lo cual es inusual. Se sospecha que se produjo un ataque de envenenamiento de LLMNR. El tráfico LLMNR se dirigió a Forela-WKstn002, cuya dirección IP es 172.17.79.136. Nuestro experto en análisis forense de redes le proporciona una captura de paquetes limitada del tiempo circundante. Dado que esto ocurrió en la VLAN de Active Directory, le sugerimos que realicemos una búsqueda de amenazas de red teniendo en cuenta el vector de ataque de Active Directory, centrándonos específicamente en el envenenamiento de LLMNR.

Este sherlock es AD estoy estudiando sobre el tema, en algunos foros lo recomiendan si quieres hacer la CDSA

![image](https://github.com/user-attachments/assets/a2f59275-62fd-4f58-a69a-6aba59589969)
Lo primero que hago es buscar en internet en que puerto corre este servicio para asi filtrar en nuestro trafico

![image](https://github.com/user-attachments/assets/b089034f-4c5e-4c80-9c42-ff7002096ab6)

La siguiente pregunta es "¿Cuál es el nombre de host de la máquina maliciosa?"
![image](https://github.com/user-attachments/assets/8f781569-2ba9-464f-80fd-f8f04bed4e66)
con el siguiente filtro encontramos la respuesta

Nos preguntan "En el tráfico NTLM, podemos ver que las credenciales de la víctima se retransmitieron varias veces a la máquina del atacante. ¿Cuándo se capturaron los hashes por primera vez?" filtramos por smb protocolo para compartir recursos
![image](https://github.com/user-attachments/assets/3ffdde90-8c3e-4e23-b96c-dc6fcb33219f)

"En el tráfico NTLM, podemos ver que las credenciales de la víctima se retransmitieron varias veces a la máquina del atacante. ¿Cuándo se capturaron los hashes por primera vez?"
![image](https://github.com/user-attachments/assets/217c1ee9-b3e3-4acb-af21-ff3a6a0a0f65)

El error tipografico que cometio el usuario DCC01 y lo correcto o como deberia ser es DC01
![image](https://github.com/user-attachments/assets/770904bd-6315-4f76-806b-81cc079e63b4)

"Para obtener las credenciales reales del usuario víctima, necesitamos combinar varios valores de los paquetes de negociación NTLM. ¿Cuál es el valor de desafío del servidor NTLM?"
![image](https://github.com/user-attachments/assets/0d41dfe3-90b7-4033-808d-e3f480e35d52)

Esto lo encontre con el filtro smb y rebusque en la informacion de SMB fui probando respuestas

"Ahora, haciendo algo similar, busque el valor de NTProofStr." fue casi lo mismo y busque exactamente el nombre en los paquetes
![image](https://github.com/user-attachments/assets/70c466b8-de85-4b9b-bc4e-2d47560dc4d7)

"Para comprobar la complejidad de la contraseña, intente recuperarla a partir de la información obtenida en la captura de paquetes. Este paso es crucial, ya que nos permite determinar si el atacante logró descifrarla y con qué rapidez."

![image](https://github.com/user-attachments/assets/9570edfd-6993-453b-9209-7efaf93b6660)
Aqui busque empece a relaizar lo que indica la pista "Cree un nuevo archivo e introduzca los valores de la siguiente manera: Usuario::Dominio:ServerChallenge:NTProofStr:NTLMv2Response (sin los primeros 16 bytes). El valor de la respuesta NTLMv2 se puede obtener de donde obtuvimos NTProofStr. Elimine los primeros 16 bytes (32 caracteres) del valor. Luego, descifre el hash con hashcat. La sintaxis de Hashcat es la siguiente: Hashcat -a0 -m5600 hashfile.txt rockyouwordlist.txt"

