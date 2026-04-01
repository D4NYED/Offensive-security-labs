# 🎯 Scope Definition - Dance-Samba

## 📌 Objetivo del análisis

Realizar un análisis de seguridad sobre una máquina Linux vulnerable con el objetivo de:

* Identificar vectores de acceso inicial
* Analizar servicios expuestos
* Escalar privilegios hasta root
* Documentar la cadena de ataque

---

## 🧱 Alcance

### Incluido

* Servicios expuestos:

  * FTP
  * SMB
  * SSH

* Enumeración de servicios

* Acceso inicial

* Escalada de privilegios

* Análisis de configuración del sistema

---

### Excluido

* Ataques de denegación de servicio (DoS)
* Fuerza bruta intensiva
* Ingeniería social
* Explotación fuera del entorno del laboratorio

---

## ⚙️ Entorno

* Tipo: laboratorio controlado
* Sistema objetivo: Linux
* Acceso del atacante: red interna

---

## ⚠️ Reglas del engagement

* No modificar configuraciones fuera de lo necesario
* No eliminar evidencias
* Mantener trazabilidad de acciones
* Actuar como atacante controlado (Red Team simulation)

---

## 🧠 Contexto

Este laboratorio simula un escenario real donde múltiples servicios mal configurados permiten a un atacante:

* Obtener acceso inicial
* Reutilizar credenciales
* Escalar privilegios

---

## 🚀 Conclusión

El alcance definido permite centrarse en la explotación controlada del sistema, simulando un escenario real de auditoría de seguridad sin afectar a entornos externos.
