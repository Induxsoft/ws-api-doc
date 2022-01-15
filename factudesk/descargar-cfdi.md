# Descargar CFDI #

Este servicio requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario/contraseña) o un Id de sesión válido.

End point: https://factudesk.api.induxsoft.net/cfdi/descargar.dkl

Solicitud POST con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "doc":"UUID del CFDI o Idd",
  "fmt":"(Opcional) vea la lista de opciones"
}
```
Solicitud POST con Id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válido",
  "doc":"UUID del CFDI o Idd",
  "fmt":"(Opcional) vea la lista de opciones"
}
```
Solicitud GET con Id de sesión
```
?uid=id-de-usuario&pwd=contraseña&doc=uuid-o-idd&nrw=opc
```
Solicitud GET con usuario y contraseña
```
?uid=id-de-usuario&pwd=contraseña&doc=uuid-o-idd&nrw=opc
```

### Respuesta exitosa ###
La respuesta de éxito dependerá del parámetro fmt de la solicitud.

Opciones para el parámetro fmt:
* raw - la respuesta será el byte array del CFDI en UTF-8 con BOM con el encabezado HTTP ```Content-type: application/octet-stream```
* xml - la respuesta será el contenido Xml con el encabezado HTTP ```Content-type: text/xml```
* jsn - la respuesta será un objeto JSON como se indica a continuación:

        ```
        Content-Type: application/json;charset=utf-8
        {
          "success":true,
          "data": "Cadena con el Xml del CFDI (sintaxis válida de JSON)"
        }
        ```
* jb64 - (Valor predeterminado aun cuando no se indique el parámetro) la respuesta será un objeto JSON como se indica a continuación:

        ```
        Content-Type: application/json;charset=utf-8
        {
          "success":true,
          "data": "Cadena codificada en base64 del byte array del Xml UTF-8 incluyendo BOM"
        }
        ```
### Respuesta error ###
Para las opciones jsn y jb64, la respuesta de error será igualmente el objeto JSON de la forma estándar:
```
Content-Type: application/json;charset=utf-8
{
	"success":false,
	"message":"Mensaje de error"
}
```

Para las opciones raw y xml, la respuesta de error será el contenido HTML de un mensaje descriptivo para el usuario.

