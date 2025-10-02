# 1.- EXPLORANDO EL SERVIDOR LINUX

En este documento veremos los **comandos básicos y esenciales** para conocer y administrar un servidor Linux.  
Cada apartado explica su función, acompañado de ejemplos y capturas.  

A lo largo del contenido se cubrirán temas como:  

- Identificación del sistema y su versión.  
- Información del kernel, memoria, CPU y discos.  
- Gestión de usuarios, grupos y permisos.  
- Configuración y comprobación de la red.  
- Herramientas para supervisar el estado del servidor.
  
---

##  Hostname
- `hostname` -> Muestra el nombre actual del host.  
- `hostname -I` -> Lista las direcciones IP del equipo.  
- `hostname -f` -> Devuelve el nombre (host + dominio).

![host](/img/hostname.png)
   
- `cat /etc/hostname` -> Lee el nombre del host almacenado en el archivo de configuración.  

![host](/img/hostname2.png)

- `hostnamectl set-hostname <Nombre>` -> Cambia el nombre del host.

![host](/img/host3.png)


---

##  Versión del sistema
- `lsb_release -a` -> Muestra la versión de Linux instalada.
- `cat /etc/os-release` -> Da información sobre la distribución instalada.
  
  ![Sistema](/img/VersionSistema.png)

- `cat /etc/debian_version` -> Muestra la versión de Debian instalada en el sistema.  

---

##  Núcleo y arquitectura
- `uname -a` -> Muestra información detallada del sistema: nombre del kernel, versión exacta, fecha de compilación, arquitectura del procesador y nombre del host.
   
- `uname -r` ->  Muestra la versión del kernel.

   ![Sistema](/img/VersionNucleo.png)


---

## Memoria RAM
- `free` -> Muestra el uso, el espacio, la compartida y la caché y la total de la memoria RAM y SWAP.  
- `free -h` -> Igual que el anterior, pero en formato más entendible para el usuario.
  
   ![RAM](/img/RAM.png)

---

## CPU
- `lscpu` -> Muestra información de tu CPU, en concreto: arquitectura, número de núcleos, hilos, velocidad de reloj, tamaño de caché y otras características del procesador.
  
   ![CPU](/img/cpu.png)
  
- `nproc` -> Da el número de procesadores lógicos de tu procesador.

   ![CPU](/img/cpu2.png)


---

## Discos y particiones
- `lsblk` -> Lista los discos y particiones en formato de árbol.  
- `lsblk -f` -> Muestra los dispositivos de bloque (discos y particiones) incluyendo su sistema de archivos, etiquetas, UUID y punto de montaje.
- `fdisk -l` -> Lista todos los discos y sus particiones, mostrando detalles como tamaños, número de sectores, tipo de partición y sistema de archivos.

     ![CPU](/img/discos.png)


---

## Sistemas montados
- `df -h` -> Uso de disco por sistema de archivos (formato legible).  
- `df -hT` -> Igual que el anterior, pero añade el tipo de sistema de archivos.
      ![Montados](/img/SistemasMontados.png)


---

## Tamaño de una carpeta
- `du -h` -> Tamaño de todos los archivos y carpetas recursivamente.  
- `du -h /home/` -> Tamaño de todos los subdirectorios en /home.  
- `du -hs /home` -> Tamaño total de la carpeta /home.  
- `du -hs /home/*` -> Tamaño individual de cada subcarpeta dentro de /home.

![Carpeta](/img/Tamaño.png)


---

## Usuarios y grupos
- `cat /etc/passwd` -> Muestra la lista de todos los usuarios del sistema junto con información adicional como UID, GID, directorio home y shell predeterminado.

![Usuarios](/img/usuarios.png)


- `cat /etc/shadow` -> Contraseñas encriptadas de los usuarios del sistema

![grupos](/img/grupos.png)

- `cat /etc/group` -> Lista de grupos configurados.

  ![grupos](/img/grupos2.png)


- `cat /etc/gshadow` / `getent gshadow` -> Contraseñas de grupos.

    ![grupos](/img/grupos3.png)

- `cat /etc/nsswitch.conf` -> Define dónde busca la información (archivos locales, DNS, etc.).  

---

## Información de la red
- `ip a` -> Lista interfaces de red, direcciones IP y su estado (UP/DOWN).  
- `ip r` -> Muestra la tabla de enrutamiento y la puerta de enlace por defecto.  
- `ping -c 4 <PuertaDeEnlace>` -> Verifica conectividad con el gateway.  
- `ping -c 4 google.es` -> Verifica conectividad a Internet.  

---

## DNS
- `nslookup google.es` -> Muestra qué DNS responde y su dirección IP.  
- `nslookup 8.8.8.8` -> Muestra información sobre el propietario de la IP.  

---

## Configuración de red
- `cat /etc/network/interfaces` -> Configuración de interfaces de red.  

---

## Configuración de DNS
- `cat /etc/resolv.conf` -> Lista los servidores DNS configurados.  

---

## Reiniciar la red
- `systemctl status networking` -> Estado actual del servicio de red.  
- `systemctl restart networking` -> Reinicia el servicio para aplicar cambios.  

---

## Interfaces de red (ifup/ifdown)
- `ifup eth0` -> Activa la interfaz de red `eth0`.  
- `ifdown eth0` -> Desactiva la interfaz de red `eth0`.  
- `ifdown eth0 && ifup eth0` -> Reinicia la interfaz aplicando configuración nueva.  
