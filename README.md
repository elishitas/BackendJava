# Guía BackendJava

## Introducción

Esta es una guía para conocer más sobre JAVA y la creación de APIS con Spring Boot


## Semana 1
- Introducción (ya lo leíste)
- [Definición de API](#Definición-de-API)
- [Tipos de APIS](#Tipos-de-APIS)
- [Funcionamiento de las APIS](#Funcionamiento-de-las-APIS)
- [REST](#REST)
- [Endpoi9nt](#Endpoint)
- [HTTP-HTTPS](#HTTP-HTTPS)
- [Definición de JSON](#Definición-de-JSON)
- [Ciclo completo](#Ciclo-completo)
- [Arqutectura en Capas](#Arqutectura-en-Capas)
- [Java](#Java)
- [Spring Framework](#Spring-Framework) 
- [Maven](#Maven)
- [Estructura del proyecto](#Estructura-del-proyecto) 
- [Clase Principal](#Clase-Principal)
- [Definición de Controller](#Definición-de-Controller)
- [Creación de un RestController](#Creación-de-un-RestController)
- [Tipos de mapeos en un rest controller de Spring Boot](#Tipos-de-mapeos-en-un-rest-controller-de-Spring-Boot)


## Semana 2
- [Services](#Services)
- [Inyección de Dependencias](#Inyección-de-Dependencias)
- [Model](#Model)
- [Entity](#Entity)
- [Domain](#Domain)
- [Mappers](#Mappers)
- [Repository](#Repository)
- [JPA](#JPA) 
- [ORM](#ORM) 

## Semana 3
- [Repaso](#Repaso)
- [Refuerzo capa Servicio](#Refuerzo-capa-Servicio)
- [Refuerzo Mappers](#Refuerzo-Mappers)
- [Manejo de Excepciones](#Manejo-de-Excepciones)
- [Tipo de respuesta HTTP](#Tipo-de-respuesta-HTTP)

## Semana 1

# Definición de API

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

# Funcionamiento de las APIS

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

Una API de REST, o API de RESTful, es una interfaz de programación de aplicaciones (API o API web) que se ajusta a los límites de la arquitectura REST y permite la interacción con los servicios web de RESTful. El informático Roy Fielding es el creador de la transferencia de estado representacional (REST).

# REST

REST no es un protocolo ni un estándar, sino más bien un conjunto de límites de arquitectura. Las personas que desarrollan las API pueden implementarlo de distintas maneras.

Cuando el cliente envía una solicitud a través de una API de RESTful, esta transfiere una representación del estado del recurso requerido a quien lo haya solicitado o al extremo. La información se entrega por medio de HTTP en uno de estos formatos: JSON (JavaScript Object Notation), HTML, XLT, Python, PHP o texto sin formato. JSON es el lenguaje de programación más popular, ya que tanto las máquinas como las personas lo pueden comprender y no depende de ningún lenguaje, a pesar de que su nombre indique lo contrario -más adelante hay definición-. 

También es necesario tener en cuenta otros aspectos. Los encabezados y los parámetros también son importantes en los métodos HTTP de una solicitud HTTP de la API de RESTful, ya que contienen información de identificación importante con respecto a los metadatos, la autorización, el identificador uniforme de recursos (URI), el almacenamiento en caché, las cookies y otros elementos de la solicitud. Hay encabezados de solicitud y de respuesta, pero cada uno tiene sus propios códigos de estado e información de conexión HTTP.

Para que una API se considere de RESTful, debe cumplir los siguientes criterios:

- Arquitectura cliente-servidor compuesta de clientes, servidores y recursos, con la gestión de solicitudes a través de HTTP.
- Comunicación entre el cliente y el servidor sin estado, lo cual implica que no se almacena la información del cliente entre las solicitudes de GET y que cada una de ellas es independiente y está desconectada del resto.
- Datos que pueden almacenarse en caché y optimizan las interacciones entre el cliente y el servidor.
-Una interfaz uniforme entre los elementos, para que la información se transfiera de forma estandarizada. Para ello deben cumplirse las siguientes condiciones:
  - Los recursos solicitados deben ser identificables e independientes de las representaciones enviadas al cliente. 
  - El cliente debe poder manipular los recursos a través de la representación que recibe, ya que esta contiene suficiente información para permitirlo.
  - Los mensajes autodescriptivos que se envíen al cliente deben contener la información necesaria para describir cómo debe procesarla.
  - Debe contener hipertexto o hipermedios, lo cual significa que cuando el cliente acceda a algún recurso, debe poder utilizar hipervínculos para buscar   las demás acciones que se encuentren disponibles en ese momento.
- Un sistema en capas que organiza en jerarquías invisibles para el cliente cada uno de los servidores (los encargados de la seguridad, del equilibrio de carga, etc.) que participan en la recuperación de la información solicitada.
- Código disponible según se solicite (opcional), es decir, la capacidad para enviar códigos ejecutables del servidor al cliente cuando se requiera, lo cual amplía las funciones del cliente. 

Si bien la API de REST debe cumplir todos estos parámetros, resulta más fácil de usar que un protocolo definido previamente, como SOAP (protocolo simple de acceso a objetos), el cual tiene requisitos específicos, como la mensajería XML y la seguridad y el cumplimiento integrados de las operaciones, que lo hacen más lento y pesado. 

Por el contrario, REST es un conjunto de pautas que pueden implementarse según sea necesario. Por esta razón, las API de REST son más rápidas y ligeras, cuentan con mayor capacidad de ajuste y, por ende, resultan ideales para el Internet de las cosas (IoT) y el desarrollo de aplicaciones para dispositivos móviles. 

Resumen de Rest:
- Interfaz uniforme
- Separación entre c-s -cliente/servidor- -Diferente a MVC-
- Sin Estado 
- Capacidad de almacenamiento en caché
- Arquitectura de sistemas en capas -Cada capa tiene un rol específico-

![1](https://i.imgur.com/sPkYWBh.png)

# Endpoint

Los endpoints son las URLs de un API o un backend que responden a una petición. Los mismos entrypoints tienen que calzar con un endpoint para existir.
Algo debe responder para que se renderice un sitio con sentido para el visitante. 

Por cada entrypoint esperando la visita de un usuario puede haber docenas de endpoints sirviendo los datos para llenar cada gráfico e infografía que se
despliega en el entrypoint.

La diferencia entre entrypoint y endpoint es que los **endpoints no están pensados para interactuar con el usuario final**. Usualmente sólo devolverán
json, o no devolverán nada. Y más que frecuentemente, un entrypoint hará varios llamados a distintos endpoints para mostrar estadísticas, galerías,
últimos comentarios, etc.

Adicionalmente, se asume que cuando se habla de un endpoint estamos en un entorno **RESTful**, por lo cual (a diferencia del uso de un browser), el
cliente *puede usar un mismo endpoint con distintos verbos* Un mismo endpoint, por ejemplo, va a devolver una lista de usuarios:

```
/users
```

# HTTP-HTTPS

El protocoloHTTP es el acrónimo de Hypertext Transfer Protocol (en español protocolo de transferencia de hiper texto). HTTPS es igual pero añadiéndole
"Seguro".
Estos dos protocolos se usan para lo mismo, la transferencia de datos. La diferencia básica entre ambos es la forma en la que viajan los datos.

La principal diferencia entre HTTP y HTTPS es la seguridad. El protocolo HTTPS impide que otros usuarios puedan interceptar la información confidencial
que se transfiere entre el cliente y el servidor web a través de Internet. Por decirlo de una manera muy sencilla, el protocolo HTTPS es la versión
segura del HTTP

La forma que tienen Request y Response de acuerdo al protocolo HTTP:

![1](https://i.imgur.com/iyHPNRW.png)

![1](https://i.imgur.com/hvSHHBy.png)

Request:
  - URL A donde queremos ir 
  - Method Metodo
  
Response
  - Status code
  
Request y Response:
  - Headers y Body

![1](https://i.imgur.com/QSXvcq8.png)

API de ejemplo [PokeApi](https://pokeapi.co/)

# Definición de JSON

JSON, que significa JavaScript Object Notation, es una formatación usada para estructurar datos en forma de texto y transmitirlos de un sistema a otro,
como en aplicaciones cliente-servidor o en aplicaciones móviles.

El archivo .json es un archivo que contiene una serie de datos estructurados en formato de texto y se usa para transferir información entre sistemas. A 
pesar de su origen estar en el lenguaje JavaScript, JSON no es un lenguaje de programación.

JSON es una notación para la transferencia de datos que sigue un estándar específico. Por eso, puede emplearse en diferentes lenguajes de programación
de sistemas.

Los datos contenidos en un archivo en formato JSON deben estructurarse por medio de una colección de pares con nombre y valor o deben ser una lista
ordenada de valores. Sus elementos tienen que contener:
  
  - Clave: corresponde al identificador del contenido. Por eso, debe ser una string delimitada por comillas.
  - Valor: representa el contenido correspondiente y puede contener los siguientes tipos de datos: string, array, object, number, boolean o null.

La transferencia de datos entre aplicaciones es realizada por medio de API —Application Programming Interface— que, entre otros formatos, utiliza la
notación JSON para estructurar la información enviada.

El archivo JSON también se usa para realizar requisiciones AJAX en sitios web, en que se hacen diferentes interacciones con bancos de datos, como MySql,
para realizar operaciones como consulta, inclusión y exclusión de registros.

Formatación del archivo JSON

  - Llaves { } sirven para delimitar los objetos y son obligatorias para iniciar y terminar el contenido.
  - Corchetes [ ] se usan para indicar un array.
  - Dos puntos : sirven para separar la clave y su valor correspondiente.
  - Coma , se usa para indicar la separación entre los elementos.
 
 Ejemplos de cómo los datos deben relacionarse en un archivo .json.

Ejemplo de un JSON:

``` json

String
{ "ciudad": "Antioquía"}

Array
{
    "ciudades": ["Monterrey", "Guadalajara", "Guanajuato"]
}

Objeto
 "ciudad": {
       "ciudad": "Guadalajara",
       "sigla": "GDL"
  }
}

Lista de objetos
{   "ciudades":[
    {"ciudad": "Guadalajara", "sigla": "GDL"},
    {"ciudad": "Monterrey", "sigla": "MTY"},
    {"ciudad": "Guanajuato", "sigla": "GTO"}
    ]
}
```
Otro Ejemplo:

``` json
{
  "squadName": "Super hero squad",
  "homeTown": "Metro City",
  "formed": 2016,
  "secretBase": "Super tower",
  "active": true,
  "members": [
    {
      "name": "Molecule Man",
      "age": 29,
      "secretIdentity": "Dan Jukes",
      "powers": [
        "Radiation resistance",
        "Turning tiny",
        "Radiation blast"
      ]
    },
}

```
# Ciclo completo

![1](https://i.imgur.com/pdDv36D.png)

# Arqutectura en Capas

La programación por capas es un estilo de programación en el que el objetivo primordial es la separación de la lógica de negocios de la lógica de diseño.

La Arquitectura Hexagonal, o la Arquitectura de Puertos y Adaptadores, como un patrón de arquitectura de diseño de software, en el que se busca
desacoplar la aplicación por componentes. Estos componentes formarán una serie de capas que serán fácilmente conectables entre si mediante puertos y
adaptadores, lo que hará que los componentes puedan llegar a ser intercambiables en cualquier nivel, y ayudará a los test automáticos.
Esta Arquitectura fue introducida por  [Alistair Cockburn](https://jmgarridopaz.github.io/content/arquitecturahexagonal.html), y según algunos
investigadores y autores, podría decirse que ha sido el precursor de la arquitectura orientada a microservicios.

Esta Arquitectura se suele representar mediante un Hexagono, en donde el número de lados representa un puerto, el cual nos permitirá ir hacia una capa
interior o exterior de la aplicación, es decir, cada componente se podrá conectar con otro componente a través de un «puerto». La comunicación entre los
puertos seguirán siempre un protocolo concreto que dependerá del objetivo o función que tenga. La comunicación será definida a través, por ejemplo de un
API.

![1](https://i.imgur.com/wcf48jz.png)

La idea principal detrás de este tipo de arquitectura, es crear un componente central o núcleo rodeados de interfaces a través del cual se pueda acceder.
Es decir, lo que se propone es un núcleo central, que ocuparía el hexagono más interior, en el que se tendrían los dominios y los repositorios, que
expondrían un API o Interfaces para poder obtener datos a partir de ellos.

# Java
[Java](https://dev.java/learn/) es un lenguaje de programación de alto nivel que nos ayuda a construir aplicaciones para diferentes dispositivos y
sistemas operativos.

[Función Lambda](https://www.youtube.com/watch?v=8LVdhVMNQSw&ab_channel=miw-upm)

# Spring Framework 

Como definición podemos decir que Spring es un framework de código abierto para la creación de aplicaciones empresariales Java

[Info](https://spring.io/)

[Documentación](https://docs.spring.io/spring-framework/docs/current/javadoc-api/index.html)

[Inicializador de Spring](https://start.spring.io/)

# Maven

Maven es un “Project Management Framework”, esto es, un framework de gestión de proyectos de software, que proporciona un modelo estándar de gestión y
descripción de proyectos. Maven da soluciones a tareas que abarcan desde la compilación hasta la distribución, despliegue y documentación de los
proyectos

# Estructura del proyecto 

Al bajar de [Inicializador de Spring](https://start.spring.io/)

El proyecto tiene diferentes carpetas las cuales en la Clase 1 solamente vamos a observar:

Main

Java

![1](https://i.imgur.com/6844JYi.png)

![1](https://i.imgur.com/uvX21Io.png)

# Clase Principal

Es la clase principal. Toda aplicación en java debe contener una clase principal con un método main. Dicho método, en caso de implementar una aplicación
con Spring, deberá llamar al método run de la clase SpringApplication. 

![1](https://i.imgur.com/sVuxFSr.png)

# Definición de Controller

Las clases que definimos como un *controller* es responsable de procesar las llamadas entrantes (**request**) que ingresan a nuestra aplicación,
validarlas y dar una respuesta (**response**).

Los controladores sirven para comunicar información entre la vista y el modelo . Es decir yo por ejemplo puedo tener una lista de Personas a nivel del
Modelo y quiero pasarlo a la vista y que la vista se encargue de mostrar la información que tenemos en el modelo.

Un *rest controller* es un tipo de *controller* que reciben peticiones con un formato de específico que cumple con formatos de solicitud RESTful
habitualmente y mayormente en JSON , aunque a veces se usan otros como HTML, XML, o simplemente texto.

# Creación de un RestController

El primer paso para crear un ‘controlador rest’ es con la clase *@RestController*.

Con esto Spring ya sabe que esa clase será un componente encargado de recibir llamadas.

```
@RestController
public class HelloWordController {
}
```
Una vez que hemos anotado la clase podemos definir el método y la ruta en la cual recibirá la llamada externa.

Anotamos el método que da respuesta con *@GetMapping* y le indicamos la ruta en la cual responderá . Aquí definimos el path “/hello”.

```
@RestController
public class HelloWordController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello dev";
    }

}
```
Arrancamos la aplicación.

Ahora podemos invocar nuestro *RestController* mediante una llamada en el path ‘/hello’ que definimos previamente.

El servicio levanta en ‘localhost:8080’ y el path es ‘/hello’. Vemos la respuesta ‘Hello dev‘

![1](https://i.imgur.com/stlHrl7.png)

# Tipos de mapeos en un rest controller de Spring Boot

Anteriormente creamos un *mapping* para el path ‘/hello’ . Este mapeo lo definimos como un *@GetMapping*.

Sin embargo, debemos saber que hay otros tipos de *mapping* en Spring Boot.

![1](https://i.imgur.com/APY5SEv.png)

En los métodos de un mapeo podemos usar:

- **Get**: para solicitar información de un recurso.
- **Post**: para enviar información a fin de crear o de actualizar un recurso.
- **Put**: para enviar información a fin de modificar un recurso.
- **Patch**: actualiza una parte del recurso.
- **Delete**: elimina un recurso específico.

Diferencia entre Post , Put, Patch

Habitualmente la diferencia entre Post y Put radica en que Post lo usamos para **añadir** un recurso y Put lo utilizamos para **modificar** un recurso en particular.

Patch también lo utilizamos para actualizar un recurso pero solo una **parcialidad** del mismo.

Ejemplos de mapeo en Spring Boot

A continuación vemos ejemplos simples de mapeo.

Para el caso del ***GetMapping*** estamos pidiendo mediante un *id* al recurso *User*. A fin de recibir este *id* utilizamos *PathVariable*

Para el ***PostMapping, PutMapping, ***PatchMapping*** se recibe un request con el body del User que se quiere insertar o actualizar.

El uso de ***RequestBody*** permite que Spring entienda la info que mandamos *body* de la petición.

En el ***DeleteMapping*** recibimos también *id* que identifica el objeto a eliminar y se devuelve true / false según si se pudo eliminar o no.

```
@RestController
public class UserController {

    private final UserService userService;

    public UserController(UserService userService) {
        this.userService = userService;
    }

    @GetMapping("/api/user/{id}")
    public User byId(@PathVariable("id") int id) {
        return userService.find(id);
    }

    @PostMapping("/api/user/")
    public User create(@RequestBody User user) {
        return userService.create(user);
    }

    @PutMapping("/api/user/")
    public User update(@RequestBody User user) {
        return userService.update(user);
    }

    @PatchMapping("/api/user/")
    public User change(@RequestBody User user) {
        return userService.change(user);
    }

    @DeleteMapping("/api/user/{id}")
    public boolean delete(@PathVariable("id") int id) {
        return userService.remove(id);
    }

}
```
## Semana 2

# Services

# Inyección de Dependencias

En informática, **inyección de dependencias** (en inglés *Dependency Injection*, DI) es un patrón de diseño orientado a objetos, en el que se suministran
objetos a una clase en lugar de ser la propia clase la que cree dichos objetos. 

Esos objetos cumplen contratos que necesitan nuestras clases para poder funcionar (de ahí el concepto de *dependencia*). 

Nuestras clases no crean los objetos que necesitan, sino que se los suministra otra clase 'contenedora' que inyectará la implementación deseada a nuestro
contrato. En otras palabras, se trata de un patrón de diseño que se encarga de extraer la responsabilidad de la creación de instancias de un componente
para delegarla en otro.

Patrón de Diseño: Es una solución general reusable que puede ser aplicada a problemas que ocurren comúnmente en el desarrollo de software, es la
descripción o plantilla de como resolver un problema que puede ser usada en diferentes situaciones. Los patrones de diseño son soluciones probadas,
expresivas y fáciles de mantener.

Otra Explicacion de Dependencias: Consiste en pasar la dependencia a la clase que la va a utilizar, en lugar de crearla internamente dentro de esa clase,
con el fin de no acoplar la clase a la implementación que está utilizando. Este proceso se le conoce como inyectar una dependencia.

  - Inversión de control(IoC): Se refiere a que es un framework (en este caso Spring) el que toma control de los objetos. Spring contiene un contenedor
  de IoC, el cual se encarga de administrar y crear instancias de objetos que se conocen como *Beans* o *Components*. Para esto, Spring utiliza la 
  anotación `@Autowired` para hacer inyección de dependencias.
    
    - Existen tres maneras de usar la inyección dependencias con `@Autowired`: en el atributo, en el constructor y en el método set. A pesar de que
    hacerlo en el atributo (Field-based) es lo más práctico, elegante y la manera en que mejor se lee; lo mejor es hacerlo en el constructor
    (Constructor-based) para poder declarar los atributos inyectados como final para que sean inmutables, y además es muy recomendado para declarar
    dependencias obligatorias. Asimismo se evita que la dependencia en un momento determinado pueda ser null.
        
    - En Java, al declarar un objeto y no inicializarlo, obtiene por defecto el valor `null`. Esto porque en Java debemos crear los objetos antes de
    poderlos utilizar. Ejemplo: `private ProductMapper mapper;`. Si lo utilizamos (Ej: `mapper.toProducts(productos);`), no lo estamos inicializando, y
    tendríamos algo como `null.toProducts(productos);`, y el objeto *null* no puede llamar al método *toProducts()*. Spring nos ayuda a crear estos
    objetos gracias a su IoC.
    
    - Al utilizar `@Autowired`, le damos a entender a Spring que los objetos que tengan esa anotación, le cedemos el control a Spring para que cree las
    instancias de esos objetos. Gracias a eso, no nos preocuparemos por crear objetos manualmente, lo cual puede ser una mala práctica. Solo se
    debe tener cuidado que, cuando se vaya a utilizar la anotación, se debe estar totalmente seguro que el objeto que se va a inyectar es un componente
    de Spring

# Model

![1](https://i.imgur.com/2zK99Oq.png)

# Entity

La idea es que la entidad refleje la estructura de la base de datos entonces es donde guardamos las entidades que se van a corresponder con tablas a la base de datos. Es lo más cercano a la base de datos es la entidad como vimos en la Estructura de Capas:

![1](https://i.imgur.com/sPkYWBh.png)

Una [entidad](https://desarrollodesoftware.home.blog/2019/03/03/que-es-una-entidad-en-java-ee-y-como-declararla/) en Java es un objeto de persistencia.

La persistencia es la habilidad de una aplicación para mantener(persistir) y recuperar información de sistemas de almacenamiento no volátiles.

Una entidad representa una tabla en una base de datos, y cada instancia de entidad corresponde a una fila en la tabla.

El estado de una entidad se representa por campos de persistencia o propiedades de persistencia.

Una entidad es la representación de información que necesitamos en nuestra aplicación.Esta entidad podría ser un usuario, un producto o cualquier dato
que nuestra aplicación necesita mantener persistente para luego recuperarla cuando la necesite. Es un objeto, elemento o ‘cosa’ con atributos
particulares que lo distinguen. Por ejemplo, este podría ser un ‘user (usuario)’ sobre el que necesitamos conocer sus atributos como el nombre, edad,
email, etc

Definición de una [entidad](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#data.sql.jpa-and-spring-data.entity-classes)

- Defines la entidad con la anotación *`@Entity`*
- Es necesario una *primary key (PK)* (clave primaria) con *`@ID`*
- El valor de esta *PK* es generada automáticamente con esta anotación *`@GeneratedValue`* con el valor AUTO

Hay otras anotaciones que puedes utilizar.

- *`@Table`* para definir explícitamente el nombre de la tabla.
- *`@Column`* para definir el nombre de la columna.

![1](https://i.imgur.com/DlVeKnK.png)

[GeneraredValue](https://javaee.github.io/javaee-spec/javadocs/)

# Domain

DTO Una de las problemáticas más comunes cuando desarrollamos aplicaciones, es diseñar la forma en que la información debe viajar desde la capa de servicios
a las aplicaciones o capa de presentación, ya que muchas veces por desconocimiento o pereza, utilizamos las clases de entidades para retornar los datos,
lo que ocasiona que retornemos más datos de los necesarios o incluso, tengamos que ir en más de una ocasión a la capa de servicios para recuperar los
datos requeridos.

El patrón DTO tiene como finalidad de crear un objeto plano (POJO) con una serie de atributos que puedan ser enviados o recuperados del servidor en una
sola invocación, de tal forma que un DTO puede contener información de múltiples fuentes o tablas y concentrarlas en una única clase simple.

![1](https://i.imgur.com/VQdhQT4.png)

En la imagen anterior podemos apreciar gráficamente como es que un **DTO** se conforma de una serie de **atributos** que puede o no, estar conformados
por más de una **fuente de datos**. 

Para esto, el servidor obtiene la información de las tablas customer y address (izquierda) y realiza un mapping con el DTO (derecha). 

Adicional, la información puede ser pasada de un lado intacta como es el caso del id , fullName , country , address  y zipCode  o ser una derivada de más
de un campo, como es el caso del fullName , el cual es la unión del firstname  y lastname .

Otra de las ventajas no tan claras en la imagen, es que nos permite omitir información que el usuario no requiere, como es el caso de password. No es
solo que no lo requiere, sino que además podría ser una gran falla de seguridad está enviando los passwords, es por ello que en el **DTO** lo omitimos.

Características de un DTO

Si bien un DTO es simplemente un objeto plano, sí que tiene que cumplir algunas reglas para poder considerar que hemos creado un DTO correctamente
implementado:

  - Solo lectura: Dado que el objetivo de un DTO es utilizarlo como un objeto de transferencia entre el cliente y el servidor, es importante evitar tener
  operaciones de negocio o métodos que realicen cálculos sobre los datos, es por ello que solo deberemos de tener los métodos GET y SET de los
  respectivos atributos del DTO.
  - Serializable: Es claro que, si los objetos tendrán que viajar por la red, deberán de poder ser serializables, pero no hablamos solamente de la clase
  en sí, sino que también todos los atributos que contenga el DTO deberán ser fácilmente serializables. Un error clásico en Java es, por ejemplo, crear
  atributos de tipo Date o Calendar para transmitir la fecha u hora, ya que estos no tienen una forma estándar para serializarse por ejemplo en
  Webservices o REST.

Entity vs DTO

Un error muy frecuente es el hecho de utilizar las clases de Entidad para utilizarlos para la transmisión de datos entre el cliente y el servidor. Solo
para entrar en contexto, las **entidades** son clases que representa al modelo de datos, o mapea directamente contra una tabla de la base de datos. Dicho
esto, las **entidades** son clases que fueron diseñadas para mapear contra la base de datos, no para ser una vista para una pantalla o servicio
determinado, lo que provoca que muchos de los campos no puedan ser serializables, no contengan todos los campos necesarios un servicio, ya sea que tengan
de más o de menos.

El hecho de que las entidades no contengan todos los atributos necesarios o que no sean serializables trae otros problemas, como la necesidad de agregar
más atributos a las entidades con el único objetivo de poder cubrir los requerimientos de transferencia de datos, dejando de lado el verdadero propósito
de la entidad, que es únicamente mapear contra la base de datos, lo que va llevando lentamente a ir creando una mezcla entre Entidad y DTO.

![1](https://i.imgur.com/IaWBT0t.png)

Ejemplo de un DTO

Para comprender mejor como es que se utilizan los **DTO**, vamos a realizar un análisis con un ejemplo de un servicio que recupera los datos todos los
datos de los clientes. Para esto, veamos como quedarían las Entidades utilizando el API de JPA de Java.

Entidad Customer:

```
package dtopattern;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name="customers")
public class Customer {
	@Id
	@GeneratedValue(strategy= GenerationType.IDENTITY)
	private Long id;
	@Column(name="firstname")
	private String firstname;
	@Column(name="lastname")
	private String lastname;
	@Column(name="password")
	private String password;
	
	/** GET and SET */
}

```
Entidad Address:

```
package dtopattern;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.JoinColumn;
import javax.persistence.ManyToMany;
import javax.persistence.Table;

@Entity
@Table(name="address")
public class Address {
	@Id
	@GeneratedValue(strategy=GenerationType.IDENTITY)
	private Long id;
	@ManyToMany()
	@JoinColumn(name="fk_customer")
	private Customer customer;
	@Column(name="country")
	private String country;
	@Column(name="address")
	private String address;
	@Column(name="zipcode")
	private String zipCode;
	
	/** GET and SET */
}
```
Por otro lado, tenemos el DTO que contiene los datos del cliente (Customer) y su dirección (Address)

```
package dtopattern;

import java.io.Serializable;

public class CustomerDTO implements Serializable{
	
	private Long id;
	private String FullName;
	private String country;
	private String Address;
	private String zipCode;
	
	/** GET and SET */
}
```
Finalmente, veamos cómo quedaría un servicio que aproveche las ventajas del patrón DTO para transmitir los datos:

```
package dtopattern;

import javax.ejb.EJB;
import javax.ejb.Stateless;
import javax.ws.rs.GET;
import javax.ws.rs.Path;
import javax.ws.rs.PathParam;
import javax.ws.rs.core.MediaType;
import javax.ws.rs.core.Response;

@Path("customers")
public class CustomerService {
	
	@GET
	@PathParam("{customerId}")
	private Response findCustomer(@PathParam("customerId") Long customerId) {
		Customer customer = customerDAO.findCustomerById(customerId); //Entity
		Address address = customerDAO.findAddressByCustomer(customerId); //Entity
		
		//Create dto
		CustomerDTO dto = new CustomerDTO();
		dto.setAddress(address.getAddress());
		dto.setCountry(address.getCountry());
		dto.setZipCode(address.getZipCode());
		dto.setFullName(customer.getFirstname() + " " + customer.getLastname());
		dto.setId(customer.getId());
		
		//Return DTO
		return Response.ok(dto, MediaType.APPLICATION_JSON).build();
	}
}

```
El ejemplo que acabamos de ver, corresponde a una implementación de un servicio **REST** utilizando el API JAX-RS de Java, el cual indica que existe un
servicio **GET** en la url *`/customers/{customerID}`*, donde *`{customerId}`* corresponde al **ID** del cliente a buscar. 

En el servicio, realizamos la consulta del cliente y su dirección en dos pasos, para finalmente, mapear los datos de estas dos entidades en un simple
**DTO** que será retornado.

Conclusión: Como hemos podido demostrar, los DTO son un patrón muy efectivo para transmitir información entre un cliente y un servidor, pues permite 
crear estructuras de datos independientes de nuestro modelo de datos, lo que nos permite crear cuantas “vistas” sean necesarias de un conjunto de tablas
u orígenes de datos. Además, nos permite controlar el formato, nombre y tipos de datos con los que transmitimos los datos para ajustarnos a un
determinado requerimiento. Finalmente, si por alguna razón, el modelo de datos cambio (y con ello las entidades) el cliente no se afectará, pues seguirá
recibiendo el mismo DTO.

# Mappers

El modelo [mapper](http://modelmapper.org/user-manual/spring-integration/) tiene la finalidad de facilitar la conversión, el traspaso de unos datos de un objeto entity a otra entity.

El objetivo de ModeMaper es hacernos el mapeo entre objetos más sencillo, para ello, tenemos que definir el modelo (en este caso, el objeto inicial) que
se mapeará y el modelo final (en este caso, el objeto final) sobre el que volcará los valores mapeados.

![1](https://i.imgur.com/vMHyh1W.png)

# Repository

Es el siguiente nivel del model.

El repositorio son las interfaces que utilizamos para definir como van accederse a los datos de nuestra base de datos.

![1](https://i.imgur.com/8CLFJyJ.png)

Entonces un micro-servicio lo dividimos en capas, siendo el repository la capa de persistencia que tiene acceso a los datos y que puede manipularlos.

En Spring un ‘**Repository**’ es el componente encargado de resolver el acceso a los datos de nuestro micro-servicio. Si necesitamos guardar, modificar,
eliminar registros de un ‘User’ del sistema; será entonces el componente *`UserRepository`* el encargado de realizar cambios directos sobre los registros
de Usuario.

Spring nos provee las funcionalidades básicas para guardar, eliminar y buscar entidades. Para esto tenemos todas las *interfaces* que extienden de
“org.springframework.data.repository.Repository”.

![1](https://i.imgur.com/jyBN8Dt.png)

Para una entidad *`User`* se puede pensar en las operaciones básicas para crear, modificar y buscar (CRUD).

**CRUD** es un acrónimo que refiere a las cuatro funciones mínimas sobre una entidad –> Create, Read, Update, Delete.

La entidad se ve así:

```
@Entity
public class User {

    @Id @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;
    private String name;
    private String surname;
    private LocalDate birthDate;
```

Luego se crea una ***interface UserRepository*** que extenderá de ***CrudRepository***. Anotamos la clase ‘UserRepository’ como un
componente *`@Repository`* .

**CrudRepository** es una interfaz genérica que recibe dos tipos. El primero es la clase que esta interfaz manejará y el segundo es el tipo de dato
del *ID* de la entidad.

Importante, que NO implementamos la interfaz. Creamos una nueva interfaz y extendemos de ***CrudReposity***. Será Spring el encargado de la
implementación de la interfaz con la clase concreta.

Los métodos que provee ***CrudRepository*** son:

- **save**: guarda una entidad
- **saveAll**: guarda las entidades de una lista iterable
- **findById**: busca por el identificador
- **existsById**: verifica si existe un identificador
- **findAll**: devuelve todos los elementos para la entidad
- **findAllById**: busca todos los elementos que tengan el identificador
- **count**: devuelve el total de registros de la entidad
- **deleteById**: elimina un registro para el identificador
- **delete**: elimina la entidad
- **deleteAllById**: elimina todos los elementos que correspondan con el id
- **deleteAll**(Iterable): elimina todos los elementos que se reciban en el parámetro
- **deleteAll()**: elimina todos los elementos

![1](https://i.imgur.com/fgYKk9F.png)

La interfaz UserRepository que extiende de CrudRepository.

```
import com.example.springbootcourse.model.User;
import org.springframework.data.repository.CrudRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface UserRepository extends CrudRepository<User, Long> {
}
```
Con esto ya tenemos creado el repository con las operaciones CRUD para la entidad.

JPA:

```
package com.academia.app.rest.model.repositories;

import com.academia.app.rest.model.entities.ContactEntity;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface ContactRepository extends JpaRepository<ContactEntity, Integer> {
}
```
# JPA

JPA (**J**ava **P**ersistence **A**PI) es una especificación de Java, standar, para un framework ORM.  Quiere decir que son una serie de reglas que Java define para que cualquier framework que quiera interactuar con la BD de Java, tenga que seguir.

Los frameworks mas populares de Java para este fin son:

  - Hibernate
  - TopLink
  - EclipseLink
  - ObjectDB

JPA utiliza anotaciones para conectar clases a tablas de la BD y así evitar hacerlo de manera nativa con SQL.

  - `@Entity`. Indica a una clase de java que esta representando una tabla de nuestra BD.
  - `@Table`. Recibe el nombre de la tabla a la cual esta mapeando la clase.
  - `@column`. Se le pone a los atributos de la clase, no es obligatoria, se indica sólo cuando el nombre de la columna es diferente al nombre del
  - atributo de la tabla.
  - `@id` and `@EmbededID`. Es el atributo como clave primaria de la tabla dentro de la clase. `@id` se utiliza cuando es clave primaria sencilla
    y 
  - `@EmbededID` cuando es una clave primaria compuesta.
  - `@GeneratedValue`. Permite generar automáticamente generar valores para las clases primarias en nuestras clases
  - `@OneToMany` and `@MatyToOne`. Representar relaciones

JPA es un conjunto de especificaciones ORM

# ORM

ORM (**O**bject **R**elational **M**apping) Es una **herramienta** que realiza un **mapeo** que nos permite **transformar** los objetos de la base de
datos como **tablas y esquemas a clases con atributos** en código de programación para poder manipular la información de una forma más fácil sin requerir
de SQL.

Spring ofrece la posibilidad de aplicar esta técnica utilizando Hibernete

# Más info:

- [Arquitectura de software y Spring](https://gustavopeiretti.com/es/)

## Semana 3

# Repaso

La clase 1 y Clase 2 se ve como se estructura la Api.

Tener las 3 carpetas:
  - Controllers
  - Model
  - Service

En el modelo se modela el problema a resolver, dentro del modelo hay 4 capas:

  - En el corazón está la base de datos, es el centro.

- Capa de Entidad: 

  - Luego las capas que tiene La Capa Model se van acomodando desde afuera del centro hacia el exterior 
	
  - Entities: Se encuentra más en contacto con la base de datos, se coloca todas las propiedades.
    Nombre, tipo de datos.
    Una etiqueta que se puede sumar es @table: El nombre de la tabla.
			 
  - Domain: El objeto que se encuntra en contacto con el dominio, con las respuesta que llega a nuestra api, son dto que sirven para no
    exponer las entidades, las tablas de la base de datos, se pueden tener varios dto.
		
  - Mappers: Mapea que valores de la entidad a los dto, tiene la función de hacer el mappeo.
		
  - Repository: Extendemos una clase JPA, se puede hacer funciones para hacer consultas más especificas. 
  Con esta clase interactuamos directamente con la base de datos, hace el CRUD 
	
- Capa de Servicio: 
		
  - Está la lógica de negocios, su mapeador, su repositorio.
  - Se inyectan objetos.
  - Siempre se pone la lógica de negocios.
	
- Capa Controller:
	
  - Es el enrutador de las peticiones que van llegando a la API, deriva a los diferentes lugares que fuese necesario.

# Refuerzo capa Servicio

# Refuerzo-Mappers

# Manejo de Excepciones

# Tipo de respuesta HTTP


