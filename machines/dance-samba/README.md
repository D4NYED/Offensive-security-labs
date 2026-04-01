# 🛡️ Dance-Samba - Security Analysis

🇬🇧 English version below  
🇪🇸 Versión en español más abajo

## 📌 Scenario

A Linux-based target exposes multiple services (FTP, SMB, SSH).
The goal is to identify the attack path, gain access and escalate privileges to root.

---

## 🎯 Objective

* Identify initial access vector
* Analyze privilege escalation path
* Determine system weaknesses

---

## 🧰 Tools Used

* nmap
* smbclient
* ftp
* ssh
* base32 / base64 decoding
* GTFOBins

---

## 🔍 Analysis

### 1. Initial Access

**Description:**
Anonymous FTP access reveals a clue that can be used as credentials.

**Evidence:**

```text
"Macarena está obsesionada con donald"
```

```bash
macarena:donald
```

👉 Credentials reused successfully via SMB.

**Conclusion:**
Weak credential management → **Credential Reuse vulnerability**

---

### 2. Execution

**Description:**
Access to the system is obtained via SSH using discovered credentials.

```bash
ssh macarena@target
```

---

### 3. Persistence

**Description:**
SSH access provides stable persistence on the system.

---

### 4. Internal Enumeration

**Description:**
A file containing encoded data is discovered.

**Evidence:**

```bash
/home/secret/hash
```

Decoding process:

```bash
Base32 → Base64 → supersecurepassword
```

👉 Chained encoding used to hide credentials.

---

### 5. Privilege Escalation

**Description:**
User has sudo permissions over the `file` binary.

**Evidence:**

```bash
sudo -l
```

```bash
(ALL) NOPASSWD: /usr/bin/file
```

**Exploitation:**

```bash
sudo file -f /opt/password.txt
```

**Result:**

```text
root:rooteable2
```

👉 Abuse of allowed binary via GTFOBins.

---

### 6. Data Access

**Description:**
Root access is achieved and sensitive files are accessed.

```bash
su root
```

---

### 7. Trick / Deception

**Description:**
A fake flag is present to mislead the attacker.

```bash
/root/root.txt       → fake
/root/true_root.txt  → real
```

---

## 📁 Key Findings

* Initial access: FTP + credential reuse
* Protocols: FTP, SMB, SSH
* Vulnerability: Weak credentials
* PrivEsc: Sudo misconfiguration (`file`)
* Technique: Chained encoding

---

## 🧠 Attack Chain

1. Anonymous FTP → information disclosure
2. Credential reuse (macarena:donald)
3. SMB access → pivot
4. SSH access → persistence
5. Discovery of encoded credentials
6. Base32 + Base64 decoding
7. Sudo abuse via GTFOBins (`file`)
8. Root access

---

## 🛡️ Mitigation

* Disable anonymous FTP access
* Enforce strong password policies
* Avoid credential reuse
* Restrict sudo permissions
* Monitor abnormal privilege usage
* Validate allowed binaries

---

## 📸 Evidence

### Initial Access

![FTP](evidence/ftp.png)

---

### Enumeration

![Enumeration](evidence/enumeration.png)

---

### Privilege Escalation

![PrivEsc](evidence/privesc.png)

---

## 🚀 Key Takeaway

> This lab highlights how simple weaknesses like credential reuse and poor sudo configurations can lead to full system compromise.
> Proper enumeration and understanding of system context are more critical than complex exploits.
>
> ---
>
> # 🛡️ Dance-Samba - Análisis de Seguridad

## 📌 Escenario

Máquina Linux con múltiples servicios expuestos (FTP, SMB, SSH).
El objetivo es identificar la cadena de ataque, obtener acceso al sistema y escalar privilegios hasta root.

---

## 🎯 Objetivo

* Identificar el vector de acceso inicial
* Analizar la escalada de privilegios
* Determinar debilidades del sistema

---

## 🧰 Herramientas utilizadas

* nmap
* smbclient
* ftp
* ssh
* base32 / base64
* GTFOBins

---

## 🔍 Análisis

### 1. Acceso inicial

**Descripción:**
El servicio FTP permite acceso anónimo y expone una pista útil.

**Evidencia:**

```text
"Macarena está obsesionada con donald"
```

```bash
macarena:donald
```

👉 Las credenciales se reutilizan con éxito en SMB.

**Conclusión:**
Gestión débil de credenciales → **Vulnerabilidad de Credential Reuse**

---

### 2. Ejecución

**Descripción:**
Se obtiene acceso al sistema mediante SSH.

```bash
ssh macarena@target
```

---

### 3. Persistencia

**Descripción:**
El acceso por SSH permite mantener sesión estable en el sistema.

---

### 4. Enumeración interna

**Descripción:**
Se localiza un archivo con información codificada.

**Evidencia:**

```bash
/home/secret/hash
```

Proceso de decodificación:

```bash
Base32 → Base64 → supersecurepassword
```

👉 Uso de encoding encadenado para ocultar credenciales.

---

### 5. Escalada de privilegios

**Descripción:**
El usuario tiene permisos sudo sobre el binario `file`.

**Evidencia:**

```bash
sudo -l
```

```bash
(ALL) NOPASSWD: /usr/bin/file
```

**Explotación:**

```bash
sudo file -f /opt/password.txt
```

**Resultado:**

```text
root:rooteable2
```

👉 Abuso de binarios permitidos → técnica GTFOBins

---

### 6. Acceso a datos

**Descripción:**
Se obtiene acceso como root y se accede a archivos sensibles.

```bash
su root
```

---

### 7. Engaño final

**Descripción:**
Existe una flag falsa para despistar.

```bash
/root/root.txt       → falso
/root/true_root.txt  → real
```

---

## 📁 Hallazgos clave

* Acceso inicial: FTP + reutilización de credenciales
* Servicios: FTP, SMB, SSH
* Vulnerabilidad: credenciales débiles
* Escalada: sudo mal configurado (`file`)
* Técnica: encoding encadenado

---

## 🧠 Cadena de ataque

1. FTP anónimo → fuga de información
2. Reutilización de credenciales (macarena:donald)
3. Acceso SMB
4. Acceso SSH → persistencia
5. Descubrimiento de credencial codificada
6. Decodificación Base32 + Base64
7. Abuso de sudo (`file`)
8. Acceso root

---

## 🛡️ Mitigación

* Deshabilitar FTP anónimo
* Aplicar políticas de contraseñas robustas
* Evitar reutilización de credenciales
* Restringir permisos sudo
* Monitorizar uso de privilegios
* Validar binarios permitidos

---

## 📸 Evidencia

### Acceso inicial

![FTP](evidence/ftp.png)

---

### Enumeración

![Enumeración](evidence/enumeration.png)

---

### Escalada de privilegios

![PrivEsc](evidence/privesc.png)

---

## 🚀 Conclusión

> Este laboratorio demuestra cómo debilidades simples como la reutilización de credenciales y una mala configuración de sudo pueden derivar en una comprometida total del sistema.
> La enumeración y el contexto son más importantes que la explotación compleja.

