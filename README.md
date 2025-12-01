# 🐧 Trabajo Práctico Final - Administración de Sistemas Linux

![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Apache](https://img.shields.io/badge/Apache-D22128?style=for-the-badge&logo=apache&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

> **Equipo:** Josias Blanco - Rodrigo Arregin  
> **Materia:** Arquitectura y Sistemas Operativos  
> **Fecha de Entrega:** 02/12/2025

---

## 📋 Tabla de Contenidos

- [Introducción](#-introducción)
- [Entorno de Trabajo](#-entorno-de-trabajo)
- [Lo que Aprendimos](#-lo-que-aprendimos)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Desarrollo de Ejercicios](#-desarrollo-de-ejercicios)
  - [Ejercicio 0: Descubriendo la IP](#ejercicio-0-descubriendo-la-ip)
  - [Ejercicio 1: Configuración Inicial](#ejercicio-1-configuración-inicial-y-git)
  - [Ejercicio 2: FastFetch Colaborativo](#ejercicio-2-fastfetch-colaborativo)
  - [Ejercicio 3: Gestión de Permisos](#ejercicio-3-gestión-de-permisos)
  - [Ejercicio 4: LVM en Acción](#ejercicio-4-lvm-en-acción)
  - [Ejercicio 5: Gestión de Archivos](#ejercicio-5-gestión-de-archivos-y-directorios)
  - [Ejercicio 6: Docker y Monitoreo](#ejercicio-6-contenedores-y-monitoreo)
  - [Ejercicio Bonus: Servidor LAMP](#-ejercicio-bonus-servidor-lamp)
- [Desafíos y Soluciones](#-desafíos-y-soluciones)
- [Conclusiones](#-conclusiones)
- [Referencias](#-referencias)

---

## 🎯 Introducción

Este trabajo práctico nos llevó por un recorrido completo de administración de sistemas Linux, desde lo más básico hasta configuraciones avanzadas con contenedores y monitoreo. La idea fue trabajar en equipo, aprender a usar Git de forma colaborativa y entender como funciona de verdad un entorno Linux desde adentro. 

Lo mas interesante del TP fue que no solo se trataba de ejecutar comandos, sino de entender **por qué** estábamos haciendo cada cosa y **cómo** todo se conecta en un sistema real. 

---

## 💻 Entorno de Trabajo

### Configuración Base ⚙️

Para este proyecto utilizamos **VirtualBox** como hipervisor y **Vagrant** para gestionar las máquinas virtuales de forma automatizada.

**Especificaciones de la VM:**
- **Sistema Operativo:** Ubuntu 22.04 LTS (Jammy)
- **Memoria RAM:** 2048 MB
- **CPUs:** 2 cores
- **Disco Adicional:** 2GB para ejercicios de LVM
- **Networking:** Modo Bridge (red pública)

### Herramientas Instaladas 🛠️

El script de instalación de Vagrant nos instaló todas las herramientas necesarias:
- `fastfetch` - Para obtener info del sistema
- `git` - Control de versiones
- `docker.io` y `docker-compose` - Contenedores
- `lvm2` - Gestión de volúmenes lógicos

---

## 📚 Lo que Aprendimos

A través de este trabajo práctico desarrollamos habilidades en:

🤖 **Virtualización y Automatización** 
- Manejo de Vagrant para levantar entornos reproducibles
- Configuración de VMs con instalación automática de herramientas

👥 **Trabajo Colaborativo** 
- Uso de Git para trabajo en equipo (add, commit, push, pull)
- Resolución de conflictos cuando dos personas editan el mismo archivo
- Buenas prácticas de commits y documentación

🐧 **Administración de Linux** 
- Gestión de usuarios, grupos y permisos (chmod, chown)
- Comprensión del sistema de permisos (lectura, escritura, ejecución)
- Manejo de servicios con systemctl

💾 **Almacenamiento Avanzado** 
- Logical Volume Manager (LVM): PV, VG, LV
- Ventajas de LVM sobre particiones tradicionales
- Montaje y configuración de fstab

🐳 **Contenedores y Orquestación** 
- Docker y Docker Compose
- Networking entre contenedores
- Gestión de volúmenes persistentes

📈 **Monitoreo y Observabilidad** 
- Stack de monitoreo con Grafana, Prometheus y Loki
- Configuración de datasources
- Visualización de métricas en tiempo real

🌐 **Servidores Web (Bonus)** 
- Instalación y configuración de LAMP stack
- Apache, MySQL y PHP working together
- Hosting de aplicaciones web

---

## 📁 Estructura del Proyecto

```
practica-linux-blanco-arregin/
│
├── README.md                          # Este archivo 
├── Vagrantfile                        # Configuración de la VM 
│
├── informacion/
│   ├── ip_vm.txt                      # IPs de nuestras VMs 
│   └── system_info.txt                # Salida de fastfetch de ambos 
│
├── permisos/
│   ├── usuarios_arregin.txt           # Info de usuarios y grupos 
│   ├── usuarios_blanco.txt
│   └── verificacion_permisos.txt      # Verificación conjunta 
│
├── lvm/
│   ├── lvm-arregin.txt                # Configuración LVM individual 
│   └── lvm-blanco.txt
│
├── archivos/
│   └── verificacion_archivos.txt      # Operaciones con archivos 
│
├── contenedores/
│   ├── docker-compose.yml             # Configuración corregida 
│   ├── prometheus.yml                 # Config de Prometheus 
│   ├── errores_encontrados.md         # Documentación del debug 
│   ├── logs_completos.txt             # Logs de todos los servicios 
│   ├── verificacion_contenedores.txt  # Estado de contenedores 
│   └── capturas/                      # Screenshots de todo funcionando 
│       ├── docker_ps.png
│       ├── grafana_datasources.png
│       ├── grafana_dashboard.png
│       ├── prometheus_targets.png
│       └── resolucion_errores.png
│
└── lamp/
    ├── verificacion_lamp.txt          # Verificación del servidor 
    └── capturas/                      # Pruebas del stack funcionando 
        ├── index_html.png
        ├── info_php.png
        └── test_db_php.png
```

---

## 🚀 Desarrollo de Ejercicios

### Ejercicio 0: Descubriendo la IP 🔍

**Objetivo:** Identificar la IP de la VM en modo bridge para poder acceder a los servicios web.

Lo primero que hicimos fue conectarnos a la VM con `vagrant ssh` y usar `ip addr show` para ver todas las interfaces de red. La interfaz principal (enp0s8) nos mostró las IPs asignadas por el router: 

- **VM Arregin:** `192.168.1.43` 📍
- **VM Blanco:**  `192.168.1.33` 📍

Estas IPs fueron fundamentales más adelante para acceder a Grafana desde el navegador y al servidor LAMP. 

**Comandos utilizados:**
```bash
ip addr show
ping -c 4 8.8.8.8  # Verificar conectividad 
```

Guardamos las IPs en `informacion/ip_vm.txt` para tenerlas siempre a mano. 

---

### Ejercicio 1: Configuración Inicial y Git 🎬

**Objetivo:** Crear el repositorio compartido y la estructura de carpetas del proyecto.

Creamos un repositorio público en GitHub llamado `practica-linux-blanco-arregin` y lo clonamos en ambas VMs. Luego configuramos nuestros datos personales de Git:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

Después armamos toda la estructura de directorios del proyecto usando `mkdir -p`: 

```bash
mkdir -p informacion permisos lvm archivos contenedores lamp
```

Lo interesante acá fue aprender que `mkdir -p` crea todos los directorios padres si no existen, y no falla si ya existen. Súper útil para scripts. 

**Lección aprendida:** La estructura organizada desde el inicio facilita mucho el trabajo colaborativo. Saber dónde va cada cosa evita conflictos. 

---

### Ejercicio 2: FastFetch Colaborativo 🚀

**Objetivo:** Capturar información del sistema de ambas VMs en un solo archivo.

Este ejercicio nos enseñó la diferencia entre `>` (sobrescribir) y `>>` (agregar). La idea era que ambos agregáramos nuestro `fastfetch` al archivo `informacion/system_info.txt` sin borrar lo del otro. 

**Proceso:**
1. Cada uno ejecutó `fastfetch` en su VM 
2. Usamos `>>` para agregar al archivo en lugar de sobrescribir 
3. Sincronizamos con Git (pull antes de push para evitar conflictos) 

```bash
echo "========== FASTFETCH DE ARREGIN ==========" >> informacion/system_info.txt
fastfetch >> informacion/system_info.txt
echo "" >> informacion/system_info.txt
```

**Resultado:** Un archivo con la info de ambos sistemas de forma legible. 

---

### Ejercicio 3: Gestión de Permisos 🔐

**Objetivo:** Entender el sistema de permisos de Linux y cómo los usuarios y grupos trabajan juntos.

#### Parte Individual 👤

Cada uno creó su propio espacio de trabajo:

```bash
mkdir /home/vagrant/blanco_espacio/
cd /home/vagrant/blanco_espacio/

# Archivo privado - solo yo puedo leer y escribir 
touch privado.txt
chmod 600 privado.txt

# Archivo público - yo leo/escribo, otros solo leen 
touch publico.txt
chmod 644 publico.txt
```
Entonces `644` significa: dueño (rw-), grupo (r--), otros (r--) 

#### Parte Colaborativa 👥

Creamos usuarios de prueba para simular un entorno de trabajo real:

```bash
sudo useradd -m estudiante1
sudo useradd -m estudiante2
sudo useradd -m estudiante3
```

Luego armamos un grupo llamado `equipotrabajo` y agregamos a todos: 

```bash
sudo groupadd equipotrabajo
sudo usermod -a -G equipotrabajo estudiante1
sudo usermod -a -G equipotrabajo estudiante2
sudo usermod -a -G equipotrabajo estudiante3
sudo usermod -a -G equipotrabajo vagrant
```

Finalmente creamos un directorio colaborativo donde todos los miembros del grupo pueden trabajar: 

```bash
sudo mkdir /tmp/colaborativo
sudo chgrp equipotrabajo /tmp/colaborativo
sudo chmod 770 /tmp/colaborativo
```

El `770` significa que el dueño y el grupo tienen permisos completos (rwx), pero otros usuarios no tienen acceso (---). 

**Lo importante:** Este ejercicio nos mostró cómo en un servidor real, múltiples usuarios pueden colaborar de forma segura en los mismos recursos sin comprometer la privacidad de archivos personales. 🛡️

---

### Ejercicio 4: Gestión de LVM 💽

**Objetivo:** Aprender a gestionar almacenamiento con Logical Volume Manager.

LVM es una forma más flexible de manejar discos que las particiones tradicionales. Permite redimensionar volúmenes sin perder datos, crear snapshots, y agregar más discos al vuelo. 

#### Conceptos Básicos 📚

- **Physical Volume (PV):** El disco físico o partición 
- **Volume Group (VG):** Grupo de uno o más PVs 
- **Logical Volume (LV):** Partición lógica dentro del VG 

#### Implementación ⚙️

Cada uno configuró su propio volumen lógico en el disco adicional (`/dev/sdc`):

```bash
# 1. Crear Physical Volume
sudo pvcreate /dev/sdc

# 2. Crear Volume Group
sudo vgcreate vg_datos_blanco /dev/sdc

# 3. Crear Logical Volume de 1.5GB
sudo lvcreate -L 1.5G -n lv_storage_blanco vg_datos_blanco

# 4. Formatear con ext4
sudo mkfs.ext4 /dev/vg_datos_blanco/lv_storage_blanco

# 5. Crear punto de montaje
sudo mkdir /mnt/lvm_storage_blanco

# 6. Montar el volumen
sudo mount /dev/vg_datos_blanco/lv_storage_blanco /mnt/lvm_storage_blanco

# 7. Agregar a fstab para montaje automático
echo "/dev/vg_datos_blanco/lv_storage_blanco /mnt/lvm_storage_blanco ext4 defaults 0 0" | sudo tee -a /etc/fstab
```

#### ¿Por qué LVM es mejor? 🌟

Imaginate que tenés una partición tradicional y se te queda chica. Con LVM podés:
- Agregar otro disco al Volume Group 
- Extender el Logical Volume sin desmontar 
- Todo sin perder datos ni reinstalar nada 

**Verificación:** Usamos `lvscan`, `pvscan` y `vgscan` para ver toda la configuración, y `df -h` para confirmar que el montaje funciona correctamente. ✅

---

### Ejercicio 5: Gestión de Archivos y Directorios 📂

**Objetivo:** Practicar operaciones avanzadas con archivos en el almacenamiento LVM.

Una vez que teníamos el volumen LVM montado, lo usamos para hacer operaciones con archivos. 

#### Estructura Creada 

```
/mnt/lvm_storage_blanco/
├── proyectos/
│   ├── activos/
│   └── archivados/
├── respaldos/
└── temporal/
```

#### Operaciones Realizadas ⚡

1. **Creación de archivos de prueba:** 📝
```bash
cd /mnt/lvm_storage_blanco/temporal/
for i in {01..10}; do
  touch documento_$i.txt
  echo "Contenido del documento $i" > documento_$i.txt
done
```

Este loop creó 10 archivos automáticamente. El `for` en bash es súper útil para tareas repetitivas. 

2. **Distribución de archivos:** 
- Documentos 1-5 → copiados a `proyectos/activos/` 
- Documentos 6-8 → movidos a `proyectos/archivados/` 
- Documentos 9-10 → respaldados en `respaldos/` y eliminados de temporal 

```bash
# Copiar (mantiene original) 
cp documento_01.txt documento_02.txt documento_03.txt documento_04.txt documento_05.txt ../proyectos/activos/

# Mover (elimina original) 
mv documento_06.txt documento_07.txt documento_08.txt ../proyectos/archivados/

# Backup y limpieza 
cp documento_09.txt documento_10.txt ../respaldos/
rm documento_09.txt documento_10.txt
```

**Diferencia clave:** `cp` hace una copia (archivo original se mantiene), `mv` mueve (archivo original desaparece). 💡

La verificación final con `find` nos mostró toda la estructura de archivos y sus ubicaciones. 

---

### Ejercicio 6: Contenedores y Monitoreo 🐳

**Objetivo:** Levantar un stack completo de monitoreo con Docker Compose y aprender a debuggear cuando las cosas no funcionan.

Este fue el ejercicio más complejo y el que más aprendimos. Nos dieron archivos con **errores intencionales** que teníamos que encontrar y corregir. 

#### Stack de Servicios 📦

Levantamos 6 contenedores:
1. **Nginx** - Servidor web 
2. **Redis** - Base de datos en memoria 
3. **PostgreSQL** - Base de datos relacional 
4. **Prometheus** - Recolección de métricas 
5. **Loki** - Agregación de logs 
6. **Grafana** - Visualización 

#### Proceso de Debug 🐛

##### Error #1: Inconsistencia en nombres de redes

![alt text](https://i.imgur.com/ZK5HC3Y.png)

**Problema encontrado:**
```yaml
services:
  nginx:
    networks:
      - monitoring
  redis:
    networks:
      - monitoring-network  # ← Nombre diferente! ⚠️
```

**Cómo lo detectamos:** 
```bash
docker-compose config  # Mostró warnings sobre redes no definidas
docker-compose up -d   # Falló al intentar crear los servicios
```

**Solución:** Unificar todos los servicios bajo la misma red `monitoring`. ✅

##### Error #2: Volúmenes mal declarados

![alt text](https://i.imgur.com/fKBwLMr.png)

**Problema encontrado:**
```yaml
services:
  grafana:
    volumes:
      - grafana-data:/var/lib/grafana  # Usa "grafana-data" 

volumes:
  grafana-storage:  # Pero declara "grafana-storage" 
```

**Cómo lo detectamos:** 
Los logs de Grafana mostraban errores de permisos y el volumen no se creaba correctamente.

**Solución:** Cambiar `grafana-data` por `grafana-storage` en la declaración del servicio. ✅

##### Error #3: Prometheus targets incorrectos

![alt text](https://i.imgur.com/q3rT7LO.png)

**Problema encontrado:** 
En `prometheus.yml` había un job configurado para scrapear métricas de Nginx en el puerto 9113, pero Nginx Alpine no expone métricas por defecto.

**Cómo lo detectamos:** 
```bash
# Accedimos a http://localhost:9090/targets
# El target de Nginx aparecía en rojo (DOWN) 
```

**Solución:** Comentamos ese job ya que Nginx no tiene un exporter configurado. ✅

#### Configuración de Grafana 📊

Una vez que todo estaba corriendo, configuramos los datasources:

1. **Prometheus:** 
   - URL: `http://prometheus:9090`
   - Access: Server (default)

2. **Loki:** 
   - URL: `http://loki:3100`
   - Access: Server (default)

Ambos datasources pasaron el test de conexión sin problemas. ✅

#### Comandos Útiles de Docker 🛠️

Durante el proceso usamos mucho estos comandos:

```bash
# Ver qué está corriendo 
docker ps

# Ver logs de un servicio específico 
docker-compose logs grafana

# Ver logs de todos los servicios 
docker-compose logs

# Reiniciar todo el stack 
docker-compose down && docker-compose up -d

# Validar la sintaxis del docker-compose.yml 
docker-compose config

# Ver las redes 
docker network ls
```

**Acceso a Grafana:** Una vez todo funcionando, pudimos acceder desde el navegador: 
- URL: `http://192.168.1.43:3000` (desde cualquier dispositivo en la red)
- Usuario: `admin` 
- Contraseña: `practica123` 

---

### 🌟 Ejercicio Bonus: Servidor LAMP

**Objetivo:** Implementar un servidor web completo con Linux, Apache, MySQL y PHP.

Este ejercicio fue re interesante porque vimos como todos los componentes trabajan juntos para servir una aplicación web real. 

#### Stack LAMP 📚

- **L**inux -> Ubuntu 22.04 (ya lo teníamos) 
- **A**pache -> Servidor web HTTP 
- **M**ySQL -> Sistema de gestión de bases de datos 
- **P**HP -> Lenguaje de programación del lado del servidor 

#### Instalación 📦

```bash
# Actualizar repositorios 
sudo apt-get update

# Instalar Apache 
sudo apt-get install -y apache2

# Instalar MySQL 
sudo apt-get install -y mysql-server

# Instalar PHP y módulos 
sudo apt-get install -y php libapache2-mod-php php-mysql

# Verificar versiones 
apache2 -v
mysql --version
php -v
```

#### Configuración de MySQL 🗄️

Creamos una base de datos de prueba y un usuario:

```bash
sudo mysql -e "CREATE DATABASE tp_final_db;"
sudo mysql -e "CREATE USER 'alumno'@'localhost' IDENTIFIED BY 'practica123';"
sudo mysql -e "GRANT ALL PRIVILEGES ON tp_final_db.* TO 'alumno'@'localhost';"
sudo mysql -e "FLUSH PRIVILEGES;"
```

#### Configuración de Apache ⚙️

```bash
# Habilitar módulos necesarios 
sudo a2enmod rewrite
sudo a2enmod php8.1

# Iniciar y habilitar servicios 
sudo systemctl start apache2
sudo systemctl enable apache2
sudo systemctl start mysql
sudo systemctl enable mysql
```

#### Archivos Web Creados 📄

1. **index.html** - Página principal con diseño CSS moderno 
   - Gradientes, cards, efectos hover
   - Totalmente responsive

2. **info.php** - Página de información de PHP 
   ```php
   <?php
   phpinfo();
   ?>
   ```
   Esta página muestra toda la configuración de PHP, módulos cargados, variables de entorno, etc.

3. **test_db.php** - Test de conexión a MySQL 🔌
   ```php
   <?php
   $conn = new mysqli("localhost", "alumno", "practica123", "tp_final_db");
   if ($conn->connect_error) {
       die("Conexión fallida: " . $conn->connect_error);
   }
   echo "Conexión exitosa a MySQL";
   ?>
   ```

#### Permisos 🔐

Los archivos web deben pertenecer al usuario de Apache:

```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```

#### Acceso al Servidor 🌐

El servidor quedó accesible desde cualquier dispositivo en la red local:

- **Página principal:** `http://192.168.1.33/` 
- **Info PHP:** `http://192.168.1.33/info.php` 
- **Test DB:** `http://192.168.1.33/test_db.php` 

**Resultado:** Todo funcionando perfectamente. La página principal se ve muy profesional con su diseño degradado púrpura, y las pruebas de PHP y MySQL confirmaron que el stack estaba bien configurado. ✅

---

## 🔧 Desafíos y Soluciones

### Docker Compose No Levantaba ❌

**Problema:** `docker-compose up -d` fallaba con errores de sintaxis.

**Solución:** El comando `docker-compose config` fue clave para validar la sintaxis del YAML antes de intentar levantar los servicios. 

### Prometheus Targets DOWN 🔴

**Problema:** Algunos targets aparecían caídos en Prometheus.

**Solución:** Entender que no todos los servicios exponen métricas por defecto. Nginx necesita un exporter adicional que no instalamos. 

### Permisos en LVM 🔒

**Problema:** Algunos comandos requerían `sudo` y no quedaba claro cuándo usarlo.

**Solución:** Cualquier operación que modifique el sistema o acceda a dispositivos de bloque necesita privilegios root. 

---

## 💡 Conclusiones

Este trabajo práctico fue mucho más que ejecutar comandos. Nos dio una visión real de cómo se administra un sistema Linux en producción: 

### Habilidades Técnicas Adquiridas 🛠️

**Virtualización:** Entender cómo Vagrant simplifica la creación de entornos reproducibles 

**Linux:** Manejo avanzado de permisos, usuarios, grupos y sistemas de archivos 

**LVM:** Gestión flexible de almacenamiento (algo que las particiones tradicionales no permiten) 

**Contenedores:** Docker Compose para manejar múltiples servicios 

**Monitoreo:** Stack completo de monitoreo con Grafana, Prometheus y Loki 

**Web Servers:** Implementación de LAMP stack completo 

### Habilidades Blandas Desarrolladas 

**Trabajo en Equipo:** Git nos obligó a coordinar y comunicarnos constantemente

**Debugging:** Aprender a leer logs, entender errores y buscar soluciones

**Documentación:** La importancia de documentar todo para reproducibilidad

**Pensamiento Crítico:** No solo ejecutar comandos, sino entender el "por qué"

### Reflexión Final 💭

Lo más valioso fue entender cómo todas estas tecnologías se conectan en un sistema real. No son herramientas aisladas, sino componentes que trabajan juntos: 

- Linux como base de todo 
- LVM para gestión flexible de almacenamiento 
- Docker para aislar aplicaciones 
- Prometheus/Grafana para ver qué está pasando 
- Git para coordinar el trabajo en equipo 

Este conocimiento es directamente aplicable al mundo laboral. Cualquier empresa que trabaje con servidores Linux usa estas mismas herramientas y conceptos. 

---

## 🙏 Agradecimientos

Gracias al profe por siempre ensenarnos con esa buena onda que lo caracteriza, sin dudas hizo mucho mas amena la cursada y tambien por este tp, en el que por ejemplo los errores en el ejercicio de Docker nos enseñaron más sobre debugging que cualquier tutorial. 

---

**Equipo:** Josias Blanco y Rodrigo Arregin
**Repositorio:** [practica-linux-blanco-arregin](https://github.com/usuario/practica-linux-blanco-arregin) 
**Fecha:** Diciembre 2025

