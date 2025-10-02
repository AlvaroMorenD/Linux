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

## 🔖 Hostname
- `hostname` -> Muestra el nombre actual del host.  
- `hostname -I` -> Lista las direcciones IP asignadas al equipo.  
- `hostname -f` -> Devuelve el nombre FQDN (host + dominio).

![host](/img/host.png)
   
- `cat /etc/hostname` -> Lee el nombre del host almacenado en el archivo de configuración.  

---

## 🖥️ Versión del sistema
- `lsb_release -a` -> Muestra la distribución de Linux y su versión.  
- `cat /etc/os-release` -> Muestra información detallada de la distribución instalada.  
- `cat /etc/debian_version` -> Muestra la versión exacta de Debian.  

---

## ⚙️ Núcleo y arquitectura
- `uname -a` -> Información completa: kernel, compilación, arquitectura.  
- `uname -r` -> Solo muestra la versión del kernel.  

---

## 🧠 Memoria RAM
- `free` -> Muestra el uso de la memoria RAM y SWAP.  
- `free -h` -> Igual que el anterior, pero en formato legible (MB, GB).  

---

## 💨 CPU
- `lscpu` -> Información detallada de la CPU: arquitectura, núcleos, hilos, etc.  
- `nproc` -> Número de procesadores lógicos disponibles.  

---

## 💽 Discos y particiones
- `lsblk` -> Lista los discos y particiones en formato de árbol.  
- `lsblk -f` -> Incluye tipo de sistema de archivos, etiquetas y UUID.  
- `fdisk -l` -> Muestra particiones, sectores y tamaños de discos detectados.  

---

## 📂 Sistemas montados
- `df -h` -> Uso de disco por sistema de archivos (formato legible).  
- `df -hT` -> Igual que el anterior, pero incluye el tipo de sistema de archivos.  

---

## 📁 Tamaño de carpetas
- `du -h` -> Tamaño de todos los archivos y carpetas recursivamente.  
- `du -h /home/` -> Tamaño de todos los subdirectorios en `/home`.  
- `du -hs /home` -> Tamaño total de la carpeta `/home`.  
- `du -hs /home/*` -> Tamaño individual de cada subcarpeta dentro de `/home`.  

---

## 👥 Usuarios y grupos
- `cat /etc/passwd` / `getent passwd` -> Lista de usuarios del sistema.  
- `cat /etc/shadow` / `getent shadow` -> Contraseñas encriptadas (requiere root).  
- `cat /etc/group` / `getent group` -> Lista de grupos configurados.  
- `cat /etc/gshadow` / `getent gshadow` -> Contraseñas de grupos.  
- `cat /etc/nsswitch.conf` -> Define dónde busca la información (archivos locales, DNS, etc.).  

---

## 🌐 Información de la red
- `ip a` -> Lista interfaces de red, direcciones IP y su estado (UP/DOWN).  
- `ip r` -> Muestra la tabla de enrutamiento y la puerta de enlace por defecto.  
- `ping -c 4 <PuertaDeEnlace>` -> Verifica conectividad con el gateway.  
- `ping -c 4 google.es` -> Verifica conectividad a Internet.  

---

## 🔍 DNS
- `nslookup google.es` -> Muestra qué DNS responde y su dirección IP.  
- `nslookup 8.8.8.8` -> Muestra información sobre el propietario de la IP.  

---

## ⚙️ Configuración de red
- `cat /etc/network/interfaces` -> Configuración de interfaces de red.  

---

## 🌐 Configuración de DNS
- `cat /etc/resolv.conf` -> Lista los servidores DNS configurados.  

---

## 🔄 Reiniciar la red
- `systemctl status networking` -> Estado actual del servicio de red.  
- `systemctl restart networking` -> Reinicia el servicio para aplicar cambios.  

---

## 🖧 Interfaces de red (ifup/ifdown)
- `ifup eth0` -> Activa la interfaz de red `eth0`.  
- `ifdown eth0` -> Desactiva la interfaz de red `eth0`.  
- `ifdown eth0 && ifup eth0` -> Reinicia la interfaz aplicando configuración nueva.  
