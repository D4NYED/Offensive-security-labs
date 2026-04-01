# 🧠 Lessons Learned

## 📌 Objetivo

Extraer aprendizajes clave del laboratorio más allá de la ejecución técnica.

---

## 🔍 1. Enumeración > Explotación

El acceso inicial no se consiguió mediante vulnerabilidades complejas, sino mediante:

* exposición de información
* interpretación de contexto

👉 La enumeración fue el punto crítico del ataque.

---

## 🔐 2. Las credenciales siguen siendo el eslabón más débil

* Uso de nombres propios como contraseña
* Reutilización entre servicios (FTP → SMB → SSH)

👉 No es un fallo técnico, es un fallo humano.

---

## 🧩 3. No todo “hash” es un hash

El archivo encontrado no era un hash real, sino encoding encadenado:

* Base32
* Base64

👉 La interpretación correcta es más importante que la fuerza bruta.

---

## ⚙️ 4. Sudo mal configurado rompe el sistema

Permitir binarios aparentemente inofensivos puede derivar en:

* lectura de archivos sensibles
* obtención de credenciales
* escalada completa

👉 No solo importan los binarios, sino cómo se usan.

---

## 🧠 5. Pensar como atacante es clave

El ataque no sigue un camino lineal:

* pistas → hipótesis → validación
* prueba-error constante

👉 La mentalidad importa más que las herramientas.

---

## 💣 6. El impacto no está en el acceso, sino en el abuso

Ser root no es el objetivo final, sino el punto de partida para:

* persistencia
* exfiltración
* movimiento lateral

👉 El verdadero riesgo empieza después del acceso.

---

## 🚀 Conclusión

> La mayoría de los compromisos no ocurren por vulnerabilidades avanzadas, sino por malas prácticas encadenadas.

👉 Enumerar bien, interpretar mejor y explotar lo simple sigue siendo la clave.
