# Bonnus SDK Web JQuery V1.2
        
    

Releases:
- Beta - V1.2 - https://bonnuslib.azureedge.net/bonnus-sdk-web-v12.js
        - Soporte Multi Modal.
        - Bonnus reusables / no reusables
        - Notificación on / off
        - Funcion para verificar el estado del momento.

- 16 nov 2018 - V1.1 - https://bonnuslib.azureedge.net/bonnus-sdk-web-v10.js


Configuración del SDK de Bonnus para Web Basado en Jquery.

- Requisitos:
  Requiere  jQuery v1.7 o superior


- Incluir librerias SDK al sitio web:

Para agregar el SDK, lo incluimos en el header de la siguiente manera:

    <link rel="stylesheet" href="https://bonnuslib.azureedge.net/bonnus-sdk-web.css" />
    <script src="https://bonnuslib.azureedge.net/bonnus-sdk-web-v10.js"></script>


- Credenciales para inicio de sesión en la API de Bonnus:

Para usar el SDK, tenemos que inicializar cada página web y generar una instancia Bonnus_SDK:

     <script type="text/javascript">
        var bns = BonnusSDK.init(["SDKID", "PARTNERID", "TOKEN"]);
     </script>
     
Es posible inicializar el SDK con un identificador únido de usuario, de manera contraria el sdk generar un identificador aleatorio y lo guardará en cookie.

     <script type="text/javascript">
        var bns = BonnusSDK.init(["SDKID", "PARTNERID", "TOKEN", "USERID"]);
     </script>

- Configuración del SDK.
La configuración del SDK vive dentro de la plataforma de Bonnus, al activar el SDK se guardaran los datos de configuración en el dispositivo. La configuración del SDK sólo puede ser modificada por Bonnus.

Limite de usuarios (opcional): Se puede establecer un límite de usuarios, al alcanzar este límite el SDK no activará la funcionalidad a otros usuarios.

Color Fondo: Establece el color a utilizar para el fondo de los Bonnus.
Color notificación: Establece el color de la notificación in-App cuando el usuario ha obtenido un Bonnus.
Color Botón: Establece el color de los botones.
Color Texto: Establece el color de los textos principales (Títulos)

Mensaje Aceptar: Establece el texto del botón para aceptar el Bonnus (Predeterminado: "Aceptar").
Mensaje Cerrar: Establece el texto del botón para cerrar el Pop-up del Bonnus (Predeterminado: "Guardar").

Estilo: Estable la plantilla a utilizar: Actualmente se cuentan con dos plantillas diferentes.
Mensaje de Soporte: Es posible establecer un mensaje personalizado para Dudas / Contacto / Soporte.

Momentos: Para configurar los momentos es necesario la siguiente información:
Trigger: Establece el texto o textos para establecer en la acción: (ej. "Momento1", "Mom1")
Logica de activación: Establece cuándo se va a dar un Bonnus, y consta de dos elementos, Logica (Igual, Mayor o Menor), Numero (1, 2, 100, 50.60).
Reusable: Establece si el usuario puede ganar un Bonnus cada vez que se cumpla la condición o sólo una vez.
Notificación: Establece si el bonnus mostrará una notificación in-App o directamente un Pop-up.


- Registro de Actividad / Momento

En la actividad en la que queramos mandar acciones y mostrar popups tenemos que hacer lo siguiente:


        BonnusSDK.trigger('TRIGGER');
        
El evento puede llamarse desde un href: <a href="javascript:BonnusSDK.trigger('Mom4');">Prueba Momento 2</a>
o desde un evento de JS.

- Verificar estado de momento.
Es posible consultar el SDK para saber si un momento ya fue ejectudo o no.

        BonnusSDK.isUsed('trigger'); : Boolean

El resultado es un boolean.
    


Demo: https://bonnussdkwebdemo.azurewebsites.net/

