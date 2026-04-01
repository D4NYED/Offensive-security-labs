# 💣 Dance-Samba — Pentesting Lab (Full Attack Chain)

🇬🇧 English version below  
🇪🇸 Versión en español más abajo


> ⚠️ No exploits. No CVEs. Just bad practices chained together.

---

## 📌 Overview

This lab demonstrates how a system can be fully compromised through:

* Information disclosure
* Credential reuse
* Weak privilege configuration

👉 Result: **Full root compromise without complex exploitation**

---

## ⚔️ Attack Summary

```text
FTP (anonymous) → Information leak
        ↓
Credential reuse (macarena:donald)
        ↓
SMB → Validation
        ↓
SSH → Initial foothold
        ↓
Encoded credentials discovery
        ↓
Base32 + Base64 decoding
        ↓
Sudo misconfiguration (file)
        ↓
ROOT
```

---

## 🎯 Key Skills Demonstrated

* Service enumeration (FTP, SMB, SSH)
* Credential analysis & reuse
* Encoding identification & decoding
* Privilege escalation via GTFOBins
* Attack chain reasoning

---

## 🔍 Key Weaknesses

* Anonymous FTP exposing sensitive information
* Weak and predictable credentials
* Credential reuse across services
* Misconfigured sudo permissions
* Lack of execution restrictions

---

## 💣 Impact

* Full system compromise
* Access to sensitive files
* Credential disclosure
* Potential lateral movement

---

## 🧠 Why This Matters

> Real-world attacks rarely rely on 0days.

This lab shows that:

* Enumeration is more valuable than exploitation
* Context beats tooling
* Misconfigurations are often enough

---

## 📁 Project Structure

```text
00_scope/                 → Scope definition
01_recon/                 → Service discovery
02_enum/                  → Service enumeration
03_initial_access/        → Initial foothold
04_privilege_escalation/  → Root escalation
05_post_exploitation/     → Impact validation
06_loot/                  → Extracted data
07_reporting/             → Security report
99_summary/               → Attack overview
99_lessons_learned/       → Key insights
```

---

## 📸 Evidence

| Phase                | Description               |
| -------------------- | ------------------------- |
| Recon                | Service discovery         |
| Enumeration          | Credential identification |
| Privilege Escalation | Sudo abuse                |

---

## 🚀 Key Takeaway

> You don’t need advanced exploits to break a system.
> You need visibility, context, and the ability to connect the dots.

---

---

# 🛡️ Dance-Samba — Análisis de Seguridad

> ⚠️ Sin exploits complejos. Solo malas prácticas encadenadas.

---

## 📌 Resumen

Este laboratorio demuestra cómo un sistema puede ser comprometido completamente mediante:

* Exposición de información
* Reutilización de credenciales
* Mala configuración de privilegios

👉 Resultado: **Compromiso total del sistema (root)**

---

## ⚔️ Cadena de ataque

```text
FTP anónimo → fuga de información
        ↓
Reutilización de credenciales
        ↓
SMB → validación
        ↓
SSH → acceso inicial
        ↓
Credenciales codificadas
        ↓
Decoding Base32 + Base64
        ↓
Sudo mal configurado (file)
        ↓
ROOT
```

---

## 🎯 Habilidades demostradas

* Enumeración de servicios
* Análisis de credenciales
* Interpretación de encoding
* Escalada de privilegios (GTFOBins)
* Pensamiento ofensivo

---

## 🔍 Debilidades clave

* FTP anónimo
* Contraseñas débiles
* Reutilización de credenciales
* Sudo mal configurado
* Falta de controles básicos

---

## 💣 Impacto

* Compromiso completo del sistema
* Acceso a datos sensibles
* Posible movimiento lateral
* Exposición de credenciales

---

## 🧠 Por qué importa

> La mayoría de ataques reales no usan exploits complejos.

Este lab demuestra que:

* Enumerar bien > explotar
* El contexto es clave
* Las malas configuraciones son suficientes

---

## 🚀 Conclusión

> No hace falta romper el sistema.
> Muchas veces, el sistema ya está roto.


