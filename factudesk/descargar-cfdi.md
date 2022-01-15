# Descargar CFDI #

Obtiene el Xml,el Xml y la representación impresa o únicamente la representación impresa de un CFDI disponible en la plataforma de Induxsoft.

Este servicio requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario/contraseña) o un Id de sesión válido.

End point: https://factudesk.api.induxsoft.net/cfdi/descargar.dkl

Solicitud POST con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "uuid":"UUID del CFDI o Idd",
  "res":"(Opcional) tipo de resultado deseado",
  "pln":"(Opcional) Identificador de plantilla de representación impresa"
}
```
Solicitud POST con Id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válido",
  "doc":"UUID del CFDI o Idd",
  "res":"(Opcional) tipo de resultado deseado",
  "pln":"(Opcional) Identificador de plantilla de representación impresa"
}
```
Solicitud GET con Id de sesión
```
?uid=id-de-usuario&pwd=contraseña&uuid=uuid-o-idd&res=opc&pln=id-plantilla
```
Solicitud GET con usuario y contraseña
```
?uid=id-de-usuario&pwd=contraseña&uuid=uuid-o-idd&res=opc&pln=id-plantilla
```
Opciones para el parámetro res:
* xmlraw - la respuesta será el byte array del Xml UTF-8 con BOM del CFDI con el encabezado HTTP ```Content-type: application/octet-stream```
* prnraw - la respuesta será el byte array de la representación impresa (PDF) del CFDI con el encabezado HTTP ```Content-type: application/pdf```
* zipraw - la respuesta será el byte array del archivo zip que contiene el Xml y la representación impresa con el encabezado HTTP ```Content-type: application/octet-stream```
* xmljsn - la respuesta será un objeto JSON con el Xml del CFDI como cadena JSON
* xmlb64 - (Valor predeterminado cuando no se indique el parámetro) la respuesta será un objeto JSON con el Xml del CFDI codificado como base 64 (Xml UTF-8 con BOM)
* prnb64 - la respuesta será un objeto JSON con el byte array de la representación impresa en base 64
* zipjsn - la respuesta será un objeto JSON con el byte array de un archivo zip con el Xml y la representación impresa en base64

Parámetro pln
Es una cadena que identifica una plantilla de generación de representación impresa previamente alojada y disponible en la plataforma, si se omite se aplicarán las reglas configuradas en el emisor de FactuDesk Web.

### Respuesta exitosa ###
La respuesta de éxito dependerá del parámetro res de la solicitud.

Para la opción jsn será en la forma:

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": "Cadena con el Xml del CFDI (sintaxis válida de JSON)"
}
```
Para la opción jb64 será en la forma:

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

