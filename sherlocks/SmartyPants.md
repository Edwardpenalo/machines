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

