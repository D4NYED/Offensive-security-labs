# 💰 Loot Collected

## 📌 Objetivo

Recopilar credenciales, archivos sensibles y artefactos obtenidos tras la explotación del sistema.

---

## 🔐 Credenciales

* `macarena:donald` → acceso inicial (SMB / SSH)
* `root:rooteable2` → escalada de privilegios

👉 Credenciales reutilizables y críticas.

---

## 🏁 Flags

* `user.txt` → ef65ad731de0ebabcb371fa3ad4972f1
* `true_root.txt` → efb6984b9b0eb57451aca3f93c8ce6b7

---

## 📁 Archivos relevantes

* `/home/secret/hash`

  * Contiene credenciales codificadas
  * Base32 + Base64

* `/opt/password.txt`

  * Archivo accesible mediante abuso de sudo
  * Contiene credenciales de root

---

## 🧠 Técnicas utilizadas

* Credential Reuse (SMB / SSH)
* Encoding abuse (Base32 + Base64)
* Privilege Escalation via GTFOBins (`file`)
* Information Disclosure

---

## 💣 Impacto

* Compromiso completo del sistema
* Acceso a credenciales críticas
* Posibilidad de reutilización en otros sistemas
* Exposición de información sensible

---

## 🚀 Conclusión

El loot obtenido demuestra que el atacante no solo consigue acceso, sino también información reutilizable que puede facilitar ataques adicionales o movimiento lateral.

👉 El verdadero riesgo no es el acceso, sino lo que se puede hacer con la información obtenida.
