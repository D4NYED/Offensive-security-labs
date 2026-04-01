# 📂 FTP Enumeration Notes

## 📌 Objetivo

Analizar el servicio FTP en profundidad para identificar:

* Accesos no autorizados
* Archivos expuestos
* Información sensible

---

## 🔍 Acceso al servicio

```bash
ftp target
```

Acceso permitido como:

```text
anonymous
```

👉 El servidor permite acceso sin autenticación.

---

## 📁 Enumeración de archivos

Listado de contenido:

```bash
ls
```

Archivo relevante encontrado:

```text
"Macarena está obsesionada con donald"
```

---

## 🧠 Análisis

El contenido del archivo sugiere:

* Posible relación entre usuario y contraseña
* Uso de credenciales basadas en contexto humano

👉 Interpretación:

```text
usuario: macarena
password: donald
```

---

## ⚠️ Riesgo identificado

* Exposición de información sensible
* Falta de control de acceso en FTP
* Posible reutilización de credenciales

---

## 🚀 Conclusión

El servicio FTP no solo permite acceso anónimo, sino que expone información crítica que facilita el acceso a otros servicios.

👉 FTP actúa como punto de entrada indirecto.
