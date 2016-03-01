# Open Whisk Hola Mundo (aka Hello World)

Tutorial para probar IBM openWhisk con una accion basica. Para mas informacion recomiendo acceder a la [documentacion oficial](https://new-console.ng.bluemix.net/docs/openwhisk/index.html) en Bluemix.



## Tabla de Contenidos
  - [Instalar Open Whisk CLI](#instalar-open-whisk-cli)
  - [Ejecutar Hola Mundo](#ejecutar-hola-mundo)

### Instalar openWhisk

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

[open_whisk]: http://www.ibm.com/cloud-computing/bluemix/openwhisk/
[cloud_foundry]: https://github.com/cloudfoundry/cli
[sign_up]:https://console.ng.bluemix.net/registration/