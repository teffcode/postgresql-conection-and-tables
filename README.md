# postgresql-conection-and-tables

Pasos esenciales para PostgreSQL, incluyendo cómo iniciar el servicio, listar las tablas, entrar a una tabla y crear filas/columnas:

**1. Iniciar el Servicio PostgreSQL (macOS con Homebrew):**

Si en algún momento PostgreSQL deja de funcionar, usa este comando para iniciarlo:

```bash
brew services start postgresql
```

**2. Acceder a la Consola `psql`:**

Para interactuar con PostgreSQL, necesitas abrir la consola `psql`. Generalmente, el comando es:

```bash
psql -U postgres -d mi_basededatos
```

*   Reemplaza `postgres` con tu nombre de usuario de PostgreSQL (si no es "postgres").
*   Reemplaza `mi_basededatos` con el nombre de tu base de datos. Si no especificas la base de datos con `-d`, intentará conectarse a una base de datos con el mismo nombre que tu usuario.

**Si tienes problemas de conexión, intenta solo:**

```bash
psql
```

Y luego, dentro de `psql`, conéctate a tu base de datos:

```sql
\c mi_basededatos
```

**3. Listar las Tablas en la Base de Datos Actual:**

Una vez que estás conectado a la base de datos correcta en la consola `psql`, usa este comando para ver una lista de todas las tablas:

```sql
\dt
```

Esto mostrará algo como:

```
              List of relations
 Schema |   Name    | Type  |      Owner
--------+-----------+-------+-----------------
 public | productos | table | estefanyaguilar
(1 row)
```

**4. Describir una Tabla (Ver Columnas):**

Para ver las columnas (y sus tipos de datos) de una tabla específica (por ejemplo, `productos`), usa:

```sql
\d productos
```

Esto mostrará el nombre de cada columna, su tipo de dato (VARCHAR, INTEGER, DECIMAL, etc.), si permite valores nulos (NULL), y otra información relevante.

**5.  Seleccionar Datos de una Tabla (Ver Filas):**

Para ver todos los datos (filas y columnas) en una tabla, usa:

```sql
SELECT * FROM productos;
```

Si quieres seleccionar solo columnas específicas, usa:

```sql
SELECT id, nombre FROM productos;
```

**6. Insertar Datos (Crear Filas):**

Para agregar nuevas filas a una tabla, usa el comando `INSERT INTO`:

```sql
INSERT INTO productos (nombre, precio) VALUES ('Nuevo Producto', 25.50);
```

*   Asegúrate de que los valores que proporcionas coincidan con los tipos de datos de las columnas.
*   Si tu columna `id` es `SERIAL`, no necesitas proporcionar un valor para ella; PostgreSQL la autogenerará.

**7. Crear Columnas Adicionales (Si Necesitas):**

Si necesitas agregar nuevas columnas a una tabla existente, usa el comando `ALTER TABLE`:

```sql
ALTER TABLE productos ADD COLUMN descripcion TEXT;
```

Esto agregará una columna llamada `descripcion` a la tabla `productos` con el tipo de dato `TEXT` (para texto largo).

**Importante:**

*   **Conexión:** Asegúrate siempre de estar conectado a la base de datos correcta antes de ejecutar cualquier comando.
*   **Tipos de Datos:** Elige los tipos de datos correctos para tus columnas.
*   **Nombres:** Usa nombres descriptivos para tus tablas y columnas.
*   **Pruebas:** Después de insertar o modificar datos, usa `SELECT` para verificar que los cambios se hayan realizado correctamente.

¡Espero que esta guía resumida te sea útil! Si tienes alguna pregunta sobre un comando específico o encuentras algún problema, no dudes en preguntar.
