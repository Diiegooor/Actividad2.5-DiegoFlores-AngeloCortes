# Security Tips

# Estos tips refuerzan la seguridad de la aplicación de protegiéndola contra accesos no autorizados,
manipulación de datos y ataques en la red, creando una experiencia más segura y confiable para los usuarios.

## Integrar Medidas Específicas basadas en los Security Tips
- Minimizar los permisos: al reducir los permisos, limitaremos el ecceso de la aplicación
  solo a los recursos estrictamente necesarios, esto reduce la superficie de ataque y protege contra posibles vulnerabilidades.
- Deshabilitar allowBackup: Configurar android:allowBackup="false" previene que la app sea respaldada a través de herramientas
  de desarrollo. Esto reduce el riesgo de que un atacante copie datos locales de la aplicación si tiene acceso físico al
  dispositivo, protegiendo información sensible.
- Certificado de Producción: Usar un certificado de producción, en lugar de uno de depuración, asegura que el APK es menos
  susceptible a la modificación por terceros y protege contra la distribución de versiones comprometidas de la aplicación.

## Proteger la Aplicación contra Ataques de Inyección SQL
- Consultas SQL Preparadas: Usar consultas preparadas evita que los datos de entrada se interpreten como
  parte de la lógica SQL, protegiendo contra ataques de inyección SQL.
- ORMs y Abstracción de Bases de Datos: Usar un ORM (como Room) proporciona una capa de seguridad porque gestiona
  las consultas SQL internamente, minimizando el riesgo de errores en la manipulación directa de SQL y previniendo posibles inyecciones.
- Sanitización de Entradas: Validar y sanitizar las entradas asegura que solo datos esperados ingresen a la
  base de datos. Esto es especialmente importante en campos como nombres de usuario o contraseñas, evitando que
  caracteres especiales o scripts maliciosos accedan o alteren la información.

## Implementar Autenticación y Autorización Seguras
- Autenticación Multifactor (MFA): Agregar MFA agrega una capa adicional de verificación, asegurando que el usuario
  realmente es quien dice ser. Esto dificulta el acceso a personas no autorizadas, incluso si obtuvieran las credenciales del usuario.
- OAuth o Tokens JWT: Los tokens JWT y OAuth permiten una autenticación basada en tokens seguros, lo cual es ideal para gestionar
  sesiones de usuarios y proteger el acceso a recursos. Al incluir datos encriptados y firmados, previenen la manipulación de sesiones
y aseguran que cada solicitud provenga de un usuario autenticado.
- Almacenamiento Seguro de Credenciales: Al usar el Android Keystore o EncryptedSharedPreferences, proteges las credenciales y tokens
  en el almacenamiento local de la aplicación. Esto dificulta que un atacante, incluso con acceso al dispositivo, obtenga claves o contraseñas directamente.

## Proteger la Aplicación contra Ataques de Red (e.g., MITM)
- HTTPS y SSL Pinning: HTTPS encripta las comunicaciones de red, asegurando que los datos transmitidos entre la app y el servidor 
  estén protegidos contra espionaje y manipulación.
- Verificación de Certificados: Validar correctamente los certificados ayuda a prevenir ataques de suplantación, en los que un
  atacante intenta interceptar o manipular los datos al usar un certificado falso.
- Network Security Config: La configuración de seguridad de red en Android permite imponer el uso de HTTPS y definir los hosts
  confiables, lo cual asegura que todas las conexiones de red sean seguras y ayuda a prevenir errores de configuración en producción.
