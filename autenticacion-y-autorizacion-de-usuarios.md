# Autenticación y autorización en la plataforma #

El consumo de servicios que requieren autenticación y autorización basada en el usuario (perfil) requieren un Identificador de sesión válido o el par de credenciales (usuario y contraseña).

## Autenticación ##

End point: https://api.induxsoft.net/auth/login/

### Autenticación con usuario y contraseña ###
Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
	"uid":"Identificador del usuario (correo electrónico o teléfono móvil)",
	"pwd":"Contraseña"
}
```
Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":
  {
    "ids":"Identificador de sesión válido",
    "uid":"Identificador interno del usuario",
    "name":"Nombre del usuario",
    "multifactor":true/false,
    "verified_email":true/false,
    "verified_mobile":true/false,
  }
}
```
* ids es una GUID (cadena de 32 caracteres) que representa un 'token' de sesión
* uid es una cadena con una GUID que es el identificador interno en la plataforma para el usuario
* name es el 'nombre completo' del usuario según su registro
* multifactor es un booleano que indica si está habilitada la autenticación multifactor
* verified_email indica si el correo del usuario está verificado
* verified_mobile indica si el número de teléfono móvil del usuario está verificado

### Validación de identificador de sesión ###
Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
	"ids":"Identificador de sesión a verificar",
}
```
Respuesta exitosa
```
Content-Type: application/json;charset=utf-8
{
	"success":true,
	"data":
  {
    "ids":"Identificador de sesión válido",
    "uid":"Identificador interno del usuario",
    "name":"Nombre del usuario"
  }
}
```
