# 🍽️ Restaurante App — Interfaz Grafica con Tkinter

🌟 **Estudiante:** Ramiro Alcoser A.

## 📚 Tema

Fundamentos de interfaces graficas de usuario con Tkinter, aplicados al proyecto restaurante_app.

## 🎯 Objetivo de aprendizaje

Comprender como el proyecto restaurante_app, desarrollado hasta la Semana 12 como una aplicacion de consola, puede incorporar una interfaz grafica sin reemplazar su arquitectura. La GUI se encarga de la presentacion y de los eventos, mientras que los servicios conservan la logica del sistema y el acceso a los datos.

## 🔄 Evolucion del programa

**ANTES**

Usuario -> CLI -> Servicios -> Modelos -> JSON

**AHORA**

Usuario -> GUI -> Eventos -> Servicios -> Modelos -> JSON

Esta version corresponde a la **Semana 13** y parte de una base grafica simplificada: se trabaja unicamente con Producto y Usuario. Las demas entidades y operaciones desarrolladas en semanas anteriores (Bebida, Cliente, Venta, ventas, indices de busqueda, menu de consola, etc.) no se trasladan todavia; se recuperaran e incorporaran a la interfaz grafica de forma progresiva en las siguientes semanas.

## 🗂️ Capas del proyecto

`modelos/`: clases sencillas que representan la informacion del sistema, como usuarios y productos.

Tambien aplican validaciones basicas con `property` para evitar objetos con datos obligatorios vacios.

`servicios/`: clases que contienen la logica de negocio y el acceso a los archivos JSON.

`datos/`: archivos JSON con informacion persistente de ejemplo.

`ui/`: vistas graficas creadas con Tkinter para interactuar con el usuario.

`main.py`: punto de entrada que inicializa los servicios, muestra la primera vista y ejecuta la aplicacion.

## 🧩 Componentes Tkinter utilizados

🪟 `Tk`: crea la ventana principal de la aplicacion.

🏷️ `Label`: muestra textos dentro de la interfaz.

⌨️ `Entry`: permite ingresar datos como usuario y contrasena.

🔘 `Button`: ejecuta una accion cuando el usuario hace clic.

💬 `messagebox`: muestra mensajes emergentes simples.

🎨 `ttk.Style`: permite definir estilos reutilizables para algunos componentes visuales.

## ⚡ Concepto de evento

Usuario hace clic -> Button genera una accion -> command ejecuta un metodo -> el metodo consulta el servicio -> la interfaz muestra el resultado.

En el login, el boton usa `command=self.iniciar_sesion`. Ese metodo obtiene los datos escritos, valida campos vacios y solicita al servicio la verificacion de credenciales.

## ✅ Funcionalidades implementadas

Inicio -> Login -> Validacion -> Interfaz principal -> Cerrar sesion -> Login

- 🔐 **Inicio de sesion (LoginView):** formulario con campos de usuario y contrasena, boton "Iniciar sesion" y mensajes de error visibles cuando los campos estan vacios o las credenciales son incorrectas. La validacion se solicita a `RestauranteServicio`; la vista no valida las credenciales por su cuenta.
- 🏠 **Panel principal (MainView):** barra superior con las opciones **Productos**, **Usuarios** y **Ventas**, y un boton para **Cerrar sesion**.
- 🍔 **Productos:** lista los productos cargados desde `datos/productos.json` (codigo, nombre, categoria y precio), solicitando la informacion a `RestauranteServicio.listar_productos()`.
- 👤 **Usuarios:** lista los usuarios cargados desde `datos/usuarios.json` (identificador, nombre y usuario), solicitando la informacion a `RestauranteServicio.listar_usuarios()`.
- 🧾 **Ventas:** identificada en el menu como funcionalidad pendiente; al seleccionarla se muestra un mensaje indicando que sera incorporada en una proxima semana.
- 📊 **Barra de estado:** muestra en todo momento la cantidad de productos y usuarios cargados.
- 🚪 **Cerrar sesion:** regresa a la pantalla de login dentro de la misma ventana, sin crear una nueva instancia de `Tk`.

La pantalla central cambia su contenido cuando el usuario selecciona una opcion superior. Esto permite visualizar el concepto de evento sin construir todavia formularios ni operaciones CRUD.

## 💾 Persistencia JSON

Los productos y usuarios se cargan desde archivos JSON locales (`datos/productos.json` y `datos/usuarios.json`) al iniciar la aplicacion, a traves de `ArchivoServicio`.

La GUI no reemplaza los servicios ni los modelos. La interfaz solicita operaciones a `RestauranteServicio`, y el servicio trabaja con los modelos y los datos persistidos. Ninguna vista lee los archivos JSON de forma directa.

Los modelos usan constructores tradicionales con `__init__` y validaciones con `property`, de modo que el paso de diccionarios JSON a objetos sea facil de seguir durante la explicacion.

## 🛠️ Requisitos

- 🐍 Python 3.x
- 🪟 Tkinter disponible en la instalacion de Python

No se requieren dependencias externas.

## ▶️ Como ejecutar

Desde la carpeta del proyecto:

```bash
python main.py
```

En Windows, si el comando `python` no esta disponible en la terminal, puede usarse:

```bash
py main.py
```

## 🔑 Credenciales de demostracion

Usuario: `admin`

Contrasena: `1234`

Tambien puede usarse:

Usuario: `caja1`

Contrasena: `abcd`

## ⚠️ Nota educativa sobre autenticacion

La autenticacion de este proyecto es local y simulada. Las contrasenas se guardan en JSON solo para fines pedagogicos. En una aplicacion real, almacenar contrasenas de esta forma no seria apropiado ni seguro.

## 🚀 Proxima evolucion

En las siguientes practicas se recuperaran e incorporaran progresivamente a la interfaz grafica las funcionalidades desarrolladas en la version de consola (Bebida, Cliente, Venta, busquedas por indice, registro, actualizacion y eliminacion de productos y usuarios, ventas y consulta de categorias), construyendo sobre esta misma base de modelos, servicios, ui y main.py.
