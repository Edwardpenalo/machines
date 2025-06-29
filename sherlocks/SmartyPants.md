Buenassss
![image](https://github.com/user-attachments/assets/36d7a511-c6c3-460b-a089-f94eaf960e78)

El director de tecnología de Forela, Dutch, almacena archivos importantes en un sistema Windows independiente, ya que el entorno de dominio de Forela sufre frecuentes vulneraciones debido a su exposición en diversas industrias. El 24 de enero de 2025, nuestros peores temores se hicieron realidad cuando un intruso accedió al servidor de archivos, instaló utilidades para facilitar sus acciones, robó archivos críticos y los borró, dejándolos irrecuperables. El equipo fue informado de inmediato del intento de extorsión por parte de los intrusos, quienes ahora exigen dinero. Mientras nuestro equipo legal aborda la situación, debemos realizar un triaje rápido para evaluar el alcance del incidente. Nota del gerente: Hace unos días, habilitamos los registros de depuración de SmartScreen en todas nuestras máquinas para mejorar la visibilidad, siguiendo una recomendación de un estudio de seguridad. Estos registros pueden proporcionar información rápida, así que asegúrese de utilizarlos.

Empezamos esta maquina con la siguiente instruccion "El atacante inició sesión en la máquina donde Dutch guarda archivos críticos, a través de RDP, el 24 de enero de 2025. Determine la marca de tiempo de este inicio de sesión."
![image](https://github.com/user-attachments/assets/a5eb2ba8-9a16-48ca-b8d8-26b0ada13056)

Recomiendo utilizar sysmon para revisar enventos, filtramos por el id de evento correspondiente a inicios de sesion por RDP y en la vista xml logramos ver la respuesta

Nos preguntan "El atacante descargó algunas utilidades que le ayudaron en su operación de sabotaje y extorsión. ¿Cuál fue la primera herramienta que descargó e instaló?" revisamos logs de smartscreen para encontrar esto
![image](https://github.com/user-attachments/assets/149657c0-6a19-4aa5-9a64-0c2ffc05ae61)

Las siguiente pregunta es "Luego, descargaron y ejecutaron la versión portátil de una herramienta que permitía buscar archivos en el equipo de forma rápida y eficiente. ¿Cuál era la ruta completa del ejecutable?"
en descargas nuevamente vemos un ejecutable que segun investigamos es Everything.exe y sirve para " aplicación de búsqueda fácil de usar que le ayuda a encontrar cualquier archivo o carpeta almacenada en su computadora de Windows"

![image](https://github.com/user-attachments/assets/9d990509-caa3-4122-85b6-d2cdf9c3f592)

En la vista XML encontraremos la hora de ejecucion de esta herramienta
![image](https://github.com/user-attachments/assets/793b740e-3a84-41ad-8d6e-c47c011d48bf)

"La utilidad se utilizó para buscar documentos críticos y confidenciales almacenados en el host, que el atacante podría robar y extorsionar a la víctima. ¿Cuál fue el primer documento que el atacante obtuvo y violó su confidencialidad?" Correlacionando eventos, utiliza herramientas para busqueda de archivos, por lo que imagino que sera un documento sensible y encuentro este envento
![image](https://github.com/user-attachments/assets/fdcbd130-dd67-4545-881a-9e917a38a8af)

"Encuentra también el nombre y la ruta del segundo documento robado." ya sabemos que el atacante estuvo en la ruta "C:\\Users\\Dutch\\Documents\\2025- Board of directors Documents\" intuimos que si esta en un directorio sensible con multiples datos seguira tomando del mismo y encontramos este
![image](https://github.com/user-attachments/assets/0bea74b7-55d9-4d43-9adc-c3db9295a349)

"El atacante también instaló una utilidad en la nube para robar y exfiltrar los documentos. ¿Cómo se llama esta utilidad?" en el momento que nos indican exfiltracion y la nube, ya tenemos como objetivo identificar tecnologias mencionada y mega es una de estas que encontramos 

![image](https://github.com/user-attachments/assets/35c58d2c-3130-48e8-a27a-c7e8c13d5024)

"¿Cuando se ejecutó esta utilidad?" en la vista XML encontramos la misma
![image](https://github.com/user-attachments/assets/3169a130-e010-4074-bf7c-847c1635c29a)

"El atacante también destruyó los datos del host, haciéndolos irrecuperables. ¿Qué herramienta se utilizó para lograrlo?" en los registros encontramos varias herramientas y nos detenmos a investigar para que sirven cada una de estas,vemos que esta sirve para " "
![image](https://github.com/user-attachments/assets/0ad9c21e-a985-41ba-a08e-12ead6ba539b)

"El atacante borró dos registros importantes, creyendo haber borrado todas sus huellas. ¿Cuándo se borró el registro de seguridad?" Nos dirigimos a los eventos de seguridad y buscamos por le id correspondiente que es el 1102, en el marco mitre es  T1070 https://attack.mitre.org/techniques/T1070/001/
![image](https://github.com/user-attachments/assets/c511ba17-2b0f-4dca-9a36-40f84d6086a0)

![image](https://github.com/user-attachments/assets/ba5d7682-af2c-43b8-ae52-6ee0963469bb)

RECOMENDACIONES 
Si es un puesto direcctivo es obvio tendra archivos sensibles recomiento introduccir claves a dichos documentos pero personalmente si no es personal de TI no tiene que tener ciertos privilegios en este ataque se hicieron de el por RDP creo que esto se podria haber evitado estableciendo una ACL nada que no este en mi rango puede conectarse, politicas de firewall para el eacceso a los sitios donde descargo herramientas, basicamente dejar los sitios visitados correctamente y limitar el trafico fuea de esos o los necesarios para laborar dia a dia, politicas de ejecucion no son programas comunes los que esta ejecutando deberia bloquearlo
