# Rporte de Vulnerabilidades

## Debug Enabled For App [android:debuggable=true]
- Descripción: La depuración se habilitó en la aplicación, lo que facilita a los ingenieros inversos conectarle un depurador. Esto permite volcar un seguimiento de la pila y acceder a clases auxiliares de depuración.
- Severidad: Alta
- impacto: Al habilitar android:debuggable=true, cualquier persona con acceso físico al dispositivo o con herramientas de depuración puede usar Android Debug Bridge (ADB) para interactuar con la aplicación y explorar su entorno de ejecución.
- Remediación: Asegurarse de que en el archivo AndroidManifest.xml esté establecido android:debuggable=false. Esto asegura que la app no sea depurable en el entorno de producción.

## Application Data can be Backed up [android:allowBackup=true]
- Descripción: Esta bandera permite a cualquiera hacer una copia de seguridad de los datos de su aplicación a través de adb. Permite a los usuarios que han habilitado la depuración USB copiar datos de la aplicación fuera del dispositivo.
- Severidad: Advertencia
- Impacto:Habilitar android:allowBackup=true permite que los datos de la aplicación se respalden automáticamente en la cuenta de Google del usuario. Esto incluye datos locales y configuraciones de la app, que pueden incluir información sensible.
  Un atacante con acceso al archivo de respaldo podría analizar estos datos, exponiendo credenciales, preferencias o información privada.
- Remediación: -Deshabilita el respaldo estableciendo android:allowBackup=false en el archivo AndroidManifest.xml.
               -Controla el contenido del respaldo si necesitas respaldo de algunos datos. Usa la propiedad android:fullBackupContent para especificar un archivo full-backup-content.xml, limitando qué datos se respaldan y excluyendo los sensibles.

## Broadcast Receiver (androidx.profileinstaller.ProfileInstallReceiver) está protegido por un permiso, pero se debe verificar el nivel de protección del permiso. Permiso: android.permission.DUMP [android: exportado = verdadero]
- Descripción: Se descubre que un receptor de transmisión se comparte con otras aplicaciones en el dispositivo, por lo que es accesible para cualquier otra aplicación en el dispositivo. Está protegido por un permiso que no está definido en la aplicación analizada.
  Como resultado, se debe verificar el nivel de protección del permiso donde está definido. Si se configura como normal o peligroso, una aplicación maliciosa puede solicitar y obtener el permiso e interactuar con el componente. Si está configurado en firma, sólo
  las aplicaciones firmadas con el mismo certificado pueden obtener el permiso.
- Severidad: Advertencia 
- impacto: Habilitar android:debuggable=true permite que la aplicación sea accesible para herramientas de depuración como ADB, lo que facilita a ingenieros inversos o atacantes conectarse a la app y analizar su comportamiento en tiempo real. Esto incluye la posibilidad
  de realizar un volcado de seguimiento de la pila, explorar variables internas y examinar clases de depuración. Los atacantes pueden usar esta vulnerabilidad para identificar y explotar fallos en el código, acceder a datos sensibles, o inyectar código malicioso.
- Remediación: Deshabilitar el Modo de Depuración en Producción: Asegúrate de que android:debuggable=false esté configurado en el archivo AndroidManifest.xml en la versión de producción de la aplicación. Esto evita que la aplicación sea depurable una vez distribuida.





