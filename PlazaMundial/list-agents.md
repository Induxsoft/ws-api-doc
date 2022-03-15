# Listar agentes

Se considera un agente a todo colaborador de la tienda en PlazaMundial.Net

Este servicio retornará un array JSON con todos los colaboradores que estén dados de alta.

End point: https://pm.api.induxsoft.net/leads/list-agents.dkl

Solicitud con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono)",
  "pwd":"Contraseña del usuario",
  "source":"Id de la tienda o una clave de API de una tienda"
}
```

Solicitud con id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión",
  "source":"Id de la tienda o una clave de API de una tienda"
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  [
    {
      "id": "Id del perfil del agente",
      "name": "Nombre del agente",
      "manager": true/false (si es un dueño/gerente o no)
    },
    { ... },..
  ]
}
```
