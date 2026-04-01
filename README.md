# Unidad-2-Componentes-Definidos-por-el-Usuario-en-Flet

El código presentado corresponde al tema de creación de componentes definidos por el usuario, ya que se implementa un componente personalizado llamado tarjetaperfil, el cual hereda de un contenedor de la librería Flet.

Este componente encapsula tanto la estructura visual como el comportamiento, ya que incluye elementos como textos organizados en una columna, estilos personalizados (bordes, tamaño y espaciado) y un evento de interacción mediante el método on_click.

Además, el componente es reutilizable, ya que puede instanciarse múltiples veces con diferentes datos, como se muestra en la creación de varios usuarios. Esto permite mejorar la organización del código, reducir la repetición y facilitar el mantenimiento de la aplicación.

Acontinuación su explicación:

libreria
-

Se utiliza la libreria de flet, que nos permite crear interfaces graficas en python.
```python
import flet as ft
```

Creacion del componente personalizado
-

En una clase llamada tarjetaperfil es la que hereda del ft.container, es decir aqui estamos creando un componente visual definido por el usuario.
```python
class tarjetaperfil(ft.Container):
```

Creacion del componete
-

Se define el init que inicializa el componete y este recibira los datos(nombre,rol,color_border), lo que permitira reutilizar el componente con diferentes datos.
```python
def __init__(self, nombre,rol, color_border=ft.Colors.BLUE):
        super().__init__()
```

Contenido del componete
-

Aqui se define lo que veremos dentro del componete, que es el nombre, rol,y estos se organizaran dentro de una columna.
```python
self.content = ft.Column(
            controls=[
                ft.Text(nombre, size=20, weight=ft.FontWeight.BOLD),
                ft.Text(rol, italic= True),
            ],
            tight=True
        )
```

Estilo visual del componente
-

Aqui definimos su diseño como:

- borde con color -> ```self.border = ft.border.all(2,color_border)```
- espaciado interno -> ```self.padding = 10```
- bordes redondeados -> ```  self.border_radius = 10```
- tamaño ->  ```self.width = 200```
- tambien se asigna un evento al componente, es decir cuando se de clic, se ejecutara la funcion saludar -> ```self.on_click = self.saludar```

Metodo del evento
-

En este metodo se recibe el evento (e) y se mostrara en la consola el nombre del usuario.
Es decir cuando demos clic al componente se ejecutara este metodo y lo mostrara en pantalla.

```python
def saludar(self, e):
        print(f"Interactuando con el componente de {self.content.controls[0].value}")
```

Funcion pricipal y Configuracion de la interfaz
-

Con esta funcion se crea la ventana principal de la aplicacion.
```python
def main(page: ft.Page):
```
se crea el titulo de la ventana unidad 2 componentes definidos por el usuario y la alinacion de los elementos.
```python
page.title = "unidad 2: componentes definidos por el usuario"
page.horizontal_alignment = ft.CrossAxisAlignment.CENTER
```    

Creación de instancias del componente
-

Aqui se crean los componentes que se reutilizaran, es decir se crean dos componentes pero con diferentes datos.
```python
usuario1 = tarjetaperfil("Ana Garcia", "Desarrolladora senior", ft.Colors.GREEN)
usuario2 = tarjetaperfil("Carlos Ruiz", "Arquitecto de software")
```

Mostrar en pantalla
-

Aqui se agrega el titulo lista de usuarios y se usa un row que es un contenedor que es para mostrar los componentes.
```python
page.add(
        ft.Text("lista de usuarios", size=30, weight="bold"),
        ft.Row([usuario1,usuario2],alignment=ft.MainAxisAlignment.CENTER)
    )
```
Ejecución de la app
-

con esto inicia la aplicacion.
```python
ft.app(target=main)
```

A continuacion se muestra el codigo completo:

```python
import flet as ft
# definicion del componete personalizado
class tarjetaperfil(ft.Container):
    def __init__(self, nombre,rol, color_border=ft.Colors.BLUE):
        super().__init__()
        self.content = ft.Column(
            controls=[
                ft.Text(nombre, size=20, weight=ft.FontWeight.BOLD),
                ft.Text(rol, italic= True),
            ],
            tight=True
        )
        self.border = ft.border.all(2,color_border)
        self.padding = 10
        self.border_radius = 10
        self.width = 200
        self.on_click = self.saludar

    def saludar(self, e):
        print(f"Interactuando con el componente de {self.content.controls[0].value}")
def main(page: ft.Page):
    page.title = "unidad 2: componentes definidos por el usuario"
    page.horizontal_alignment = ft.CrossAxisAlignment.CENTER
    
    #instanciando nuestros componetes personalizados
    usuario1 = tarjetaperfil("Ana Garcia", "Desarrolladora senior", ft.Colors.GREEN)
    usuario2 = tarjetaperfil("Carlos Ruiz", "Arquitecto de software")

    page.add(
        ft.Text("lista de usuarios", size=30, weight="bold"),
        ft.Row([usuario1,usuario2],alignment=ft.MainAxisAlignment.CENTER)
    )

ft.app(target=main)
```

Acontinuacion se muestra la ejecucion:

<img width="1575" height="558" alt="image" src="https://github.com/user-attachments/assets/11044386-3113-4b25-b90a-c4f5dcc3f051" />

<img width="851" height="915" alt="image" src="https://github.com/user-attachments/assets/7672405f-b25f-40b8-8526-fbd5659636a9" />

cuado damos clic se muestra la accion en la consola:

<img width="575" height="173" alt="image" src="https://github.com/user-attachments/assets/1fd6ea13-906a-48aa-843b-88c31835c11f" />

