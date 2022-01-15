# API de la plataforma de Induxsoft #

## Consideraciones generales ##
Todos los servicios se consumen a través de solicitudes HTTP.

Las respuestas siempre regresan el código HTTP 200 (independiéntemente del éxito o fracaso) 
con la información en JSON de acuerdo a la siguiente convención:

Respuesta de error

```
Content-Type: application/json;charset=utf-8
{
	"success":false
	"message":"Mensaje de error"
}
```

Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true
	"data":{...}
}
```
El miembro ```data``` de la respuesta contiene información específica del resultado satisfactorio del servicio.

