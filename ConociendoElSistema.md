# 1.- EXPLORANDO EL SERVIDOR LINUX

En este documento veremos los **comandos básicos y esenciales** para conocer y administrar un servidor Linux.  
Cada apartado explica su función, acompañado de ejemplos y capturas para facilitar la comprensión.  

A lo largo del contenido se cubrirán temas como:  

- Identificación del sistema y su versión.  
- Información del kernel, memoria, CPU y discos.  
- Gestión de usuarios, grupos y permisos.  
- Configuración y comprobación de la red.  
- Herramientas para supervisar el estado del servidor.
  
---

## 1. Nombre del host 
- **Comando:** `hostname`  
  Muestra el nombre del host actual del sistema.  

- **Comando:** `hostname -I`  
  Muestra las direcciones IP asignadas al host.  

- **Comando:** `hostname -f`  
  Muestra el FQDN (Fully Qualified Domain Name), es decir, el nombre de host completo con dominio.  

![host](/img/host.png)

- **Comando:** `hostnamectl set-hostname NuevoNombre`  
  Permite cambiar el nombre del host de forma permanente (requiere cerrar sesión para aplicar).  

- **Comando:** `cat /etc/hostname`  
  Muestra el nombre de host guardado en el archivo de configuración.  

![hostname](/img/hostname.png)

---

## 2. Versión del sistema 🖥️
- **Comando:** `lsb_release -a` → Muestra la distribución de Linux y su versión.  
- **Comando:** `cat /etc/os-release` → Muestra información detallada de la distribución.  
- **Comando:** `cat /etc/debian_version` → Muestra la versión de Debian.  

![sistema](/img/sistema.png)

---

## 3. Versión del núcleo y arquitectura ⚙️🔧
- **Comando:** `uname -a` → Información completa del kernel, arquitectura y compilación.  
- **Comando:** `uname -r` → Muestra únicamente la versión del kernel.  

![nucleo](/img/nucleo.png)

---

## 4. Memoria RAM 🧠💾
- **Comando:** `free` y `free -h`  
  Muestran el uso de la memoria RAM y swap. La opción `-h` lo muestra en formato legible (MB/GB).  

![ram](/img/ram.png)

---

## 5. CPU 🖥️💨
- **Comando:** `lscpu` → Información detallada de la CPU: arquitectura, núcleos, hilos, etc.  
- **Comando:** `nproc` → Número de procesadores lógicos disponibles.  

![cpu](/img/cpu.png)

---

## 6. Discos y particiones 💽
- **Comando:** `lsblk` → Dispositivos de bloque (discos, particiones, etc.) en forma de árbol.  
- **Comando:** `lsblk -f` → Incluye tipo de sistema de archivos, UUID y etiqueta.  
- **Comando:** `fdisk -l` → Lista las particiones y discos detectados.  

![discos](/img/discos.png)

---

## 7. Sistemas montados 📂
- **Comando:** `df -h` → Uso de disco de cada sistema de archivos montado.  
- **Comando:** `df -hT` → Incluye el tipo de sistema de archivos.  

![sistemasMontados](/img/sistemasMontados.png)

---

## 8. Tamaño de carpetas 📁
- **Comando:** `du -h` → Tamaño de todos los archivos y directorios recursivamente.  
- **Comando:** `du -h /home/` → Tamaño de archivos y subdirectorios de `/home`.  
- **Comando:** `du -hs /home` → Tamaño total de `/home`.  
- **Comando:** `du -hs /home/*` → Tamaño de cada subcarpeta dentro de `/home`.  

![tamano](/img/tamano.png)

---

## 9. Usuarios y grupos del sistema 👥🔒
- **Comandos:** `cat /etc/passwd` y `getent passwd` → Lista de usuarios del sistema.  
![passwd](/img/passwd.png)

- **Comandos:** `cat /etc/shadow` y `getent shadow` → Contraseñas encriptadas (requiere root).  
![shadow](/img/shadow.png)

- **Comandos:** `cat /etc/group` y `getent group` → Lista de grupos.  
![group](/img/group.png)

- **Comandos:** `cat /etc/gshadow` y `getent gshadow` → Contraseñas de grupos.  
![gshadow](/img/gshadow.png)

- **Comando:** `cat /etc/nsswitch.conf` → Indica dónde busca el sistema la información de usuarios, grupos, hosts, etc.  
![nsswitch](/img/nsswitch.png)

---

## 10. Información de la red 🌐🌎
- **Comando:** `ip a` → Muestra interfaces de red, direcciones IP y estado.  
![ipa](/img/ipa.png)

- **Comando:** `ip r` → Tabla de rutas y puerta de enlace.  
![ipr](/img/ipr.png)

- **Comando:** `ping -c 4 <PuertaDeEnlace>` → Verifica conectividad con el gateway.  
- **Comando:** `ping -c 4 google.es` → Verifica conectividad a Internet.  

![ping](/img/ping.png)

---

## 11. Comprobar DNS 🔍
- **Comando:** `nslookup google.es` → Servidor DNS que responde y su IP.  
- **Comando:** `nslookup 8.8.8.8` → Información sobre el propietario de la IP.  

![dns](/img/dns.png)

---

## 12. Configuración de la red ⚙️
- **Comando:** `cat /etc/network/interfaces` → Configuración de interfaces de red.  

![configuracion](/img/configuracion.png)

---

## 13. Configuración tradicional de DNS 🌐
- **Comando:** `cat /etc/resolv.conf` → Muestra los servidores DNS configurados.  

![resolv](/img/resolv.png)

---

## 14. Reiniciar la red 🔄
- **Comando:** `systemctl status networking` → Estado del servicio de red.  
- **Comando:** `systemctl restart networking` → Reinicia el servicio aplicando cambios.  

![reiniciarRed](/img/reiniciarRed.png)

---

## 15. Bajar o subir una tarjeta de red 🖧⬆️⬇️
- **Comando:** `ifup eth0` → Activa la interfaz de red.  
- **Comando:** `ifdown eth0` → Desactiva la interfaz de red.  
- **Comando:** `ifdown eth0 && ifup eth0` → Reinicia la interfaz aplicando cambios.  

![bajarYsubirTarjeta](/img/bajarYsubirTarjeta.png)
