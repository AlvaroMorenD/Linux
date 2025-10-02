# 1.- EXPLORANDO EL SERVIDOR LINUX

En este documento veremos los **comandos básicos y esenciales** para aprender y administrar un servidor Linux. 
 
A lo largo del contenido se cubrirán temas como:  

- Identificación del sistema y su versión.  
- Información del kernel, memoria, CPU y discos.  
- Gestión de usuarios, grupos y credenciales.  
- Configuración y comprobación de la red.  
- Herramientas para supervisar el estado del servidor.
  
---

##  Hostname
- `hostname` -> Muestra el nombre del host de tu equipo.  
- `hostname -I` -> Lista las direcciones IP del equipo.  
- `hostname -f` -> Devuelve el nombre (host + dominio).

![host](/img/hostname.png)
   
- `cat /etc/hostname` -> Lee el nombre del host configurado en el archivo de configuración correspondiente.  

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
- `fdisk -l` -> Lista todos los discos y sus particiones, mostrando detalles como sus tamaños, los número de sectores, el tipo de partición y el sistema de archivos empleado.

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

- `cat /etc/group` -> Muestra todos los grupos configurados en el sistema, incluyendo el nombre del grupo, GID y los usuarios que pertenecen a cada grupo.

  ![grupos](/img/grupos2.png)


- `cat /etc/gshadow` -> Contraseñas de grupos.

    ![grupos](/img/grupos3.png)

---

## Información de la red
- `ip a` -> Muestra todas las interfaces de red del sistema, sus direcciones IP, máscara de red, estado de la interfaz UP o DOWN, si la red está configurada estáticamente o dinámicamente, etc...
- `ip r` -> Muestra información sobre la puerta de enlace.

    ![ip](/img/red.png)


- `ping -c 4 <TuPuertaDeEnlace>` -> Envía 4 paquetes a la puerta de enlace de la red para comprobar la conectividad y medir el tiempo de respuesta.  
- `ping -c 4 google.es` -> Envía 4 paquetes a un servidor externo (en este caso a **google.es** para verificar la conectividad a Internet y medir la latencia.


    ![ip](/img/ping.png)

---

## DNS
- `nslookup google.es` -> Consulta el nombre de dominio `google.es` y muestra **qué servidor DNS respondió la consulta** y la **dirección IP** asociada al dominio. Responde el servidor DNS que tu sistema está usando y muestra la IP pública que corresponde al dominio

`nslookup 8.8.8.8` -> Consulta la dirección IP `8.8.8.8` "servidor publico de Google" y muestra información sobre su dominio inverso y propietario.  
   
![DNS](/img/DNS.png)

---

## Configuración de red
- `cat /etc/network/interfaces` -> Configuración de las interfaces de red. En mi caso está configurado por DHCP, pero estáticamente sería introducir manualmente la IP, máscara, puerta de enlace y DNS. Un ejemplo es:

```text
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4
```

![RED](/img/comprobarRed.png)


---

## Configuración de DNS
- `cat /etc/resolv.conf` -> Lista los servidores DNS configurados. En mi caso los de Moviestar

![DNS](/img/configuracionDNS.png)


---

## Reiniciar la red
- `systemctl status networking` -> Muestra el estado del servicio de red, indica si está activo, inactivo o bloqueado.
- `systemctl restart networking` -> Reinicia el servicio para aplicar cambios en posibles configuraciones.

![red](/img/reiniciarRed.png)

---

## Interfaces de red (ifup/ifdown)
- `ifup <TuinterfazDeRed>` -> Activa la interfaz de red especificada.  
- `ifdown <TuinterfazDeRed>` -> Desactiva la interfaz de red especificada.  
- `ifdown <TuinterfazDeRed> && ifup <TuinterfazDeRed>` -> Primero descativa la interfaz de red y después la vuelve a activar

![red](/img/subirybajarRed.png)

