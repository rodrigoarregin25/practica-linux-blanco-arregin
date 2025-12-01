# 🐳 Errores de Docker - Registro de Soluciones

---

## ❌ Error 1: Volumen de Grafana no declarado

### 🔴 Error:
```bash
vagrant@linux-practice:~/practica-linux-blanco-arregin/proyecto/contenedores$ docker-compose up -d
ERROR: Named volume "grafana-data:/var/lib/grafana:rw" is used in service "grafana" but no declaration was found in the volumes section.
```

### 🔍 Diagnóstico:
se intenta usar el servicio grafana-data pero se declara al volumen como grafana-storage:

```yaml
 67   grafana:
 68     container_name: grafana-practica
 69     image: grafana/grafana:latest
 70     ports:
 71       - "3000:3000"
 72     environment:
 73       - GF_SECURITY_ADMIN_PASSWORD=practica123
 74       - GF_USERS_ALLOW_SIGN_UP=false
 75     volumes:
 76       - grafana-data:/var/lib/grafana
```

```yaml
 88 volumes:
 89   grafana-storage:
```

### ✅ Solución:
llamar al volumen grafana-data

```yaml
 88 volumes:
 89   grafana-data:
```

---

## ❌ Error 2: Red no definida para Redis

### 🔴 Error:
```bash
vagrant@linux-practice:~/practica-linux-blanco-arregin/proyecto/contenedores$ docker-compose up -d
ERROR: Service "redis" uses an undefined network "monitoring-network"
```

### 🔍 Diagnóstico:
todos los servicios estan bajo la misma red, monitoring, pero a redis se le configuro una red diferente: monitoring-network:

**configuracion de nginx, postgres, prometheus, loki y grafana:**
```yaml
    networks:
      - monitoring
```

**configuracion de redis:**
```yaml
    networks:
      - monitoring-network
```

### ✅ Solución:
cambiar la configuracion de red de redis a "monitoring"

```yaml
  # Servicio 2: Redis - Base de datos en memoria
  redis:
    container_name: redis-practica
    image: redis:alpine
    ports:
      - "6379:6379"
    restart: unless-stopped
    networks:
      - monitoring
```

---

## ❌ Error 3: Data source de Nginx caído en Prometheus

### 🔴 Error:
data sourse de nginx down en prometheus

### 🔍 Diagnóstico:
prometheus esta intentando recolectar metricas de un servicio que no las expone. esto se puede comprobar al ver los puertos en los que nginx esta escuchando y vemos que no aparece el 9113, sino que solo estan los puertos que corresponden al servidor web:

```bash
docker exec nginx-practica netstat -tuln
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.11:46093        0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 :::80                   :::*                    LISTEN
udp        0      0 127.0.0.11:34527        0.0.0.0:*
```

### ✅ Solución:
eliminar el job de nginx en prometheus ya que es imposible que se obtengan las metricas directaemnte de esta imagen

```yaml
  #- job_name: 'nginx'
  #static_configs:
  #- targets: ['nginx:9113'] # ERROR INTENCIONAL: nginx no expone métricas en este puerto por defecto
```

---

