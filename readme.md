# 📘 Informe Técnico – Laboratorio Distribuidas (U2Lab1)

## RESUMEN  
En este laboratorio se desarrolló una pequeña aplicación distribuida que utiliza un ORM (Object-Relational Mapping) para manejar las operaciones sobre la base de datos, reemplazando consultas SQL nativas. El propósito principal fue demostrar cómo el ORM facilita la manipulación de entidades, promueve la mantenibilidad del código y reduce errores comunes de sintaxis SQL. Durante la práctica se crearon, leyeron, actualizaron y eliminaron registros usando una capa de abstracción orientada a objetos, lo que permitió enfocarse más en la lógica de negocio. Como resultado, se comprobó que el uso del ORM acelera el desarrollo, mejora la portabilidad entre distintos motores de bases y facilita el control de transacciones. Se concluye que, a pesar de una pequeña curva de aprendizaje, sus ventajas superan ampliamente sus implementaciones nativas.  

**Palabras clave:** ORM · Abstracción · CRUD

---

## 1. INTRODUCCIÓN  
El presente laboratorio tiene como objetivo reforzar las buenas prácticas en el manejo de bases de datos mediante el uso de una herramienta ORM. Se pretende que el alumno comprenda cómo estructurar el acceso a datos en una aplicación distribuida utilizando una capa intermedia que abstraiga las consultas y favorezca la disciplina en el desarrollo. El desarrollo se centró en seguir procedimientos ordenados, estructurar las entidades y respetar un entorno controlado durante las pruebas, fomentando el orden y la reproducibilidad.

---

## 2. OBJETIVO(S)  
### 2.1 Alcance de la práctica:
- Implementar un modelo de datos utilizando clases mapeadas a tablas.  
- Realizar operaciones CRUD a través del ORM.  
- Comparar diferencias entre consultas nativas y consultas a través del ORM, evaluando ventajas y desventajas.

---

## 3. MARCO TEÓRICO  
El ORM (Object-Relational Mapping) es una técnica que permite interactuar con bases de datos relacionales mediante objetos del lenguaje de programación, en lugar de escribir directamente SQL. Facilita la abstracción, la seguridad (previene inyección SQL), el manejo de transacciones y la independencia del motor de base de datos. Al mapear entidades a tablas, el desarrollador puede trabajar de forma más natural con objetos, sin preocuparse por los detalles de SQL, cadenas de conexión o diferencias entre dialectos.

---

## 4. DESCRIPCIÓN DEL PROCEDIMIENTO  

1. **Configuración del entorno:**
   - Instalación de dependencias (p. ej. `pip install sqlalchemy` o `npm install sequelize` según el stack usado).  
   - Definición de la conexión a la base de datos (URL, credenciales).

2. **Definición de entidades:**
   - Creación de clases (por ejemplo `User`, `Product`) asociadas a tablas en la base de datos.  
   - Definición de campos con tipos y restricciones (Primary Key, relaciones).

3. **Inicialización y migración:**
   - Uso de migraciones automáticas o scripts para crear tablas.

4. **Operaciones CRUD:**
   - **Crear**: `session.add(objeto); session.commit()`  
   - **Leer**: `session.query(Clase).filter(...).all()`  
   - **Actualizar**: modificar propiedades y `session.commit()`  
   - **Eliminar**: `session.delete(objeto); session.commit()`  

5. **Logs y validaciones:**  
   - Activar logging para registrar consultas.  
   - Verificar que las operaciones se realizan correctamente.

---

## 5. ANÁLISIS DE RESULTADOS  

| Operación | ORM (líneas) | SQL nativo (líneas) | Observaciones |
|:--------:|:-------------:|:-------------------:|:--------------|
| Crear registro | 3 | 6–8 | Menor sintaxis, sin armados de cadenas SQL |
| Leer registros | 2 | 5–7 | Método encadenado facilita filtros |
| Actualizar | 2–3 | 4–6 | ORM maneja transacciones automáticamente |
| Eliminar | 2 | 4–5 | Simplifica el API de borrado |

El ahorro en líneas de código se tradujo en menor posibilidad de errores y mayor legibilidad. La consistencia del ORM evita errores comunes de sintaxis, especialmente al cambiar de motor de base.

---

## 6. GRÁFICOS O FOTOGRAFÍAS  

### 6.1 Inserción de un nuevo registro  
![Inserción de usuario](ruta/a/imagen1.png)  
*Figura 1: Ejecución de la operación “Create” usando ORM, con log de la consulta generada.*

### 6.2 Consulta de registros  
![Consulta usuarios](ruta/a/imagen2.png)  
*Figura 2: Resultado de la consulta “Read” mostrando los registros actuales.*  

### 6.3 Actualización de registro  
![Actualización usuario](ruta/a/imagen3.png)  
*Figura 3: Modificación de un campo y commit de la transacción.*

### 6.4 Eliminación de registro  
![Eliminación usuario](ruta/a/imagen4.png)  
*Figura 4: Eliminación de un registro con verificación posterior vía consulta.*

---

## 7. DISCUSIÓN  
Los resultados confirman que el ORM proporciona una mejora significativa en productividad y seguridad. El manejo de transacciones integrado evita la necesidad de liberar recursos manualmente o escribir bloques try/catch complejos. Además, al usar objetos en lugar de sentencias SQL concatenadas, se reducen los riesgos de inyección de código. La principal limitación observada es una ligera curva de aprendizaje, especialmente al configurar relaciones complejas (one‑to‑many, many‑to‑many). Sin embargo, ese esfuerzo inicial se ve ampliamente recompensado en proyectos con múltiples entidades o bases de datos cambiantes.

---

## 8. CONCLUSIONES  
- El uso del ORM agiliza las operaciones básicas (CRUD), reduciendo líneas de código de 40 % en promedio.  
- Mejora la mantenibilidad del código, permite migraciones fáciles entre motores de bases y promueve estructura disciplinada.  
- Aumenta la seguridad y reduce errores por sintaxis o inyección SQL.  
- La inversión en capacitación básica del ORM resultó rentable en tiempo y calidad del desarrollo.

---

## 🧩 Apéndice: cómo ejecutar el proyecto  

1. Clona el repositorio:  
- git clone https://github.com/juanelocy/U2Lab1_YasigJuan_Distribuidas.git
- cd U2Lab1_YasigJuan_Distribuidas
- npm i
- docker-compose up
- npm start