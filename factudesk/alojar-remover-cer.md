# Administrar certificados #

Permite almacenar o actualizar un certificado en la plataforma o bien removerlo.

Este servicio requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario/contraseña) o un Id de sesión válido.

End point: https://factudesk.api.induxsoft.net/certificados/administrar/

## Alojar (o actualizar) certificado

Solicitud POST con usuario y contraseña para alojar un certificado
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "cer":"Base 64 del byte array del archivo .cer",
  "key":"Base 64 del byte array del archivo .key",
  "kpw":"Contraseña de la clave privada"
}
```
Solicitud POST con Id de sesión para alojar un certificado
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válido",
  "cer":"Base 64 del byte array del archivo .cer",
  "key":"Base 64 del byte array del archivo .key",
  "kpw":"Contraseña de la clave privada"
}
```

### Consideraciones
* La contraseña de la clave privada no se validará por lo que podría dar lugar a que el certificado alojado no pueda usarse
* Si la contraseña o la llave privada no son correctas, deberá volver a invocar el servicio

### Posibles errores
* Error de autenticación de usuario o validez de id de sesión

### Respuesta exitosa ###

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": 
  {
  	"ncer":"Número del certificado alojado"
  }
}
```

## Eliminar un certificado
Solicitud POST con usuario y contraseña para eliminar un certificado
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válido",
  "rfc":"RFC del emisor (propietario del certificado)",
  "ncer":"Número del certificado a eliminar"
}
```

Solicitud POST con Id de sesión para eliminar un certificado
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válido",
  "opt":"ELIMINAR",
  "rfc":"RFC del emisor (propietario del certificado)",
  "ncer":"Número del certificado a eliminar"
}
```

### Posibles errores
* El número de certificado no corresponde a un certificado en la plataforma
* El certificado no pertenece al rfc indicado
* Error de autenticación de usuario o validez de id de sesión

### Respuesta exitosa ###

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": null
}
```



