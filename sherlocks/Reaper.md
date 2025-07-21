Buenasss
<img width="1601" height="381" alt="image" src="https://github.com/user-attachments/assets/e9032648-58b8-4739-924a-e79e019881f8" />

Nuestro SIEM nos alertó sobre un inicio de sesión sospechoso que requiere revisión inmediata. La alerta indicaba que la dirección IP y el nombre de la estación de trabajo de origen no coincidían. Se le proporcionó una captura de red y registros de eventos del período cercano al incidente. Corresponda la evidencia obtenida e informe a su responsable del SOC.

"¿Cuál es la dirección IP de Forela-Wkstn001?" Inciamos con esta pregunta podemos encontrar esta ip ya que en la info  con el protocolo LLMNR (Link-Local Multicast Name Resolution)logramos encontrar el usuario que estamos buscando
<img width="1785" height="711" alt="image" src="https://github.com/user-attachments/assets/70cedc5e-9f60-42d5-b251-c78c948af1df" />


"¿Cuál es la dirección IP de Forela-Wkstn002?" filtramos por busqueda de dominios y encontramos una solicitud a dicha ip 

<img width="1684" height="343" alt="image" src="https://github.com/user-attachments/assets/10587faa-c899-4824-bc88-35f878422b2a" />

"¿Cuál es el nombre de usuario de la cuenta cuyo hash fue robado por el atacante?" "¿Cuál es la dirección IP del dispositivo desconocido utilizado por el atacante para interceptar las credenciales?"  Son preguntas diferentes pero correlacionamos y nos damos cuenta que tenemos ambas en este log, el usuario,ip , puerto, id de sesion, archivo compartido, hora del inicio malicioso y estacion de trabajo.

<img width="1546" height="987" alt="image" src="https://github.com/user-attachments/assets/20d53a99-02d6-46a9-b88d-c7447abcaad2" />

<img width="1348" height="968" alt="image" src="https://github.com/user-attachments/assets/79dadd73-1cc1-49cf-abde-89785e44373f" />
<img width="1158" height="748" alt="image" src="https://github.com/user-attachments/assets/8200838d-8a5b-44a3-bae2-b4dcd1b9aad8" />

"¿Cuál es el nombre compartido al que accede como parte del proceso de autenticación la herramienta maliciosa utilizada por el atacante?" Filtramos id de evento por archivo compartido 

<img width="1236" height="479" alt="image" src="https://github.com/user-attachments/assets/771839c0-cadd-46fa-a631-cb59b8d1456b" />

Con esto logramos  completar la maquina 
<img width="877" height="760" alt="image" src="https://github.com/user-attachments/assets/e2860cc0-aab2-4ca5-9ff4-d6aa1309813e" />

RECOMENDACIONES 

Establecer lista de control de acceso

Bloquear accesos a recursos y establecer usuarios quienes pueden y quines no acceder y compartir dichos archivos

Bloquear puertos inutilizados

Capacitación del personal





