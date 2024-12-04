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

