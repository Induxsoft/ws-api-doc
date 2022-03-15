# Verificar  usuario

Verifica que el usuario indicado (por el par de credenciales id de usuario/contraseña o por un identificador de sesión) 
tenga un rol en la tienda especificada.

End point:https://pm.api.induxsoft.net/start-user-session.dkl

Solicitud con usuario/contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Correo o teléfono del usuario",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda"
}
```
Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión",
  "source":"Id de la tienda o una clave de API de una tienda"
}
```
Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
       "apikey": "La misma clave de API o id de tienda indicada en la solicitud",
        "uid": "Id del usuario",
        "storeid": "Id de la tienda",
        "storename": "Nombre de la tienda",
        "uname": "Nombre del usuario",
        "ids": "Identificador de sesión",
        "role": "Rol del usuario en la tienda (owner/manager/sales)"
  }
}
```
