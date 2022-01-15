# Timbrado de CFDI 4.0 #

El servicio de timbrado requiere autenticación a través de una Cuenta de Timbrado Induxsoft (CTI) estándar.

Consideraciones:
* Las CTI estándar no tienen caducidad (vigencia), pero están limitadas por su saldo de timbres pre-pagados

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

Respues exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":
  {
    "uuid":"UUID del Timbre Fiscal Digital (TFD)",
    "xml":"Base 64 del byte array del Xml UTF-8 del CFDI incluyendo el complemento del TFD"
  }
}
```

Si en la solicitud se estableció nb64=true, la respuesta será una cadena JSON del Xml del CFDI, en caso contrario será la representación en base 64 del byte array del Xml UTF-8 (incluyendo el BOM).
