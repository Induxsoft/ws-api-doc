# Cancelación de CFDI 4.0 #

El servicio de cancelación requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario y contraseña) o un Id de sesión válida.

End point: https://factudesk.api.induxsoft.net/cfdi/cancelacion/4.0/

Solicitud de cancelación con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Identificador de usuario (correo electrónico o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "uuid":"UUID del CFDI",
  "motivo":"Clave de motivo de cancelación del SAT",
  "frel":"(Opcional) UUID del CFDI relacionado, en caso de que el motivo sea'01'"
}
```

* motivo - 01, 02, 03 o 04 según el catálogo de claves del SAT

Solicitud de cancelación con Identificador de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión",
  "uuid":"UUID del CFDI",
  "motivo":"Clave de motivo de cancelación del SAT",
  "frel":"(Opcional) UUID del CFDI relacionado, en caso de que el motivo sea'01'"
}
```

Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":null
}
```
