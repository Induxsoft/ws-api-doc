# Administración de espacios de trabajo
## Generalidades
Los espacios de trabajo son una forma de organizar y coordinar equipos de trabajo y sus derechos sobre diversos activos o servicios.

La propietariedad de un espacio de trabajo corresponde a un usuario (perfil) o a una organización (NIC).

En el caso de las organizaciones, pueden crear y administrar espacios de trabajo únicamente los usuarios "administradores" del NIC.

En todos los casos, cada espacio de trabajo puede configurar un equipo (grupo de usuarios) con permisos de administra.

## Crear un espacio de trabajo
End point: https://api.induxsoft.net/workspaces/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"create",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario",
  "workspace":{
    "name":"Nombre del espacio de trabajo"
  }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo espacio de trabajo",
    ... Todos los datos disponibles del espacio de trabajo ...
  }
}
```

## Obtener los datos de un espacio de trabajo
End point: https://api.induxsoft.net/workspaces/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"read",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario",
  "workspace":"Id del especio de trabajo a actualizar"
  }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo espacio de trabajo",
    ... Todos los datos disponibles del espacio de trabajo ...
  }
}
```

## Actualizar un espacio de trabajo
End point: https://api.induxsoft.net/workspaces/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"update",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario",
  "workspace":{
    "id":"Id del especio de trabajo a actualizar",
    "name":"Nombre del espacio de trabajo",
    ... Todos los datos a actualizar ...
  }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data":
  {
    "id":"Identificador del nuevo espacio de trabajo",
    ... Todos los datos disponibles del espacio de trabajo ...
  }
}
```

## Eliminar un espacio de trabajo
End point: https://api.induxsoft.net/workspaces/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"delete",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario",
  "workspace":"Id del especio de trabajo a eliminar"
  }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": null
}
```

## Listar todos los espacios de trabajo
End point: https://api.induxsoft.net/workspaces/

Solicitud
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Identificador de sesión válida (token)",
  "operation":"list",
  "owner":"NIC de la organización, si se omite se asume al usuario como propietario"
  }
}
```

Respuesta exitosa

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": [{ ...Información de cada espacio de trabajo..},...]
}
```
