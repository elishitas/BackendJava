# Guía BackendJava

## Introducción

Esta es una guía para conocer más sobre JAVA y la creación de APIS con Spring Boot


## Semana 1
- Introducción (ya lo leíste)
- [¿Qué es una API?](#¿Qué-es-una-API?)
- [Tipos de APIS](#Tipos-de-APIS)
- [¿Cómo funcionan las API?](#¿Cómo-funcionan-las-API?)
- [¿Qué es JSON? ¿Para qué sirve?](#Qué-es-JSON?)
  - Them
  - Them

# ¿Qué es una API?

Las **API** son mecanismos que permiten a dos componentes de software **comunicarse** entre sí mediante un conjunto de definiciones y protocolos. 

API significa “interfaz de programación de aplicaciones”. 

En el contexto de las API, la palabra aplicación se refiere a cualquier software con una función distinta. 

La interfaz puede considerarse como un contrato de servicio entre dos aplicaciones. Este contrato define cómo se comunican entre sí mediante solicitudes y respuestas. 

La documentación de una API contiene información sobre cómo developers deben estructurar esas solicitudes y respuestas.

# Tipos de APIS

- **API privadas**

Estas son internas de una empresa y solo se utilizan para conectar sistemas y datos dentro de la empresa.

- **API públicas**

Están abiertas al público y cualquier persona puede utilizarlas. Puede haber o no alguna autorización y coste asociado a este tipo de API.

- **API compuestas**

Estas combinan dos o más API diferentes para abordar requisitos o comportamientos complejos del sistema.

- **API de socios**

Solo pueden acceder a ellas los desarrolladores externos autorizados para ayudar a las asociaciones entre empresas.

# ¿Cómo funcionan las API?

La arquitectura de las API suele explicarse en términos de **cliente** y **servidor**. La aplicación que envía la solicitud se llama **cliente**, y la que envía la respuesta se llama **servidor**. 

Las API pueden funcionar de cuatro maneras diferentes, según el momento y el motivo de su creación.

- **API de SOAP**

Estas API utilizan el protocolo simple de acceso a objetos. El cliente y el servidor intercambian mensajes mediante XML. Se trata de una API menos flexible que era más popular en el pasado.

- **API de RPC**

Estas API se denominan llamadas a procedimientos remotos. El cliente completa una función (o procedimiento) en el servidor, y el servidor devuelve el resultado al cliente.

- **API de WebSocket**

La API de WebSocket es otro desarrollo moderno de la API web que utiliza objetos JSON para transmitir datos. La API de WebSocket admite la comunicación bidireccional entre las aplicaciones cliente y el servidor. El servidor puede enviar mensajes de devolución de llamada a los clientes conectados, por lo que es más eficiente que la API de REST.

- **API de REST**

Estas son las API más populares y flexibles que se encuentran en la web actualmente. El cliente envía las solicitudes al servidor como datos. El servidor utiliza esta entrada del cliente para iniciar funciones internas y devuelve los datos de salida al cliente.
