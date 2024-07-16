<h1 align="center">
  <br>
  <a href="https://www.oracle.com/mx/education/oracle-next-education/"><img src="https://github.com/JoelTotoR/API-REST-ForoHub/blob/main/Badge-Spring.png" alt="insignia challenge foro hub" width="450"></a>
  <br>
  Challenge ForoHub 
  <br>
</h1>

<h4 align="center">API REST de un foro desarrollada en Java con Spring Boot.</h4>
<p align="center">
  <a href="https://www.java.com" target="_blank">
    <img src="https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=java&logoColor=white" alt="Java" />
</a>
<a href="https://spring.io/projects/spring-boot" target="_blank">
    <img src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white" alt="Spring Boot" />
</a>
<a href="https://www.mysql.com/" target="_blank">
    <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white" alt="MySQL" />
<a href="https://insomnia.rest/" target="_blank">
    <img src="https://img.shields.io/badge/Insomnia-4000BF?style=flat-square&logo=insomnia&logoColor=white" alt="Insomnia" />
</a>

<a href="https://www.jetbrains.com/idea/" target="_blank">
    <img src="https://img.shields.io/badge/IntelliJ%20IDEA-000000?style=flat-square&logo=intellij-idea&logoColor=white" alt="IntelliJ IDEA" />
</a>
</p>


## Descripción
Esta es una API REST desarrollada en Java utilizando Spring Boot y varias dependencias. La API permite la interacción de usuarios en un foro de una plataforma de cursos en línea.Las principales funcionalidades incluyen publicación de tópicos relacionados con los cursos, respuestas a dichos tópicos, registro de nuevos usuarios y otras funcionalidades más.



## 🎨 Caracteristicas
- **❔ Topicos**
  - Listar los tópicos creados por los usuarios
  - Publicar un nuevo tópico
  - Editar el tópico creado
  - Actualizar status del tópico (ACTIVO, INACTIVO, RESUELTO)
- **🙍‍♂️🙎‍♀️Usuario**
  - Registrar nuevos usuarios
  - Editar información
  - Conocer los usuarios registrados
  - Dar de baja usuarios
- **📚 Cursos**
  - Listar los cursos disponibles
  - Registrar nuevos cursos
  - Editar la información del curso
  - Desactivar curso
- **✅ Respuestas**
  - Listar las respuestas de los tópicos
  - Responder tópicos de otros usuarios
  - Editar la respuesta publicada
- **🔒 Validación de usuarios por Json Web Token (JWT)**

## 💻 Tecnologías

Las tecnologías empleadas para la elaboración del proyecto son:

- Java
- Spring Boot
- MySql
- Auth0
- lombook
- flyway
- Open Api Spring doc
- Spring security


## 🚩 Endpoints

A continuación se muestran cuatro de los principales endpoints de la API; sin embargo, recomiendo ampliamente instalar el proyecto y revisar la documentación en Swagger para conocer todas las funcionalidades.

_Los resultados se muestran en el puerto 8080 del localhost, pero puede configurarlo al que desee._


#### Generar JWT
Para acceder a las funcionalidades de la API, es necesario agregar un JSON Web Token (JWT) en la autorización de tipo Bearer. Para obtener este token, debes enviar una solicitud con un nombre de usuario y una contraseña válidos en el cuerpo de la solicitud (body) a la siguiente URL:

##### url
```
http://localhost:8080/login
```

##### Request Body
```
{
	"usuario": "nombreUsuario",
	"contrasena": "contraseña"
}
```

##### Request Body
```
{
	"token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJNYXJpZSBSb2phcyIsImlzcyI6ImZvcm9odWIiLCJpZCI6MywiZXhwIjoxNzIxMDk2MjA2fQ.OgTYaCKhwZALWQHtrdeHwImxz-t3o9lifZq0e80gdXs"
}
```
El token de la solicitud tiene una vigencia de 2 horas; por lo tanto, pasado ese tiempo, el token generado habrá expirado y será necesario generar uno nuevo.

#### GET - Listar los tópicos publicados
##### url
```
http://localhost:8080/topicos
```

##### Response Body: (200 - Ok)
```
{
	"totalPages": 2,
	"totalElements": 7,
	"size": 5,
	"content": [
		{
			"id": 3,
			"nombre": "Practicando Spring Framework: Challenge Foro Hub",
			"categoria": "CHALLENGE"
		},
		{
			"id": 4,
			"nombre": "Desarrollo de carrera: demanda del mercado",
			"categoria": "DESARROLLO"
		},
		{
			"id": 5,
			"nombre": "Propósito profesional: ser el protagonista de tu carrera",
			"categoria": "DESARROLLO"
		},
		{
			"id": 6,
			"nombre": "Java: trabajar con listas y colecciones de datos",
			"categoria": "PROGRAMACION"
		},
		{
			"id": 7,
			"nombre": "Practicando Spring Boot: Challenge Literalura",
			"categoria": "CHALLENGE"
		}
	],
	"number": 0,
	"sort": {
		"empty": true,
		"sorted": false,
		"unsorted": true
	},
	"numberOfElements": 5,
	"pageable": {
		"pageNumber": 0,
		"pageSize": 5,
		"sort": {
			"empty": true,
			"sorted": false,
			"unsorted": true
		},
		"offset": 0,
		"paged": true,
		"unpaged": false
	},
	"first": true,
	"last": false,
	"empty": false
}
```

Los parametros del listado como el tamaño, el orden entre otros. Puede ser modificados agregando `?size={}&page={}` entre otros.

#### POST - Publicar una nueva respuesta
##### url

```
http://localhost:8080/respuesta
```

##### Request Body
```
{
	"mensaje": "Error en las variables de entorno",
	"topico_id": "1",
	"autor_id": "1",
	"solucion": "Deberias revisar que java pueda reconocer las variables de entorno ya que puede que no pueda acceder a los perfiles de las bases"
}
```


##### Response Body: (201 - Created)
```
{
	"id": 3,
	"topico": "Error al hacer el deploy",
	"mensaje": "Error en las variables de entorno",
	"fechaCreacion": "2024-07-15T18:44:29.1177932",
	"autor": "Joel Toto_po",
	"solucion": "Deberias revisar que java pueda reconocer las variables de entorno ya que puede que no pueda acceder a los perfiles de las bases"
}
```

##### Response Header
```
Location	http://localhost:8080/respuesta/3
```

#### PUT - Actualizar estado de un tópico
```
http://localhost:8080/topicos/3/resuelto
```

##### Response Body: (200 - Ok)
```
{
	"id": 3,
	"titulo": "Requisitos fullstack",
	"mensaje": "Si quiero ser FullStack, que herramientas deberia apender",
	"curso": "Desarrollo de carrera: demanda del mercado",
	"autor": "Joel Toto_po",
	"fechaCreacion": "2024-07-15T12:44:29",
	"status": "RESUELTO"
}
```


#### PUT - Actualizar estado de un tópico
```
http://localhost:8080/usuarios/3
```

#####  Respuesta: (204 - No Content)

## Diagrama base de datos

<div align="center">
<img src="https://github.com/JoelTotoR/API-REST-ForoHub/blob/main/diagrama_base_de_datos_forohub.png" alt="diagrama base de datos foro hub" width="500">
</div>

## Folow me
<div class="redes" align="center">
    <a href="https://www.facebook.com/profile.php?id=100005125908086&mibextid=ZbWKwL" target="_blank" title="Facebook"><img src="https://img.icons8.com/color/48/000000/facebook-new.png" alt="Facebook"></a>
    <a href="https://www.instagram.com/toto._.p0?igsh=YzljYTk1ODg3Zg==" target="_blank" title="Instagram"><img src="https://img.icons8.com/color/48/000000/instagram-new.png" alt="Instagram"></a>
    <a href="https://www.linkedin.com/in/joel-toto-r/" target="_blank" title="LinkedIn"><img src="https://img.icons8.com/color/48/000000/linkedin.png" alt="LinkedIn"></a>
    <a href="https://github.com/JoelTotoR" target="_blank" title="GitHub"><img src="https://img.icons8.com/color/48/000000/github--v1.png" alt="GitHub"></a>
</div>

