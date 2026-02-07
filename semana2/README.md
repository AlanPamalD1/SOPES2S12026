# Semana 2 - Creación modulo


## Instrucciones para ejecutar el módulo de kernel

0. Instala las herramientas de compilacion
   ```bash
   sudo apt -y install build-essential libncurses-dev bison flex libssl-dev libelf-dev
   ```

2. Abre una terminal y navega al directorio del módulo:
    ```bash
    cd ~/semana2
    ```

3. Compila el módulo usando `make`:
    ```bash
    make
    ```

4. Inserta el módulo en el kernel:
    ```bash
    sudo insmod mouse.ko
    ```

5. Verifica que el módulo esté cargado:
    ```bash
    lsmod | grep mouse
    ```

6. Consulta los mensajes del kernel para ver la salida del módulo:
    ```bash
    dmesg | tail
    ```

    Para mover el mouse, escribe en /proc/mouse_control
    ```bash
    echo "10 10" > /proc/mouse_control
    ```
    Mueve el mouse 10 pixeles en X y 10 pixeles en Y

7. Para remover el módulo:
    ```bash
    sudo rmmod mouse
    ```

8. Limpia los archivos generados:
    ```bash
    make clean
    ```

## ¿Qué hace este módulo?

Este módulo de kernel es un ejemplo básico que, al ser cargado, permite controlar el mouse, escribiendo en **/proc/mouse_control** el dx y dy en formato dos enteros separados por un espacio, ej: "10 10"

---

# Nota

Si el modulo se ejecuta en una maquina virtual es posible que el sistema anfitrion tome el control del mouse por motivos de usabilidad. Para VMware es posible deshabilitar este comportamiento cambiendo los siguientes ajustes:

En el archivo .vmx de la maquina virtual (archivo creado en la carpeta configurada durante la instalación) se abre con editor de texto (ej: bloc de notas) y se debe de agregar la linea al final: **vmmouse.present = "FALSE"**