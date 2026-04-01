# 📂 SMB Enumeration Notes

## 📌 Objetivo

Analizar el servicio SMB para identificar:

* Accesos válidos
* Recursos compartidos
* Posibles vectores de acceso lateral

---

## 🔍 Enumeración inicial

Listado de recursos compartidos:

```bash
smbclient -L //target -N
```

👉 Se identifican shares disponibles en el sistema.

---

## 🔐 Acceso con credenciales

Uso de credenciales obtenidas en fase previa:

```bash
smbclient -L //target -U macarena
```

```text
Password: donald
```

👉 Autenticación exitosa.

---

## 📁 Acceso a recursos

Acceso a un recurso compartido:

```bash
smbclient //target/share -U macarena
```

Comandos básicos:

```bash
ls
get file.txt
```

---

## 🧠 Análisis

* El servicio SMB permite autenticación con credenciales reutilizadas
* No existen restricciones adicionales (IP, MFA, etc.)
* Posible exposición de archivos internos

👉 SMB actúa como punto de pivot tras obtener credenciales.

---

## ⚠️ Riesgos identificados

* Reutilización de credenciales
* Acceso a recursos internos
* Falta de segmentación o control de acceso

---

## 🚀 Conclusión

El servicio SMB no presenta una vulnerabilidad directa, pero permite:

* Validar credenciales
* Acceder a recursos compartidos
* Facilitar el movimiento lateral

👉 SMB se convierte en un vector clave dentro de la cadena de ataque.
