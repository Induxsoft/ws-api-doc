# Subir CFDI #

Este servicio no requiere autenticación

End point: https://factudesk.api.induxsoft.net/cfdi/subir/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "xml":"Xml del CFDI a alojar",
  "nb64":true/false (opcional)
}
```
* xml - Es una cadena que contiene la representación codificada en base 64 del byte array del Xml UTF-8 de un CFDI, a menos que nb64=true
* nb64 - Es un parámetro opcional booleano que si se establece en ```true``` indica que el Xml del CFDI está codificado como una cadena JSON.

Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":null
}
```
