# Sellar y timbrar CFDI 4.0 y CR 2.0 #

El servicio de sellado y timbrado requiere autenticación a través de una Cuenta de Timbrado Induxsoft (CTI) estándar.

Consideraciones:
* Las CTI estándar no tienen caducidad (vigencia), pero están limitadas por su saldo de timbres pre-pagados
* Debe haber por lo menos un certificado alojado en la plataforma asociado al emisor

End point: https://factudesk.api.induxsoft.net/comprobantes/sellar-timbrar/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "cti":"Id de Cuenta de Timbrado Induxsoft (CTI)",
  "pwd":"Contraseña de la CTI",
  "xml":"Xml del CFDI o CR a timbrar",
  "idd":"identificador conocido previo al timbrado (opcional)",
  "nb64":true/false (opcional),
  "ncer":"Número de certificado a utilizar (opcional)"
}
```
* cti - El Id de una Cuenta de Timbrado Induxsoft (CTI) Estándar
* pwd - La contraseña de la CTI
* xml - Es una cadena que contiene la representación codificada en base 64 del byte array del Xml UTF-8 de un CFDI o CR, a menos que nb64=true
* nb64 - Es un parámetro opcional booleano que si se establece en ```true``` indica que el Xml del CFDI o CR está codificado como una cadena JSON y la respuesta (el CFDI timbrado) también deberá devolverse en esa forma.
* ncer - Es el número de un certificado previamente alojado en la plataforma de Induxsoft, si se omite se intentará sellar con el primer certificado vigente que se haya configurado para el emisor

Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":
  {
    "uuid":"UUID del Timbre Fiscal Digital (TFD)",
    "xml":"Base 64 del byte array del Xml UTF-8 del CFDI o CR incluyendo el complemento del TFD",
    "idd":"Identificador previo al timbrado (si se proporcionó en la solicitud) o en caso contrario el UUID",
    "tpo":"cfdi/cr (indica de qué tipo de documento se trata)"
  }
}
```

* Si en la solicitud se estableció ```nb64=true```, el campo ```xml``` será una cadena JSON del Xml del CFDI o CR, en caso contrario será la representación en base 64 del byte array del Xml UTF-8 (incluyendo el BOM).
* Si no se indicó un ```idd``` (Identificador previo al timbrado) en la solicitud, este campo contendrá también el UUID del CFDI timbrado.

¿Por qué podría necesitar un Identificador previo al timbrado (idd)?

El idd es opcional, pero en algunos escenarios de programación puede resultar útil contar con un Identificador conocido antes de mandar a timbrar que serviría para recuperar el CFDI de la plataforma de Induxsoft incluso si perdió la conexión justo antes de recibir la respuesta del servicio Web pero despues de haber hecho el envío de la solicitud.
