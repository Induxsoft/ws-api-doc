# Timbrado de CFDI 4.0 #

El servicio de timbrado requiere autenticación a través de una Cuenta de Timbrado Induxsoft (CTI) estándar.

Consideraciones:
* Las CTI estándar no tienen caducidad (vigencia), pero están limitadas por su saldo de timbres pre-pagados

End point: https://factudesk.api.induxsoft.net/cfdi/timbrado/4.0/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "cti":"Id de Cuenta de Timbrado Induxsoft (CTI)",
  "pwd":"Contraseña de la CTI",
  "xml":"Xml del CFDI a timbrar",
  "idd":"identificador conocido previo al timbrado (opcional)",
  "nb64":true/false (opcional)
}
```
* cti - El Id de una Cuenta de Timbrado Induxsoft (CTI) Estándar
* pwd - La contraseña de la CTI
* xml - Es una cadena que contiene la representación codificada en base 64 del byte array del Xml UTF-8 de un CFDI, a menos que nb64=true
* nb64 - Es un parámetro opcional booleano que si se establece en ```true``` indica que el Xml del CFDI está codificado como una cadena JSON y la respuesta (el CFDI timbrado) también deberá devolverse en esa forma.

Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":
  {
    "uuid":"UUID del Timbre Fiscal Digital (TFD)",
    "xml":"Base 64 del byte array del Xml UTF-8 del CFDI incluyendo el complemento del TFD",
    "idd":"Identificador previo al timbrado (si se proporcionó en la solicitud) o en caso contrario el UUID"
  }
}
```

* Si en la solicitud se estableció ```nb64=true```, el campo ```xml``` será una cadena JSON del Xml del CFDI, en caso contrario será la representación en base 64 del byte array del Xml UTF-8 (incluyendo el BOM).
* Si no se indicó un ```idd``` (Identificador previo al timbrado) en la solicitud, este campo contendrá también el UUID del CFDI timbrado.

¿Por qué podría necesitar un Identificador previo al timbrado (idd)?

El idd es opcional, pero en algunos escenarios de programación puede resultar útil contar con un Identificador conocido antes de mandar a timbrar que serviría para recuperar el CFDI de la plataforma de Induxsoft incluso si perdió la conexión justo antes de recibir la respuesta del servicio Web pero despues de haber hecho el envío de la solicitud.
