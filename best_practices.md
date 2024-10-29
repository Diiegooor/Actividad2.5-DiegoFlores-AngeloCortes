# Buenas Practicas 

Estas son las buenas Practicas a seguir para fortalecer la seguridad de la aplicación y proteger 
la infraestructura del codigo y la información que pueda ser privados.

## Asegurar codigo e infraestructura 
- Deshabilitar Opciones de Depuración: Asegúrate de que android:debuggable esté configurado como false en el archivo AndroidManifest.xml para evitar que la app sea susceptible a depuraciones externas.
- Evitar permisos innecesarios: Utilizar solo los permisos estrictamente necesarios, especialmente los de alta sensibilidad como los de ubicación.
- Control de versiones: Utilizar un sistema de control de versiones seguro como git y definir ramas separadas para desarrollo, prueba y producción para evitar errores en el despliegue.

## Implementar cifrado para datos sensibles 
- Implementa EncryptedSharedPreferences para almacenar datos sensibles en el dispositivo de manera segura.
- verificar el certificado SSL/TLS en la aplicación para evitar ataques de intermediario (MITM).

## Asegurar la comunicación de red utilizando HTTPS
- Configurar HTTPS y usar SSL pinning para asegurar que la app solo se comunique con servidores de confianza, previniendo ataques MITM.
- Desactivar protocolos y cifrados inseguros (por ejemplo, SSLv3, TLS 1.0) para evitar que los datos sean interceptados.

## Validar y sanitizar todas las entradas del usuario
- Implementar validación en cada campo de entrada en el cliente y el servidor.
- Sanitizar y escapar todas las entradas antes de usarlas en consultas SQL, HTML o almacenamiento para evitar inyecciones de código.
- No muestrar detalles técnicos de errores al usuario final. En lugar de esto, usar mensajes de error generales que no revelen el funcionamiento interno de la aplicación.

- 
