# Actividad-5-API-CON-CRUD

# API de Alumnos de la BUAP

API desarrollada con FastAPI para consultar un json de alumnos respectivos de la comunidad BUAP.

## Documentación interactiva(A veces se desactiva, porque uso version gratuita para subir la API)
- **Swagger UI (Testing UI)**: [https://api-alumnos-mz6o.onrender.com/docs](https://api-alumnos-mz6o.onrender.com/docs)
- **ReDoc (Documentación alternativa)**: [https://api-alumnos-mz6o.onrender.com/redoc](https://api-alumnos-mz6o.onrender.com/redoc)

## Endpoints disponibles

### Obtener todos los alumnos
- `GET /alumnos/` - Devuelve todos los registros de alumnos (50 items)

### Búsqueda por parámetros (Query)
- `GET /alumnos` - Filtra por ID y nombre exacto:
  - `id`: ID del alumno (requerido)
  - `nombre`: Nombre completo exacto (requerido)

- `GET /alumnos/matricula` - Busca por matrícula (coincidencia parcial):
  - `matricula`: Parte inicial de la matrícula o igual puede ser toda la matricula :)

- `GET /alumnos/genero/semestre` - Filtra por género y semestre:
  - `genero`: `Masculino`, `Femenino` o `No binario`
  - `semestre`: Semestre actual (ej: `Sexto semestre`)

- `GET /alumnos/genero/semestre/transporte` - Filtro combinado:
  - `genero`, `semestre`, `transporte`: `STU`, `Transporte público`, etc.

- `GET /alumnos/info` - Búsqueda avanzada con todos los campos opcionales

- `GET /alumnos/rango-edad` - Filtra por rango de edad:
  - `min_edad`: Edad mínima
  - `max_edad`: Edad máxima

- `GET /alumnos/rango-porcentaje` - Filtra por avance en carrera:
  - `min_porcentaje`: % mínimo completado
  - `max_porcentaje`: % máximo completado

### Búsqueda por path
- `GET /alumnos/{id}` - Alumno por ID (1-50)
- `GET /alumnos/carrera/{carrera}` - Filtra por carrera exacta
- `GET /alumnos/medio_transporte/{transporte}` - Filtra por transporte
- `GET /alumnos/semestre/{semestre}` - Filtra por semestre
- `GET /alumnos/servicios_bc/{servicios}` - Filtra por uso de biblioteca (`Sí`/`No`)
- `GET /alumnos/experiencia/{value}` - Filtra por experiencia (`Sí`/`No`)

### Crear, actualizar o eliminar registros

- ` POST /usersclass/`
    Agrega un nuevo alumno si su id no existe aún.
    Body (JSON): objeto Alumno.

- ` PUT /usersclass/`
    Actualiza un alumno existente basado en su id.
    Body (JSON): objeto Alumno.

- ` DELETE /alumnos/{id}`
    Elimina un alumno por su id.
    Devuelve un mensaje de éxito o error si no fue encontrado.
  
## Ejemplos de uso

```bash
# Obtener alumno con ID 1
curl -X 'GET' 'https://tu-api.onrender.com/alumnos/1'

# Buscar alumnos de ITI
curl -X 'GET' 'https://tu-api.onrender.com/alumnos/carrera/ITI'

# Filtrar mujeres en transporte público
curl -X 'GET' 'https://tu-api.onrender.com/alumnos/genero/semestre/transporte?genero=Femenino&transporte=Transporte%20público'

# Búsqueda avanzada
curl -X 'GET' 'https://tu-api.onrender.com/alumnos/info?carrera=ITI&min_edad=20&max_edad=22'
