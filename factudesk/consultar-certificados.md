# Consultar certificados #

Devuelve un array de objetos que contienen información de los certificados alojados en la plataforma.

Este servicio requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario/contraseña) o un Id de sesión válido.

End point: https://factudesk.api.induxsoft.net/consultas/certificados/

Solicitud POST con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "rfc":"RFC del propietario del certificado"
}
```
Solicitud POST con Id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válido",
  "rfc":"RFC del propietario del certificado"
}
```

### Respuesta exitosa ###

Para las opciones de resultado xmljsn y xmlb64:
```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": 
  [
  	{
    "numero":"Número del certificado", 
    "vigencia_hasta":"fecha y hora de expiración en formato yyyy-mm-ddThh:mm:ss", 
    "vigencia_desde":"fecha y hora de inicio de vigencia en formato yyyy-mm-ddThh:mm:ss",
    "emisor":"Nombre del sujeto (emisor) según el certificado"
    "vigente":true/false (indica si el certificado está vigente al momento de la consulta)
    },
    {...},...
  ]
}
```
