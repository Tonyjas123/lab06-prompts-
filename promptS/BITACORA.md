# Bitacora de prompts 
  
Laboratorio 06: Fundamentos de Ingenieria de Prompts. 
  
Herramienta de IA usada: (escribe aqui cual usaste) 
  
## Ejercicio 2: Tokens y ventana de contexto 
  
## Ejercicio 3: Temperatura 
  
## Ejercicio 4: Prompt vago vs estructurado 
  
## Ejercicio 5: Anatomia de un prompt 
  
## Ejercicio 6: Del prompt basico al profesional 


| Texto | Caracteres | Tokens |
|-------|------------|--------|
| Los estudiantes programan en Java. | 35 | 8 |
| The students program in Java. | 29 | 6 |
| desafortunadamente | 18 | 2 |

### Observaciones sobre la ventana de contexto
Al preguntar dentro del mismo chat, la IA respondió correctamente ("TiendaTec" y "Java Swing") porque la información quedó guardada dentro de su ventana de contexto activa. Sin embargo, al abrir un chat nuevo, la IA no supo la respuesta porque la ventana de contexto inicia completamente vacía y no conserva el historial del chat anterior.

## Ejercicio 3: Temperatura

| Temperatura | % de BiblioTec | Nombres en los 5 intentos |
|-------------|----------------|---------------------------|
| 0 | 100.0% | BiblioTec, BiblioTec, BiblioTec, BiblioTec, BiblioTec |
| 0.5 | 69.9% | BiblioTec, BiblioTec, LibroYa, BiblioTec, PrestaLibro |
| 1 | 38.3% | BiblioTec, PrestaLibro, LibroYa, LectoGo, BiblioTec |
| 1.8 | 32.1% | LectoGo, NubeDeTinta, LibroYa, PrestaLibro, BiblioTec |

### Observaciones
Al aumentar la temperatura, los porcentajes de probabilidad se distribuyen entre más opciones, haciendo que los nombres elegidos sean más variados y menos predecibles en cada intento.

El simulador nunca inventa un nombre nuevo porque la temperatura solo cambia la probabilidad de selección entre las opciones preexistentes; no agrega ni genera conocimiento nuevo que no esté previamente definido en el modelo.
## Ejercicio 4: Prompt vago vs prompt estructurado

| Criterio | Prompt vago | Prompt estructurado |
|----------|-------------|---------------------|
| Menciona el objetivo del sistema | No | Sí |
| Menciona a los usuarios principales | No | Sí |
| Tiene exactamente 3 funcionalidades | No | Sí |
| Está en 3 párrafos | No | Sí |
| Lo usaría en un informe real | No | Sí |

### Observaciones
El prompt estructurado permite obtener una respuesta precisa, alineada con el formato deseado . En cambio, el prompt vago genera una respuesta  impredecible en extensión y sin varios detalles clave.

## Ejercicio 5: Anatomía de un prompt, paso a paso

### Desglose de componentes del prompt final

| Componente | Texto de mi prompt |
|------------|--------------------|
| Rol | Actúa como desarrollador Java. |
| Instrucción | Crea un programa en Java usando una clase Producto con los atributos codigo, nombre, precio y stock. |
| Contexto | ...para gestionar los productos de una tienda. |
| Ejemplo | Usa este estilo para los métodos: getPrecio(), setPrecio(double precio). |
| Formato | Explica primero la estructura de la clase y luego presenta el código Java. |

### Evolución de las respuestas por nivel

- **Nivel 1 (Básico):** La IA genera un programa en Java genérico e impredecible (como un "Hola Mundo" o una calculadora simple).
- **Nivel 2 (+ Rol):** Adopta un tono más técnico y profesional orientado al desarrollo de software.
- **Nivel 3 (+ Contexto):** Centra la lógica del programa en el dominio específico de la gestión de productos de tienda.
- **Nivel 4 (+ Instrucción):** Incluye de forma exacta los atributos solicitados (`codigo`, `nombre`, `precio`, `stock`) dentro de la clase `Producto`.
- **Nivel 5 (+ Formato y Ejemplo):** Organiza la salida explicando primero la estructura, sigue las convenciones de nombres solicitadas en los métodos y entrega el código listo para usar.

## Ejercicio 6: Del prompt básico al profesional (e iterar)

### Evaluación del prompt profesional

| Qué revisar | Cumple (Sí / No) |
|-------------|------------------|
| ¿Está escrito en Java y usa Swing? | Sí |
| ¿Pide correo y contraseña? | Sí |
| ¿Explica el funcionamiento antes o después del código? | Sí |
| ¿El código está organizado en clases? | Sí |
| ¿Valida los datos que ingresa el usuario? | No (hasta la iteración) |

### Prompt final iterado

```text
Actua como desarrollador Java. Crea un ejemplo de login para una aplicacion de escritorio utilizando Swing. El usuario debe ingresar correo y contrasena. Explica brevemente el funcionamiento y presenta el codigo organizado por clases.

[Mejora iterativa]: Mejora el codigo anterior con estas restricciones: no uses librerias externas, valida que el correo contenga @ y que la contrasena tenga al menos 8 caracteres, y muestra los mensajes con JOptionPane.

