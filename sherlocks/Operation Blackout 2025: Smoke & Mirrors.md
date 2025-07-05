Buenass
![image](https://github.com/user-attachments/assets/f00637c7-7e85-4333-aa08-a472a831faab)
Byte Doctor Reyes investiga un ataque sigiloso posterior a una brecha de seguridad en el que parecen faltar varios registros de seguridad y alertas de Windows Defender. Sospecha que el atacante empleó técnicas de evasión de defensas para desactivar o manipular los controles de seguridad, lo que dificulta considerablemente la detección. Utilizando los registros de eventos exportados, su objetivo es descubrir cómo el atacante comprometió las defensas del sistema para pasar desapercibido.

iniciamos con la pregunta "El atacante desactivó la protección LSA en el host comprometido modificando una clave de registro. ¿Cuál es la ruta completa de esa clave de registro?" Utilizando el buscador tomamos el indicio LSA ( Local Security Authority) para buscar este indicador de compromiso
![image](https://github.com/user-attachments/assets/ab274f6d-0e62-450b-a668-5389fb898dbe)

Utilizando la opcion de buscar "¿Qué comando de PowerShell ejecutó primero el atacante para deshabilitar Windows Defender?" encontramos el comando que desactiva la protección que analizar archivos descargados o provenientes de internet. 
![image](https://github.com/user-attachments/assets/510a681a-d579-44dd-94a3-6a5a0f96b0f9)

"El atacante cargó un parche AMSI escrito en PowerShell. ¿Qué función de la DLL está siendo parcheada por el script para deshabilitar AMSI eficazmente?" estamos buscando parches a dll y encontramos un script el cual es el siguiente
![image](https://github.com/user-attachments/assets/97f03519-950f-460a-aa26-684212f46018)

"¿Qué comando utilizó el atacante para reiniciar la máquina en modo seguro?" Utilizamos la busqueda nuevamente y filtramos por safeboot (que se refiere a inicio seguro) aqui encontraremos el comando utilizado

![image](https://github.com/user-attachments/assets/59531c3c-a27c-4460-83cf-d8d22d627d0c)

"¿Qué comando de PowerShell utilizó el atacante para deshabilitar el registro del historial de comandos de PowerShell?" Utilizamos para buscar contenido relacionado con el indicador History

![image](https://github.com/user-attachments/assets/501b2c16-68ec-49fc-a29a-a70853c18ab9)

logramos hacer el sherlock¡
![image](https://github.com/user-attachments/assets/6eccf3d9-a6ec-4f85-99f9-bdf0384755a3)

RECOMENDACIONES 
Habilitar protecciones reforzadas en endpoints
Implementacion de politicas para prohibir la ejecucion de las shells
Protección del historial y cuidado de logs ( para evitar que se pierda informacion como cuando o que se hizo en el sistema)
Verificar cambios sospechosos en la configuración de Defender
