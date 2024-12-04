# PC5

## Ejercicio 1: Configuración básica del sistema

```bash
PS C:\Users\user\Desktop\PC5 - KevinCondor> vagrant provision
==> default: Running provisioner: ansible_local...
    default: Running ansible-playbook...

PLAY [Configuracion VM - PC5] **************************************************

TASK [Gathering Facts] *********************************************************
ok: [default]

TASK [Actualizar los paquetes del sistema] *************************************
changed: [default]

TASK [Configurar la zona horaria y locales] ************************************
changed: [default]

TASK [Crear un grupo llamado admin] ********************************************
ok: [default]

TASK [Crear un usuario devuser perteneciente al grupo admin con contraseña cifrada] ***
changed: [default]

PLAY RECAP *********************************************************************
default                    : ok=5    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```
    
## Ejercicio 2: Implementación de servicios web con seguridad básica

```bash
TASK [Instalar Nginx] **********************************************************
changed: [default]

TASK [Generar certificados SSL autofirmados] ***********************************
changed: [default]

TASK [Configurar Nginx para utilizar SSL] **************************************
changed: [default]

TASK [Permitir tráfico en el puerto 443 (HTTPS)] *******************************
changed: [default]

TASK [Activar UFW] *************************************************************
changed: [default]

PLAY RECAP *********************************************************************
default                    : ok=10   changed=8    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

## Ejercicio 3: Despliegue de aplicación web con balanceador de carga

```bash
TASK [Instalar dependencias de Python] *****************************************
changed: [default]

TASK [Instalar Flask y Gunicorn] ***********************************************
changed: [default]

TASK [Crear directorio de la aplicación] ***************************************
changed: [default]

TASK [Copiar la aplicación Flask] **********************************************
changed: [default] => (item=files/greeting.py)
changed: [default] => (item=files/wsgi.py)

PLAY RECAP *********************************************************************
default                    : ok=14   changed=12   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

Se presentó el problema que al querer al aplicar las correcciones/cambios con el comando `vagrant provision` aparecía el siguiente error:

```bash
PS C:\Users\user\Desktop\PC5 - KevinCondor> vagrant provision
==> default: Running provisioner: ansible_local...
An error occurred in the underlying SSH library that Vagrant uses.
The error message is shown below. In many cases, errors from this
library are caused by ssh-agent issues. Try disabling your SSH
agent or removing some keys and try again.

If the problem persists, please report a bug to the net-ssh project.

timeout during server version negotiating
```
Se probro con deshabilitar temporalmente ssh, reinstalar vagrant y virtualbox pero el problema persistió dificultando el desarrollo fluido, ya que la única 'solución' que funcionaba era aplicar `vagrant destroy & vagrant up` pero este hacía que solo el proceso de levantar la vm demore alrededor de 20 min a más por cada vez que se quería probar los cambios.