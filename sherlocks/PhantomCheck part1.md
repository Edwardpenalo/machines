Buenasss
![image](https://github.com/user-attachments/assets/47ba961c-81cd-4a3e-91ff-c3022f67c058)
Talion sospecha que el actor de amenazas realizó comprobaciones anti-virtualización para evitar ser detectado en entornos aislados. Su tarea consiste en analizar los registros de eventos e identificar las técnicas específicas utilizadas para la detección de la virtualización. Byte Doctor requiere evidencia de las comprobaciones de registro o los procesos que el atacante ejecutó para realizar estas comprobaciones.

Iniciamos esta maquina con la pregunta "¿Qué clase de WMI utilizó el atacante para recuperar información del modelo y del fabricante para la detección de virtualización?" y en estos logs encontramos que utilizo  "Win32_ComputerSystem" para consultar informacion del sistema y vemos que el atacante estaba buscando una maquina virtual ya que esto devuelve ese tipo de datos.
![image](https://github.com/user-attachments/assets/1e142d3c-b2c4-4737-8a08-686bd11e699d)

"¿Qué consulta WMI ejecutó el atacante para recuperar el valor de temperatura actual de la máquina?" este WIMI
![image](https://github.com/user-attachments/assets/f027917b-5844-4fc6-bdcf-7377baee1c7f)

La pregunta que se nos hace es "El atacante cargó un script de PowerShell para detectar la virtualización. ¿Cuál es el nombre de la función del script?" vemos que se realizo un script con un titulo muy especifico y mas adelante vemos indicadores de que es el mismo que vemos aqui
![image](https://github.com/user-attachments/assets/0ce68188-648e-44a9-b5e0-52187f68278c)

"¿Qué clave de registro consultó el script anterior para recuperar los detalles del servicio para la detección de virtualización?"Como vemos en este log tiene la ruta de la clave de registros y al final los servicios con esto identificamos que el atacante esta obteniendo informacion sobre los servicios de virtualizacion 
![image](https://github.com/user-attachments/assets/deace6f2-c2f1-4e4e-b362-36a49434ae41)

"El script de detección de máquinas virtuales también puede identificar VirtualBox. ¿Qué procesos compara para determinar si el sistema ejecuta VirtualBox?"Luego de leer detenidamente el escript vemos que se realiza una condicion $vb = Get-Process
    if (($vb -eq "vboxservice.exe") -or ($vb -match "vboxtray.exe")) mediante esto podemos determinar la forma que se identifica si es una maquina virtual box
![image](https://github.com/user-attachments/assets/364b3a1c-1430-4896-aaf7-1f7e93cab60e)

"El script de detección de máquinas virtuales imprime cualquier detección con el prefijo "Esto es una". ¿Qué dos plataformas de virtualización detectó el script?" las plataformas que mas se repiten en los Logs son Hyper_v y Vmware
![image](https://github.com/user-attachments/assets/075476db-1b73-4626-890f-9d58217a03fa)

Recomendaciones

Desactivar la ejecucion de powershell y scripts en los usuarios de la organizacion

Establcer politicas de grupo y restrincion de permisos para proteger nuestras claves de registro 

Restringir la ejecucion de escripts ya que puede ejecutarlo en otro programa de consola
