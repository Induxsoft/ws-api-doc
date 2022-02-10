# Descargar CFDI o CR #

Obtiene el Xml,el Xml y la representación impresa o únicamente la representación impresa de un CFDI o CR disponible en la plataforma de Induxsoft.

Este servicio requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario/contraseña) o un Id de sesión válido.

End point: https://factudesk.api.induxsoft.net/comprobantes/descargar/

Solicitud POST con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "doc":"UUID del CFDI o Idd",
  "tpo":"cfdi/cr (opcional)",
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
  "tpo":"cfdi/cr (opcional)",
  "res":"(Opcional) tipo de resultado deseado",
  "pln":"(Opcional) Identificador de plantilla de representación impresa"
}
```
Solicitud GET con Id de sesión
```
https://factudesk.api.induxsoft.net/comprobantes/descargar/?uid=id-de-usuario&pwd=contraseña&uuid=uuid-o-idd&tpo=cfdi/cr&res=opc&pln=id-plantilla
```
Solicitud GET con usuario y contraseña
```
https://factudesk.api.induxsoft.net/comprobantes/descargar/?uid=id-de-usuario&pwd=contraseña&uuid=uuid-o-idd&tpo=cfdi/cr&res=opc&pln=id-plantilla
```
El parámetro ```doc``` será el UUID de un CFDI o una constancia de retención, si se requiere más de 1, deberán delimitarse por comas. Tratándose de descarga de más de un comprobante, únicamente se admitirán en ```res``` los valores: ziplnk y zipraw, siendo predeterminado ziplnk. El máximo de comprobantes a devolver será de 50.

El parámetro ```tpo``` indica el tipo de documento solicitado: cfdi-CFDI o cr-Constancia de retención, si se omite, se asume el valor cfdi como predeterminado.

Opciones para el parámetro res:
* xmllnk - Se obtendrá un enlace temporal al documento Xml del CFDI
* prnlnk - Se obtendrá un enlace temporal al documento (pdf) de la representación impresa
* ziplnk - Se obtendrá un enlace a un archivo zip que contiene tanto el xml como su representación impresa
* xmljsn - la respuesta será un objeto JSON con el Xml del CFDI como cadena JSON
* xmlb64 - (Valor predeterminado) la respuesta será un objeto JSON con el Xml del CFDI codificado como base 64 (Xml UTF-8 con BOM)
* xmltxt - El Xml del CFDI con encabezado HTTP ```Content-type: text/xml```
* xmlraw - El Xml del CFDI con encabezado HTTP ```Content-type: application/octet-stream```
* prnraw - El contenido de la representación impresa con encabezado HTTP ```Content-type: application/octet-stream```
* prnpdf - El contenido de la representación impresa con encabezado HTTP ```Content-type: application/pdf```
* zipraw - El contenido de un archivo Zip con el Xml del CFDI y su representación impresa con encabezado HTTP ```Content-type: application/octet-stream```

Parámetro pln
Es una cadena que identifica una plantilla de generación de representación impresa previamente alojada y disponible en la plataforma, si se omite se aplicarán las reglas configuradas en el emisor de FactuDesk Web.

### Respuesta exitosa ###

Para las opciones de resultado xmljsn y xmlb64:
```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": 
  {
  	"content":"El Xml del CFDI como una cadena o un byte array base 64"
  }
}
```

Para las opciones de resultado xmllnk, prnlnk y ziplnk:
```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": 
  {
  	"link":"Enlace temporal al archivo a descargar"
  }
}
```

Para las opciones de resultado xmltxt, xmlraw, prnraw, prnpdf y zipraw:
Se inicia la descarga del contenido directamente (generalmente el navegador descargará o abrirá el archivo).

### Respuesta error ###
Para las opciones xmljsn, xmlb64, xmllnk, prnlnk y ziplnk la respuesta de error será igualmente un objeto JSON de la forma estándar:
```
Content-Type: application/json;charset=utf-8
{
	"success":false,
	"message":"Mensaje de error"
}
```
Para las opciones xmltxt, xmlraw, prnraw, prnpdf y zipraw en caso de error se devolverá una página Html con el mensaje correspondiente al usuario.

