# Instalación de Docker y Docker Compose en Ubuntu 

Aquí encontrarás la guía paso a paso para dejar listo tu servidor con el motor de Docker y el plugin de Compose, ideal para desplegar herramientas como n8n.

---

# 🐳 Instalación de Docker en Ubuntu Server

En este repositorio se detallan los comandos oficiales para instalar Docker Engine y Docker Compose de manera correcta, evitando versiones desactualizadas de los repositorios comunes.
``
---

## 📹 Video Tutorial

Si prefieres seguir el proceso visualmente, puedes ver el tutorial completo aquí:
[Ver video en YouTube](https://youtu.be/mIkkz34a6Hg)

---

## 🛠️ Pasos de Instalación

### 1. Actualizar el sistema y preparar dependencias
Primero, actualizamos los paquetes actuales e instalamos las herramientas necesarias para manejar repositorios vía HTTPS.

```bash
sudo apt update && sudo apt install -y ca-certificates curl gnupg lsb-release
```

### 2. Agregar la llave GPG oficial de Docker
Esto sirve para validar que los paquetes que vamos a instalar son firmados por Docker.

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL [https://download.docker.com/linux/ubuntu/gpg](https://download.docker.com/linux/ubuntu/gpg) | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

### 3. Configurar el repositorio oficial
Añadimos el repositorio de Docker a nuestra lista de fuentes de Ubuntu.
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

###  4. Instalar Docker Engine y Docker Compose
Actualizamos nuevamente e instalamos el motor de Docker junto con el plugin de Compose
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### 5. Configurar permisos de usuario (Opcional)
Ejecuta este comando para poder usar Docker sin tener que escribir sudo en cada instrucción.
```bash
sudo usermod -aG docker $USER
```

### Nota: Es necesario cerrar sesión y volver a entrar para que este cambio se aplique.


### ✅ Verificación de la instalación
Para comprobar que todo quedó instalado correctamente, ejecuta los siguientes comandos:
```bash
docker --version
docker compose version
```


