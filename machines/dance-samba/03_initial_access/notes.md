# 🎯 Objetivo

Obtener acceso inicial al sistema objetivo

# 📌 Vector identificado

Acceso a recurso SMB con credenciales débiles obtenidas desde FTP

# 🔧 Proceso

1. Acceso FTP anónimo:

* Se descarga archivo `nota.txt`

Contenido:
"I don't know what to do with Macarena, she's obsessed with donald."

2. Análisis:

* Posibles usuarios:

  * macarena
  * donald

3. Ataque de credenciales en SMB:

```bash
crackmapexec smb 172.17.0.2 -u macarena -p donald
```

✔️ Acceso válido

4. Enumeración de shares:

* Share accesible: `macarena`

5. Acceso al share:

```bash
smbclient //172.17.0.2/macarena -U macarena
```

6. Obtención de flag de usuario:

```bash
get user.txt
```

# 📊 Resultado

* Acceso autenticado a SMB
* Lectura de archivos del usuario
* Obtención de user flag

# 🧩 Análisis

* Credenciales débiles basadas en contexto (OSINT interno)
* Reutilización de nombres como passwords
* SMB expuesto sin restricciones fuertes

# 🚀 Siguiente paso

* Escalar acceso a shell interactiva
* Buscar persistencia o pivot (SSH)

