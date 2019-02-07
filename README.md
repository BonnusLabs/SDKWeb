# Bonnus SDK Web JQuery V1.6
        
    

Releases:

- V1.6 - https://bonnuslib.azureedge.net/bonnus-sdk-web-v16.js
        - Fixes generales
        - Update RSA 2048
        - Ligas de soporte
        - Fixes colores
        - Compatibilidad IE 11
        
- V1.5 - https://bonnuslib.azureedge.net/bonnus-sdk-web-v15.js
        - ID de Campaña estático
        
- V1.4 - https://bonnuslib.azureedge.net/bonnus-sdk-web-v14.js
        - Integración de datos de segmentación de usuario
        - Integración de encriptación RSA 1024
        
- V1.3 - https://bonnuslib.azureedge.net/bonnus-sdk-web-v13.js
        - Funciones Callback

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
    
- Funciones Callback

Es posible pedirle al SDK que ejecute alguna función despues de cierta acción, esta función es útil para poder llamar funciones de registro de actividad o redireccionamiento.
Para establecer la función de callback es necesario agregar tanto la función como el momento donde se llama:

        BonnusSDK.trigger('Mom2', FuncionCallback, 'momento');
        
  Los posibles momentos son:
        - beforeOpen : Momento justo antes de abrir el modal.
        - Opended : Momento justo al tarminar de abrir el modal
        - beforeClose : Momento justo antes de cerrar el modal
        - afterClose : Momento justo después de haber cerrado el modal
        - onAlert: Momento en el que se abre la alerta
        
        
- Datos de segmentación de usuarios
        Es posible que el partner envíe a Bonnus datos de segmentación de usuario, de esta forma las campañas de regreso estarán más enfocadas al usuario, los datos de segmentación son opcionales y puedesn enviarse uno o todos. mientras mas datos mejor segmentación
        
    La segmentación de usuarios deberá de realizarse antes de la inicialización del SDK de esta forma:
                BonnusSDK.setBirthDate("20/04/1980"); - Establece fecha de nacimiento, es posible aceptar solo mes y año o año.
                BonnusSDK.setZipCode("14250"); - Establece el código postal del usuario
                BonnusSDK.setGender("M"); - Establece Femenino o Masculino, solo acepta una letra M o F
                BonnusSDK.setGeo("14.00004, -95.0154"); - Estable le posición del dispositivo del usuqario en formato (Lat,Long)

        
   Los datos de segmentación de usuario son enviados a la API de Bonnus con una encriptación adicional RSA 2048


- Campaña ID.
        Si se conoce los ids de campañas que esta asociado un momento, puede especificarse directamente la campaña que se desea, esta función es optima opara sitios donde se da a escoger uno u otros Bonnus.
        Para enviar el id de campañas es necesario incluirlo en el trigger de esta forma:
        
        BonnusSDK.trigger('Momento', null, null,'CAMPAIGN_ID');
        
    Es necesario mencionar que si la campaña cambia o caduca debera de establecerse una nueva campaña o el trigger generará un error en consol.
Demo: https://bonnussdkwebdemo.azurewebsites.net/

