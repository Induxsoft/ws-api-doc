# Solicitar acuses de cancelación #

El servicio requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario y contraseña) o un Id de sesión válida.

End point: https://factudesk.api.induxsoft.net/comprobantes/cancelaciones/acuses/

* tipo - Una cadena que indica si el uuid corresponde a un CFDI o una constancia de retenciones (CR), si se omite se asume que se trata de un CFDI. Los valores posibles son: ```cfdi```y ```cr```

Si se requiere más de un acuse, los UUIDs deberán delimiarse por comas.

Solicitud de acuses con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Identificador de usuario (correo electrónico o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "uuid":"UUID del CFDI",
  "tipo":"(opcional) cfdi/cr"
}
```

Solicitud de acuses con Identificador de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión",
  "uuid":"UUID del CFDI",
  "tipo":"(opcional) cfdi/cr"
}
```

Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":[{"uuid":"XML del acuse",...  ]
}
```

En todos los casos se devuelve un arreglo con los UUIDs y el XML del acuse en el miembro data.
