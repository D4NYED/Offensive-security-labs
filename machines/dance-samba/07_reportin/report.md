# 🛡️ Security Assessment Report - Dance-Samba

## 📌 Executive Summary

Se ha identificado una cadena de ataque completa que permite a un atacante comprometer el sistema desde acceso inicial hasta privilegios de root.

El acceso inicial se obtiene mediante exposición de información en FTP, seguido de reutilización de credenciales y escalada de privilegios mediante una mala configuración de sudo.

👉 Impacto: **Compromiso total del sistema**

---

## 🎯 Scope

* Máquina objetivo: Dance-Samba
* Servicios analizados: FTP, SMB, SSH
* Tipo de análisis: Pentesting / laboratorio controlado

---

## 🔍 Key Findings

### 1. Exposición de información (FTP)

* Acceso anónimo habilitado
* Filtración de información sensible

👉 Riesgo: Alto

---

### 2. Reutilización de credenciales

* Credenciales débiles reutilizadas en múltiples servicios

👉 Riesgo: Alto

---

### 3. Escalada de privilegios (sudo misconfig)

* Permisos sudo sobre `/usr/bin/file`

👉 Riesgo: Crítico

---

## 🧠 Attack Chain

1. Acceso FTP anónimo
2. Obtención de credenciales
3. Acceso SMB / SSH
4. Enumeración interna
5. Decoding de credenciales
6. Abuso de sudo (`file`)
7. Acceso root

---

## 💥 Impact

* Acceso completo al sistema
* Lectura de archivos sensibles
* Posible persistencia
* Control total del entorno

---

## 🛡️ Recommendations

* Deshabilitar acceso FTP anónimo
* Implementar políticas de contraseñas robustas
* Evitar reutilización de credenciales
* Restringir permisos sudo
* Monitorizar actividad sospechosa
* Aplicar principio de mínimo privilegio

---

## 🚀 Conclusion

Este escenario demuestra cómo múltiples debilidades aparentemente simples pueden encadenarse hasta provocar una comprometida total del sistema.

👉 La seguridad no falla por un único fallo crítico, sino por la acumulación de malas prácticas.
