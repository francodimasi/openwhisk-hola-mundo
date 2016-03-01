# Open Whisk Hola Mundo (aka Hello World)

Tutorial para probar IBM openWhisk con una accion basica. Para mas informacion recomiendo acceder a la [documentacion oficial](https://new-console.ng.bluemix.net/docs/openwhisk/index.html) en Bluemix.



## Tabla de Contenidos
  - [Instalar Open Whisk CLI](#instalar-open-whisk-cli)
  - [Ejecutar Hola Mundo](#ejecutar-hola-mundo)

### Instalar Open Whisk CLI

Las siguientes instrucciones explican como hacer [fork del proyecto en GitHub](https://github.com/francodimasi/openwhisk-hola-mundo#fork-destination-box), instalar la tool para interactuar con [OpenWhisk][open_whisk] y luego hacer push de una accion basica, Hola Mundo. Para instalar OpenWhisk ejecutamos los siguientes pasos:

  1. [Crear una cuenta][sign_up] en Bluemix o usar una existente. Para acceder a los servicios de Open Whisk quizas debamos esperar unas horas hasta tener acceso.

  2. Ingresar a GitHub y hacer [fork del proyecto en GitHub](https://github.com/francodimasi/openwhisk-hola-mundo#fork-destination-box). Despues debes clonar el Fork a tu carpeta local.
  
  3. Si todavia no esta instalado en tu sistema, debes instalar Python 2.7

  4. Luego de instalar Python debes instalar [pip](https://en.wikipedia.org/wiki/Pip_(package_manager)), un gestor de paquetes que te permitira instalar Open Whisk CLI. Lo instalas de la siguiente manera:

    ```sh
    $ sudo easy_install pip
    ```
  5. Por ultimo debes autenticarte con tus credenciales de Open Whisk provistas por Bluemix.

    ```sh
    $ wsk property set --auth <tu-credencial-de-openwhisk> --namespace <nombre-del-namespace>
    ```

  6. Para testear que este todo correctamente instalado, ejecuta el siguiente comando:

    ```sh
    $ wsk action invoke /whisk.system/samples/echo -p message hola --blocking --result
    ```
    **Respuesta:** La respuesta deberia ser un JSON que contiene la palabra hola dentro de una propiedad message.

### Ejecutar Hola Mundo

Vamos a escribir una funcion simple que soporte algunos parametros para probar la plataforma:

1. Creamos un archivo de JavaScript el cual tendra la funcion main(). Dicha funcion siempre debe ser invocada por convencion. Es el punto de entrada a nuestro codigo. En este caso creamos un file llamado `hola.js`:

    ```js
    function main(params) {
    return {payload: 'Hola, ' + params.nombre};
    }
    ```
2. Creamos una accion con wsk, en este caso la vamos a llamar hola.

    ```sh
    $ wsk action create hola hola.js
    ```
    ```sh
    ok: created action hola
    ```
3. Listamos las acciones creadas:

    ```sh
    $ wsk action list
    ```
    ```sh
    actions
    /<tu-namespace>/hola                                 private
    ```
4. Ejecutamos la accion:

  ```sh
  $ wsk action invoke --blocking hola --param nombre 'Franco'
  ```
  ```sh
  response:
  {
      "result": {
          "payload": "Hola, Franco"
      },
      "status": "success",
      "success": true
  }
  ```

[open_whisk]: https://new-console.ng.bluemix.net/docs/openwhisk/openwhisk_about.html
[cloud_foundry]: https://github.com/cloudfoundry/cli
[sign_up]:https://console.ng.bluemix.net/registration/