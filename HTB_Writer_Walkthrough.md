# HTB - Appointment 🩺

## 📌 Objetivo

Explotar la máquina "Appointment" de Hack The Box utilizando técnicas de reconocimiento, enumeración y SQL Injection para obtener la flag.

---

## 🔍 1. Enumeración con Nmap

Ejecutamos un escaneo básico con scripts NSE y detección de versiones:

```bash
sudo nmap -sC -sV <IP_target>
```

**Resultado:**
- Puerto 80 abierto
- Servicio: HTTP (Apache 2.4.38)

![Nmap Scan](imagenes/nmap_scan.png)

---

## 🌐 2. Navegación al servicio web

Accedemos al servicio HTTP navegando a la IP objetivo desde el navegador. Se muestra una interfaz web simple, lo que sugiere posible vector de ataque por inyección web.

---

## 🗂️ 3. Fuerza bruta de directorios con Gobuster

Se ejecuta Gobuster para descubrir directorios ocultos o sensibles:

```bash
gobuster dir -u http://<IP_target> -w /usr/share/wordlists/dirb/common.txt
```

**Resultado:**
No se descubren directorios útiles. El ataque no da información relevante.

![Gobuster](imagenes/gobuster_result.png)

---

## 🛡️ 4. Explotación con SQL Injection

Dado que el puerto 80 sirve una aplicación web, se prueba una **inyección SQL clásica**:

- Usuario: `admin'#`
- Contraseña: `abc123` (el valor es irrelevante)

Explicación:
- `'` cierra la cadena SQL
- `#` convierte el resto de la línea en comentario (en MySQL/PHP)

Esto permite el **bypass de autenticación**, accediendo como usuario administrador.

![SQLi login](imagenes/sqli_login.png)

---

## 🏁 5. Obtención de la flag

Una vez dentro del sistema, la flag se muestra o se puede encontrar fácilmente tras la autenticación exitosa.

```bash
cat /root/root.txt
```

![Flag obtenida](imagenes/flag.png)

---

## ✅ Conclusiones

- Enumeración con `nmap` y `gobuster` nos dio visibilidad inicial.
- La web era vulnerable a SQL Injection básica.
- Con una sola inyección fue posible acceder como administrador y capturar la flag.
- La importancia de validar y filtrar entradas del usuario queda demostrada.

---

**Autor**: [Tu Nombre o Alias]  
**HTB Username**: [Tu usuario en Hack The Box]  
