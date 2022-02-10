# Enviar CFDI o CR #

Envía como archivos adjuntos por correo electrónico el Xml,el Xml y la representación impresa o únicamente la representación impresa de un CFDI o CR disponible en la plataforma de Induxsoft.

Este servicio requiere autenticación por usuario, por lo que deberá presentar el par de credenciales (usuario/contraseña) o un Id de sesión válido.

End point: https://factudesk.api.induxsoft.net/comprobantes/enviar/

Solicitud POST con usuario y contraseña
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "uid":"Id de usuario (correo o teléfono móvil)",
  "pwd":"Contraseña del usuario",
  "doc":"UUID del CFDI o Idd",
  "to":"Dirección de correo del destinatario",
  "from": "Nombre para mostrar del remitente (opcional)",
  "cc":"Dirección de correo cc (opcional)",
  "cco":"Dirección de correo de copia oculta (opcional)",
  "reply":"Dirección de correo de respuesta (opcional)",
  "subject":"Asunto del mensaje de correo",
  "body":"Cuerpo del mensaje de correo (opcional)",
  "tpo":"cfdi/cr (opcional)",
  "res":"(Opcional) tipo de resultado deseado",
  "pln":"(Opcional) Identificador de plantilla de representación impresa"
}
```
Solicitud POST con Id de sesión
```
Method: POST
Content-Type: application/json;charset=utf-8
{
  "ids":"Id de sesión válido",
  "doc":"UUID del CFDI o Idd",
  "to":"Dirección de correo del destinatario",
  "from": "Nombre para mostrar del remitente (opcional)",
  "cc":"Dirección de correo cc (opcional)",
  "cco":"Dirección de correo de copia oculta (opcional)",
  "reply":"Dirección de correo de respuesta (opcional)",
  "subject":"Asunto del mensaje de correo",
  "body":"Cuerpo del mensaje de correo (opcional)",
  "tpo":"cfdi/cr (opcional)",
  "res":"(Opcional) tipo de resultado deseado",
  "pln":"(Opcional) Identificador de plantilla de representación impresa"
}
```

Si se omite el parámetro ```body``` se usará la plantilla de correo predeterminada de Induxsoft.

Solicitud GET con Id de sesión
```
https://factudesk.api.induxsoft.net/comprobantes/enviar/?uid=id-de-usuario&pwd=contraseña&uuid=uuid-o-idd&tpo=cfdi/cr&res=opc&pln=id-plantilla&to=destinatario
```
Solicitud GET con usuario y contraseña
```
https://factudesk.api.induxsoft.net/comprobantes/enviar/?uid=id-de-usuario&pwd=contraseña&uuid=uuid-o-idd&tpo=cfdi/cr&res=opc&pln=id-plantilla&to=destinatario
```
El parámetro ```doc``` será el UUID de un CFDI o una constancia de retención, si se requiere más de 1, deberán delimitarse por comas. El máximo de comprobantes a enviar será de 50 y solo se admite un destinatario por solicitud.

El parámetro ```tpo``` indica el tipo de documento solicitado: cfdi-CFDI o cr-Constancia de retención, si se omite, se asume el valor cfdi como predeterminado.

Opciones para el parámetro res:
* both - Ajunta el XML y el PDF (Predeterminado)
* pdf - Adjunta únicamente el PDF
* xml - Adjunta únicamente el XML

Parámetro pln
Es una cadena que identifica una plantilla de generación de representación impresa previamente alojada y disponible en la plataforma, si se omite se aplicarán las reglas configuradas en el emisor de FactuDesk Web.

### Respuesta exitosa ###

```
Content-Type: application/json;charset=utf-8
{
  "success":true,
  "data": null
}
```

