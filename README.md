# 🏛️ Workshop: GitHub Copilot para anahuac puebla

## Desarrollo Asistido por IA con .NET 8

![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Enabled-green)
![.NET 8](https://img.shields.io/badge/.NET-8.0-purple)
![Duración](https://img.shields.io/badge/Duración-3%20horas-blue)

---

## 📋 Tabla de Contenidos

- [Introducción](#-introducción)
- [Conceptos Clave de GitHub Copilot](#-conceptos-clave-de-github-copilot)
- [Pre-requisitos](#️-pre-requisitos)
- [Agenda del Workshop](#-agenda-del-workshop)
- [Laboratorio 1: Especificaciones con IA](#-laboratorio-1-especificaciones-con-ia-30-min)
- [Laboratorio 2: REST API con .NET](#-laboratorio-2-rest-api-con-net-45-min)
- [Laboratorio 3: Frontend con Agente Especializado](#-laboratorio-3-frontend-con-agente-especializado-30-min)
- [Laboratorio 4: Pruebas y Documentación](#-laboratorio-4-pruebas-y-documentación-20-min)
- [Laboratorio 5: Características Avanzadas](#-laboratorio-5-características-avanzadas-15-min)
- [Referencia Rápida](#-referencia-rápida)
- [Recursos Adicionales](#-recursos-adicionales)

---

## 🎯 Introducción

Este workshop práctico te guiará en el desarrollo de un **Sistema de Ventas de Productos Escolares** para anahuac puebla utilizando **GitHub Copilot** como asistente de desarrollo. Aprenderás a:

- ✅ Generar especificaciones técnicas con IA
- ✅ Crear APIs REST siguiendo arquitectura Vertical Slice
- ✅ Desarrollar frontends con estilo institucional
- ✅ Escribir pruebas unitarias automáticamente
- ✅ Crear agentes personalizados especializados
- ✅ Traducir código legacy a tecnologías modernas

### Estándares del Proyecto

| Aspecto | Estándar |
|---------|----------|
| **Tipo** | API REST |
| **Tecnología** | C# .NET 8 |
| **Arquitectura** | Vertical Slice + Repository Pattern |
| **Idioma** | Español (código, comentarios, documentación) |
| **Base de datos** | InMemory (desarrollo) / SQL Server (producción) |
| **Frontend** | Blazor WebAssembly |

---

## 🧠 Conceptos Clave de GitHub Copilot

### ¿Qué es @workspace?

El **@workspace** es un participante de chat que proporciona contexto sobre todo tu espacio de trabajo (proyecto) a GitHub Copilot.

#### ¿Para qué sirve?

| Función | Ejemplo |
|---------|---------|
| **Buscar código** | `@workspace ¿dónde se define la clase Producto?` |
| **Entender el proyecto** | `@workspace ¿qué hace este proyecto?` |
| **Encontrar patrones** | `@workspace ¿cómo se implementan los repositorios?` |
| **Generar código contextual** | `@workspace crea un nuevo endpoint similar a los existentes` |

#### ¿Cuándo usarlo?

- ✅ Cuando necesitas que Copilot entienda la estructura de tu proyecto
- ✅ Para generar código que siga los patrones existentes
- ✅ Para buscar implementaciones específicas
- ✅ Para preguntas sobre arquitectura del proyecto

#### Ejemplo práctico:

```
# Sin @workspace - Copilot no conoce tu proyecto
"Crea un controlador para productos escolares"
→ Genera código genérico

# Con @workspace - Copilot analiza tu proyecto
"@workspace Crea un controlador para productos escolares"
→ Genera código siguiendo TUS patrones y convenciones
```

---

### Modos de GitHub Copilot Chat

GitHub Copilot tiene **tres modos principales** de operación. Es crucial entender cuándo usar cada uno:

#### 1️⃣ Modo Ask (Preguntar) 💬

| Característica | Descripción |
|----------------|-------------|
| **Ícono** | 💬 Burbuja de mensaje |
| **Función** | Solo responde preguntas, **NO modifica archivos** |
| **Uso ideal** | Explorar, entender, planificar, aprender |

**Cuándo usar Modo Ask:**
- 🔍 Investigar cómo implementar algo
- 📚 Entender código existente
- 🤔 Comparar opciones de diseño
- 📋 Planificar antes de implementar

**Ejemplo:**
```
[Modo Ask]
"¿Cuál es la mejor forma de implementar autenticación JWT en .NET 8?"

→ Copilot EXPLICA las opciones pero NO crea archivos
```

---

#### 2️⃣ Modo Agent (Agente) 🤖

| Característica | Descripción |
|----------------|-------------|
| **Ícono** | 🤖 Robot o chispa |
| **Función** | **PUEDE crear y modificar archivos** automáticamente |
| **Uso ideal** | Implementar cambios, crear código, refactorizar |

**Cuándo usar Modo Agent:**
- ✏️ Crear nuevos archivos
- 🔧 Modificar código existente
- 🏗️ Implementar funcionalidades completas
- 🔄 Refactorizar código

**Ejemplo:**
```
[Modo Agent]
"Crea un controlador REST para productos escolares con operaciones CRUD"

→ Copilot CREA el archivo ProductosController.cs con todo el código
```

---

#### 3️⃣ Modo Plan (Planificar) 📋

| Característica | Descripción |
|----------------|-------------|
| **Ícono** | 📋 Lista o documento |
| **Función** | Genera un **plan detallado ANTES de ejecutar** |
| **Uso ideal** | Tareas complejas que involucran múltiples archivos |

**Cuándo usar Modo Plan:**
- 📁 Crear múltiples archivos relacionados
- 🏛️ Implementar funcionalidades que cruzan capas
- 🔍 Revisar cambios antes de aplicarlos
- ⚠️ Tareas donde quieres control sobre cada paso

**Ejemplo:**
```
[Modo Plan]
"Implementa la funcionalidad completa de Ventas con entidad, DTOs, 
repositorio, servicio y controlador"

→ Copilot MUESTRA el plan:
  1. Crear Venta.cs
  2. Crear VentaDto.cs
  3. Crear IVentaRepositorio.cs
  4. Crear VentaRepositorio.cs
  5. Crear VentasController.cs

→ Tú APRUEBAS cada paso antes de que se ejecute
```

---

#### Comparativa de Modos

| Aspecto | Ask 💬 | Agent 🤖 | Plan 📋 |
|---------|--------|----------|---------|
| Modifica archivos | ❌ No | ✅ Sí | ✅ Sí (con aprobación) |
| Velocidad | Rápido | Rápido | Más lento |
| Control | N/A | Bajo | Alto |
| Ideal para | Aprender | Implementar | Tareas complejas |
| Riesgo | Ninguno | Medio | Bajo |

---

### Agentes Personalizados (@nombre-agente)

Los **agentes personalizados** son "expertos" que puedes crear para tareas específicas. Se definen en archivos Markdown en `.github/agents/`.

#### ¿Cómo funcionan?

1. Creas un archivo `.github/agents/mi-agente.md`
2. Defines el rol, reglas y conocimiento del agente
3. Lo invocas con `@mi-agente` en el chat

#### ¿Para qué sirven?

| Uso | Ejemplo |
|-----|---------|
| **Especialización** | Agente experto en frontend con estilos anahuac puebla |
| **Consistencia** | Agente que siempre sigue los estándares del equipo |
| **Revisión** | Agente que revisa código según checklist |
| **Dominio** | Agente que conoce terminología específica de anahuac puebla |

#### Ejemplo de agente:

```markdown
# .github/agents/frontend-anahuac puebla.md

# Agente: Frontend anahuac puebla

## Rol
Eres experto en desarrollo frontend para anahuac puebla.

## Reglas
- Usar colores institucionales (#00594C, #8DC63F)
- Todo el texto en español mexicano
- Componentes accesibles (WCAG AA)
```

**Uso:**
```
@frontend-anahuac puebla Crea un componente de tarjeta para mostrar productos
```

---

### Comandos Especiales (/comando)

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/tests` | Genera pruebas unitarias | Selecciona código → `/tests` |
| `/doc` | Genera documentación XML | Selecciona clase → `/doc` |
| `/fix` | Propone corrección de errores | Selecciona código con error → `/fix` |
| `/explain` | Explica código seleccionado | Selecciona código → `/explain` |
| `/new` | Crea nuevo archivo/proyecto | `/new crear clase Producto` |

---

## 🛠️ Pre-requisitos

### Software Necesario

```powershell
# Verificar instalaciones
dotnet --version  # Debe ser 8.0 o superior
code --version    # Visual Studio Code
git --version     # Git
```

> **📝 NOTA:** Este taller usa **base de datos en memoria** (InMemory Database) para no requerir instalación de software adicional como SQL Server o SQLite. Los datos se pierden al reiniciar la aplicación, pero es perfecto para desarrollo y pruebas.

### Extensiones de VS Code

1. **GitHub Copilot** - Extensión principal
2. **GitHub Copilot Chat** - Chat integrado
3. **C# Dev Kit** - Soporte para .NET

### Cuenta de GitHub

- Necesitas una cuenta con acceso a GitHub Copilot
- Puede ser licencia individual, de organización o educativa

---

## 📅 Agenda del Workshop

| Tiempo | Módulo | Descripción | Modo Copilot |
|--------|--------|-------------|--------------|
| 0:00 - 0:15 | Introducción | Setup y configuración | - |
| 0:15 - 0:45 | Lab 1 | Especificaciones y diseño | **Ask** → **Agent** |
| 0:45 - 1:30 | Lab 2 | REST API para productos escolares | **Agent** + **Plan** |
| 1:30 - 1:45 | ☕ Break | Descanso | - |
| 1:45 - 2:15 | Lab 3 | Frontend con Agente | **@frontend-anahuac puebla** |
| 2:15 - 2:35 | Lab 4 | Pruebas y documentación | **Agent** |
| 2:35 - 2:50 | Lab 5 | Agentes y traducción | **Custom Agents** |
| 2:50 - 3:00 | Cierre | Q&A y recursos | - |

---

## 🔬 LABORATORIO 1: Especificaciones con IA (30 min)

### Objetivos
- ✅ Usar Modo Ask para explorar y diseñar
- ✅ Cambiar a Modo Agent para crear archivos
- ✅ Generar especificaciones técnicas completas

---

### Paso 1.1: Crear estructura inicial

**🤖 PROMPT en Modo Agent:**

```
Crea la estructura de carpetas inicial para el proyecto:
- docs/especificaciones
- src
- .github/agents
```

**📝 Alternativa manual (si el agente no ejecuta los comandos):**

```powershell
mkdir -p docs/especificaciones
mkdir -p src
mkdir -p .github/agents
```

---

### Paso 1.2: Explorar con MODO ASK 🔍

> **💡 IMPORTANTE:** Asegúrate de estar en **Modo Ask** (ícono de mensaje 💬 en Copilot Chat). Este modo NO modifica archivos, solo responde preguntas.

**📍 Cómo activar Modo Ask:**
1. Abre Copilot Chat (`Ctrl+Shift+I`)
2. Busca el selector de modo en la parte superior
3. Selecciona "Ask" o el ícono de mensaje

**🤖 PROMPT - Copia y pega en Copilot Chat:**

```
Soy arquitecto de software en anahuac puebla y necesito diseñar un sistema de ventas de productos escolares. 

Ayúdame a entender:

1. ¿Qué entidades principales necesitaría para un sistema que gestione:
   - Diferentes categorías de productos escolares (Útiles, Uniformes, Libros)
   - Inventario de productos con características y precios
   - Ventas a estudiantes con información de la escuela
   - Estadísticas de ventas por escuela y categoría

2. ¿Qué endpoints REST serían necesarios?

3. ¿Cómo aplicar Vertical Slice Architecture en este contexto?

4. ¿Qué consideraciones de seguridad debo tener para datos de estudiantes y transacciones?

Responde en español.
```

**📝 Observa:** Copilot responde con información detallada pero **NO crea ningún archivo**. Esto es ideal para la fase de exploración.

---

### Paso 1.3: Refinar el diseño con preguntas de seguimiento

> **💡 NOTA:** Seguimos en Modo Ask para profundizar en el diseño.

**🤖 PROMPT de seguimiento:**

```
Gracias. Ahora explícame con más detalle:

1. ¿Cómo estructurarías los Vertical Slices para la funcionalidad de Productos?
   - Muéstrame la estructura de carpetas
   - ¿Qué archivos tendría cada slice?

2. Para el Repository Pattern, ¿usarías repositorios genéricos o específicos?

3. Dame un ejemplo de cómo se vería un endpoint POST para crear producto siguiendo estos patrones

Sigue respondiendo en español
```

---

### Paso 1.4: Cambiar a MODO AGENT para implementar 🤖

> **💡 IMPORTANTE:** Ahora cambia a **Modo Agent** (ícono de robot 🤖). Este modo **PUEDE crear y modificar archivos**.

**📍 Cómo activar Modo Agent:**
1. En Copilot Chat, busca el selector de modo
2. Selecciona "Agent" o el ícono de robot/chispa

**🤖 PROMPT en Modo Agent:**

```
Ahora sí, crea la especificación técnica del sistema para los modulos de Gestion de productos y ventas basicas

Crea el archivo docs/especificaciones/especificacion-sistema.md con:

1. **Visión General**
   - Sistema REST API + Frontend para gestionar ventas de productos escolares del anahuac puebla
   
2. **Estándares Técnicos**
   | Aspecto | Estándar |
   |---------|----------|
   | Tipo | API REST |
   | Tecnología | C# .NET 8 |
   | Arquitectura | Vertical Slice + Repository Pattern |
   | Idioma | Español |

3. **Requisitos Funcionales**
   - CRUD de productos escolares (Útiles, Uniformes, Libros, etc.)
   - Gestión de características de productos: precio, categoría, stock, descripción
   - Ventas a estudiantes con información de escuela y grado
   - Estadísticas de ventas por escuela

4. **Modelo de Datos** (diagrama Mermaid)

5. **Estructura de Vertical Slices**

6. **Endpoints de la API** (tabla completa)

Todo en español
```

**✅ Resultado esperado:** Copilot crea el archivo `docs/especificaciones/especificacion-sistema.md` automáticamente.

---

### Paso 1.5: Crear modelo de dominio con diagrama

**🤖 PROMPT en Modo Agent:**

```
Crea el archivo docs/especificaciones/modelo-dominio.md con:

1. Diagrama Mermaid de entidad-relación para:
   - Producto (Id, Nombre, Descripcion, Precio, Stock, CategoriaProducto, Marca, SKU)
   - DetalleVenta (Id, VentaId, ProductoId, Cantidad, PrecioUnitario, Subtotal)
   - Venta (Id, EstudianteId, FechaVenta, Total, MetodoPago)
   - Estudiante (Id, NombreCompleto, Matricula, Escuela, Grado, Grupo)
   - EstadisticaVentas (Id, ProductoId, Escuela, TotalVentas, TotalUnidades)

2. Descripción de cada entidad en español

3. Reglas de negocio

4. Catálogo de tipos (CategoriaProducto, EstadoProducto, MetodoPago)

Todo en español mexicano
```

---

### Paso 1.6: Definir contratos de API

> **💡 NOTA:** Usamos `#file:` para referenciar archivos existentes y que Copilot use ese contexto.

**🤖 PROMPT en Modo Agent:**

```
Basándote en los endpoints definidos en #file:docs/especificaciones/especificacion-sistema.md, crea el archivo docs/especificaciones/contratos-api.md con la especificación detallada.

Para cada endpoint incluye:
- Esquema de solicitud (JSON)
- Esquema de respuesta (JSON)  
- Códigos de estado HTTP
- Ejemplos de uso

Todo en español
```

**✅ Verificar antes de continuar:**
- [ ] Existen los 3 archivos en `docs/especificaciones/`
- [ ] Los diagramas Mermaid se renderizan correctamente en VS Code
- [ ] La tabla de endpoints está completa

---

### 🛠️ Troubleshooting Lab 1

| Problema | Solución |
|----------|----------|
| Copilot no crea archivos | Verifica que estés en **Modo Agent**, no en Modo Ask |
| Los diagramas Mermaid no se ven | Instala la extensión "Markdown Preview Mermaid Support" |
| Copilot responde en inglés | Agrega "Responde en español" al final del prompt |

---

## 🔬 LABORATORIO 2: REST API con .NET (45 min)

### Objetivos
- ✅ Crear estructura de proyecto .NET
- ✅ Implementar arquitectura Vertical Slice
- ✅ Usar Modo Plan para tareas complejas
- ✅ Generar código siguiendo estándares

---

### Paso 2.1: Crear instrucciones de Copilot

> **⚠️ IMPORTANTE:** Este paso debe ejecutarse **ANTES** de crear código para que Copilot siga los estándares desde el inicio.

**🤖 PROMPT en Modo Agent:**

```
Crea el archivo .github/copilot-instructions.md con instrucciones para que Copilot actúe como experto en .NET para anahuac puebla:

# Instrucciones para GitHub Copilot - Proyecto anahuac puebla Productos Escolares

## Idioma
- Todo el código, comentarios y documentación debe estar en **español**
- Mensajes de error en español mexicano
- Nombres de variables y métodos en español (excepto palabras técnicas estándar como Get, Set, Async)

## Estándares de Código
| Aspecto | Estándar |
|---------|----------|
| Tecnología | C# .NET 8 |
| Arquitectura | Vertical Slice + Repository Pattern |
| Async | Usar async/await en todas las operaciones I/O |
| Nullable | Nullable reference types habilitados |

## Nomenclatura
- Clases y métodos públicos: PascalCase en español (Producto, ObtenerTodas)
- Variables privadas: _camelCase (_productoRepositorio)
- Interfaces: IEntidad (IProductoRepositorio)
- DTOs: EntidadDto, CrearEntidadSolicitud, ActualizarEntidadSolicitud

## Estructura Vertical Slice
Cada funcionalidad debe estar en: /Funcionalidades/{Nombre}/
- {Nombre}.cs (Entidad)
- {Nombre}Dto.cs (DTOs)
- I{Nombre}Repositorio.cs (Interface)
- {Nombre}Repositorio.cs (Implementación)
- {Nombre}sController.cs (Controlador)

## Documentación
- XML comments en español para todas las APIs públicas
- Documentar parámetros y valores de retorno
- Incluir ejemplos en comentarios cuando sea útil

## anahuac puebla Específico
- Terminología oficial: Producto, Venta, Categoría, Estudiante, Inventario
- Escuelas participantes: Primaria, Secundaria, Preparatoria
- Formatos de fecha: dd/MM/yyyy para display, ISO 8601 para API

## Seguridad
- Nunca loggear datos sensibles (nombres completos, matrículas, información de pago)
- Validar todas las entradas del usuario
- Usar consultas parametrizadas (nunca concatenar SQL)
- Implementar rate limiting en endpoints públicos

## Manejo de Errores
- Usar excepciones personalizadas para errores de negocio
- Retornar ProblemDetails en errores HTTP
- Loggear excepciones con contexto suficiente
```

---

### Paso 2.2: Crear la solución y proyectos

> **💡 DEMOSTRACIÓN:** Este paso muestra cómo GitHub Copilot puede interactuar con la terminal para ejecutar comandos.

**🤖 PROMPT en Modo Agent:**

```
Crea la estructura del proyecto .NET en la carpeta src:

1. Una solución llamada anahuac puebla.ProductosEscolares
2. Un proyecto Web API llamado anahuac puebla.ProductosEscolares.API con .NET 8
3. Un proyecto de pruebas xUnit llamado anahuac puebla.ProductosEscolares.Pruebas
4. Agrega los proyectos a la solución
5. Agrega la referencia del proyecto de pruebas al API

Ejecuta los comandos en la terminal
```

**✅ Observa:** Copilot debería ejecutar los comandos `dotnet` automáticamente en la terminal integrada.

**📝 Alternativa manual:**

```powershell
cd src
dotnet new sln -n anahuac puebla.ProductosEscolares
dotnet new webapi -n anahuac puebla.ProductosEscolares.API -f net8.0
dotnet new xunit -n anahuac puebla.ProductosEscolares.Pruebas -f net8.0
dotnet sln add anahuac puebla.ProductosEscolares.API
dotnet sln add anahuac puebla.ProductosEscolares.Pruebas
dotnet add anahuac puebla.ProductosEscolares.Pruebas reference anahuac puebla.ProductosEscolares.API
```

---

### Paso 2.3: Usar MODO PLAN para tarea compleja 📋

> **💡 IMPORTANTE:** Activa **Modo Plan** (ícono de lista 📋). Este modo genera un plan detallado ANTES de ejecutar, permitiéndote revisar y aprobar cada paso.

**📍 Cómo activar Modo Plan:**
1. En Copilot Chat, busca el selector de modo
2. Selecciona "Plan" o "Edit" con planificación

**🤖 PROMPT en Modo Plan:**

```
Basándote en la especificación #file:docs/especificaciones/especificacion-sistema.md y el modelo de dominio #file:docs/especificaciones/modelo-dominio.md, implementa la funcionalidad principal de gestión de productos escolares.

Crea la estructura Vertical Slice completa en src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ con:

1. **Entidad**: Con las propiedades definidas en el modelo de dominio, incluyendo:
   - Enums para estados y tipos según la especificación
   - Validaciones en el constructor
   - Timestamps de auditoría

2. **DTOs**: Para transferencia de datos según los contratos definidos

3. **Repositorio**: Interface e implementación con Entity Framework

4. **Controlador**: Con los endpoints definidos en la especificación de API

Requisitos:
- Seguir la nomenclatura definida en copilot-instructions.md
- Async/await en todas las operaciones
- Documentación XML completa
- Validaciones con Data Annotations
- Atributos para Swagger

Muéstrame el plan antes de ejecutar
```

**📝 Observa el plan:** Copilot analizará las especificaciones y mostrará un plan como:

```
📋 Plan de implementación:

1. ✏️ Crear src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/Producto.cs
   - Entidad principal con propiedades y validaciones
   - Enums EstadoProducto, CategoriaProducto y MetodoPago

2. ✏️ Crear src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/ProductoDto.cs
   - DTOs para transferencia de datos

3. ✏️ Crear src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/IProductoRepositorio.cs
   - Interface del repositorio

4. ✏️ Crear src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/ProductoRepositorio.cs
   - Implementación con Entity Framework

5. ✏️ Crear src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/ProductosController.cs
   - Controlador REST con todos los endpoints

¿Aprobar plan?
```

**Revisa y aprueba** cada paso del plan.

**✅ Verificar:** Después de aprobar el plan, verifica que se crearon los archivos en `src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/`

---

### Paso 2.4: Implementar DbContext

**🤖 PROMPT en Modo Agent:**

```
@workspace Basándote en las entidades creadas y la especificación #file:docs/especificaciones/modelo-dominio.md, crea el DbContext en src/anahuac puebla.ProductosEscolares.API/Datos/:

1. DbContext para Entity Framework Core (compatible con InMemory)
2. DbSets para las entidades del modelo de dominio
3. Configuración Fluent API en OnModelCreating:
   - Índices en campos de búsqueda frecuente
   - Configuración de longitudes máximas
   - Relaciones entre entidades

4. Método público InicializarDatosSemilla() que:
   - Verifique si ya existen datos
   - Si no hay datos, agregue 3 productos de ejemplo según los tipos definidos en la especificación
   - Guarde los cambios
```

---

### Paso 2.5: Configurar Program.cs

**🤖 PROMPT en Modo Agent:**

```
@workspace Actualiza src/anahuac puebla.ProductosEscolares.API/Program.cs para configurar:

1. Entity Framework con base de datos en memoria:
   - Usar UseInMemoryDatabase("ProductosDb")
   - No requiere connection string externo ni instalación de BD

2. Inyección de dependencias:
   - Registrar ProductosDbContext
   - Registrar IProductoRepositorio -> ProductoRepositorio

3. Swagger/OpenAPI con:
   - Título: "API de Productos Escolares anahuac puebla"
   - Descripción: "API REST para gestión de ventas de productos escolares"
   - Versión: v1
   - Contacto: anahuac puebla

4. Middleware:
   - Habilitar CORS para desarrollo (permitir localhost)
   - Usar Swagger en desarrollo
   - Mapear controladores

5. Inicializar datos semilla al arrancar:
   - Obtener el DbContext del service provider
   - Llamar al método InicializarDatosSemilla()
```

---

### Paso 2.6: Instalar paquetes NuGet necesarios

> **💡 DEMOSTRACIÓN:** Copilot puede instalar paquetes NuGet directamente.

**🤖 PROMPT en Modo Agent:**

```
Instala el paquete NuGet en el proyecto anahuac puebla.ProductosEscolares.API:
- Microsoft.EntityFrameworkCore.InMemory
```

**📝 Alternativa manual:**

```powershell
cd src/anahuac puebla.ProductosEscolares.API
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

> **📝 NOTA:** Usamos `InMemory` en lugar de SQLite o SQL Server para no requerir instalación de software adicional. Los datos se almacenan en memoria y se pierden al reiniciar, pero los datos semilla se cargan automáticamente al iniciar.

---

### Paso 2.7: Ejecutar y probar la API

> **💡 DEMOSTRACIÓN:** Copilot puede compilar y ejecutar proyectos .NET.

**🤖 PROMPT en Modo Agent:**

```
Compila y ejecuta el proyecto anahuac puebla.ProductosEscolares.API
```

**📝 Alternativa manual:**

```powershell
cd src/anahuac puebla.ProductosEscolares.API
dotnet run
```

Abre en el navegador: `https://localhost:5001/swagger` o `http://localhost:5000/swagger`

**✅ Verificar:**
- Swagger UI muestra todos los endpoints
- GET /api/v1/productos retorna los productos semilla
- POST /api/v1/productos puede crear nuevos productos

> **💡 Si algo falla:** Revisa la consola de VS Code para ver errores de compilación o runtime.

---

### Paso 2.8: Implementar funcionalidad de Ventas

**🤖 PROMPT en Modo Plan:**

```
Basándote en #file:docs/especificaciones/especificacion-sistema.md y #file:docs/especificaciones/modelo-dominio.md, implementa la funcionalidad de Ventas como Vertical Slice.

Revisa el modelo de dominio para:
- Identificar la entidad de ventas y sus propiedades
- Identificar las relaciones con Productos y Estudiantes
- Identificar los métodos de pago soportados

Crea en src/anahuac puebla.ProductosEscolares.API/Funcionalidades/:
1. Entidad Venta con sus propiedades según el modelo
2. Entidad DetalleVenta para el carrito de compras
3. DTOs correspondientes
4. Interface e implementación del repositorio
5. Controlador con los endpoints definidos en la especificación
6. Actualizar el DbContext con los nuevos DbSets

Muéstrame el plan primero
```

**✅ Verificar antes de continuar:**
- [ ] La API compila sin errores (`dotnet build`)
- [ ] Swagger muestra endpoints de Productos y Ventas
- [ ] Los datos semilla se cargan al iniciar

---

### 🛠️ Troubleshooting Lab 2

| Problema | Solución |
|----------|----------|
| Error "Package not found" | Ejecuta `dotnet restore` en la carpeta del proyecto |
| DbContext no registrado | Verifica que `Program.cs` tenga `builder.Services.AddDbContext<...>` |
| Swagger no aparece | Asegúrate de que `app.UseSwagger()` esté antes de `app.Run()` |
| Puerto en uso | Cambia el puerto en `launchSettings.json` o cierra otras instancias |
| Datos semilla no aparecen | Verifica que `InicializarDatosSemilla()` se llame en `Program.cs` |

---

## 🔬 LABORATORIO 3: Frontend con Agente Especializado (30 min)

> **⚠️ PRERREQUISITO:** Este laboratorio requiere haber completado el **Laboratorio 2**. Necesitas:
> - La solución `anahuac puebla.ProductosEscolares.sln` creada
> - El proyecto `anahuac puebla.ProductosEscolares.API` funcionando
> - El archivo `.github/copilot-instructions.md` configurado

### Objetivos
- ✅ Crear un agente personalizado especializado
- ✅ Usar el agente para desarrollo frontend
- ✅ Aplicar estilos institucionales de anahuac puebla
- ✅ Consumir la API REST desde Blazor

---

### Paso 3.1: Crear el Agente de Frontend (versión básica) 🤖

> **💡 CONCEPTO:** Los agentes personalizados permiten crear "expertos" especializados que Copilot puede usar para tareas específicas.

**🤖 PROMPT en Modo Agent:**

```
Crea el archivo .github/agents/frontend-anahuac puebla.md con un agente básico para desarrollo frontend:

# Agente: Frontend anahuac puebla (@frontend-anahuac puebla)

## Rol
Eres un experto en desarrollo frontend para el Instituto Nacional de Estadística y Geografía (anahuac puebla).

## Idioma
- Todo el código, comentarios y textos de interfaz deben estar en **español mexicano**
- Usar terminología oficial de anahuac puebla (Producto, Venta, Estudiante, Escuela, Categoría, etc.)

## Tecnologías
- Blazor WebAssembly (.NET 8)
- CSS3 con variables personalizadas (custom properties)
- HTML5 semántico

## Accesibilidad (WCAG AA)
- Contraste mínimo 4.5:1 para texto
- Todos los elementos interactivos accesibles por teclado
- Atributos ARIA donde corresponda

## Responsive Design
- Enfoque Mobile First
- Breakpoints: Móvil (< 576px), Tablet (576px - 992px), Desktop (> 992px)

## Reglas Importantes
1. SIEMPRE incluir estados de carga (spinners, skeletons)
2. SIEMPRE manejar errores con mensajes amigables en español
3. NUNCA usar inglés en textos visibles para el usuario
4. SIEMPRE documentar componentes con comentarios en español
```

---

### Paso 3.2: Analizar el sitio de anahuac puebla con screenshot 📸 *(Opcional)*

> **💡 DEMOSTRACIÓN:** Copilot puede analizar imágenes para extraer información de diseño como colores, tipografía y estilos.
>
> **📝 NOTA:** Los pasos 3.2 y 3.3 son opcionales pero recomendados. Si los omites, el agente usará colores institucionales genéricos definidos en el paso 3.1.

**📍 Instrucciones:**
1. Abre el sitio oficial de anahuac puebla: https://www.anahuac puebla.org.mx/
2. Toma un screenshot de la página principal (usa `Win+Shift+S` en Windows o `Cmd+Shift+4` en Mac)
3. Guarda la imagen o tenla en el portapapeles

**🤖 PROMPT en Modo Agent (adjunta el screenshot):**

```
Analiza este screenshot del sitio oficial de anahuac puebla y extrae la siguiente información de diseño:

1. **Paleta de colores**: Identifica los colores principales usados en:
   - Header/navegación
   - Botones y llamadas a la acción
   - Fondos y textos
   - Acentos y elementos secundarios
   Proporciona los códigos hexadecimales exactos o aproximados

2. **Tipografía**: 
   - Fuentes utilizadas (o similares si no son identificables)
   - Jerarquía de tamaños (h1, h2, h3, texto base)

3. **Componentes UI identificados**:
   - Estilo de header y navegación
   - Estilo de tarjetas/cards
   - Estilo de botones
   - Estilo de footer

4. **Espaciado y layout**:
   - Márgenes y paddings aproximados
   - Estructura de grid

Genera esta información en formato que pueda agregar al agente frontend-anahuac puebla.md
```

---

### Paso 3.3: Actualizar el agente con estilos de anahuac puebla 🎨 *(Opcional)*

> **💡 NOTA:** Ahora actualizamos el agente básico con la información extraída del screenshot. (Requiere haber completado el paso 3.2)

**🤖 PROMPT en Modo Agent:**

```
Actualiza el archivo #file:.github/agents/frontend-anahuac puebla.md agregando la información de diseño extraída del screenshot.

Agrega las siguientes secciones después de "Responsive Design":

## Paleta de Colores Institucional anahuac puebla
(Incluye los colores identificados con sus códigos hex y uso recomendado)

## Tipografía
(Incluye las fuentes y escala de tamaños)

## Componentes Estándar
Describe el estilo visual para:
- Header Institucional
- Footer Institucional  
- Tarjetas (Cards)
- Botones
- Tablas

## Estructura de Archivos
Organiza los componentes Blazor así:
/Components
  /Layout
  /Paginas
  /Compartidos
/wwwroot
  /css
  /img
```

**✅ Resultado:** El agente ahora tiene toda la información de diseño institucional de anahuac puebla extraída directamente del sitio oficial.

---

### Paso 3.4: Crear proyecto Blazor

**🤖 PROMPT en Modo Agent:**

```
Crea un proyecto Blazor WebAssembly llamado anahuac puebla.ProductosEscolares.Web con .NET 8 en la carpeta src y agrégalo a la solución anahuac puebla.ProductosEscolares.sln
```

**📝 Alternativa manual:**

```powershell
cd src
dotnet new blazorwasm -n anahuac puebla.ProductosEscolares.Web -f net8.0
dotnet sln add anahuac puebla.ProductosEscolares.Web
```

**✅ Verificar:** El proyecto aparece en la solución (`dotnet sln list`)

---

### Paso 3.5: Usar el Agente @frontend-anahuac puebla 🎨

> **💡 IMPORTANTE:** A partir de ahora, usa el agente especializado escribiendo `@frontend-anahuac puebla` al inicio de cada prompt relacionado con frontend.

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Crea el archivo de estilos principal para el proyecto web.

Necesito un archivo CSS que:
- Defina variables con la paleta de colores institucional
- Incluya un reset CSS básico
- Configure la tipografía base importando las fuentes necesarias
- Tenga clases reutilizables para los componentes principales: botones, tarjetas, encabezado, navegación, pie de página y tablas
- Incluya clases utilitarias para layout y espaciado
- Agregue animaciones sutiles para transiciones y estados de carga

Usa los estilos definidos en el agente frontend-anahuac puebla.md
```

---

### Paso 3.6: Crear Layout Principal

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Crea el layout principal de la aplicación Blazor.

Quiero un diseño que replique la estructura del sitio oficial de anahuac puebla con:

- Un encabezado institucional con el logo, título del sistema y navegación principal
- Una barra secundaria con breadcrumbs para mostrar la ubicación actual
- Un área de contenido principal centrada y con buen espaciado
- Un pie de página institucional con logo, enlaces legales, contacto y copyright

El layout debe ser completamente responsive y usar los estilos definidos en el tema CSS
```

---

### Paso 3.7: Crear Componentes Reutilizables

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Crea componentes Blazor reutilizables para el sistema de productos escolares.

Necesito los siguientes componentes:

1. **Tarjeta de Producto**: Un componente que muestre la información de un producto en formato card, incluyendo nombre, descripción, precio, stock disponible, un badge de estado con colores según la disponibilidad, y un botón de "Agregar al carrito" o "Agotado" según el stock

2. **Widget de Estadística**: Un componente para mostrar métricas destacadas con un número grande, título descriptivo e ícono. Ideal para dashboards

3. **Indicador de Carga**: Un componente simple con spinner y mensaje personalizable para mostrar estados de carga

Todos los componentes deben:
- Recibir parámetros apropiados
- Usar los estilos del tema anahuac puebla
- Ser responsive
- Tener documentación básica
```

---

### Paso 3.8: Crear Página Principal

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Crea la página de inicio del Sistema de Ventas de Productos Escolares.

La página debe incluir:

1. Una sección hero llamativa con título, subtítulo motivacional sobre la importancia de adquirir productos escolares, y un botón para ver los productos disponibles

2. Una sección de estadísticas destacadas usando los widgets, mostrando métricas como productos disponibles, ventas totales, escuelas atendidas y estudiantes registrados (usa datos de ejemplo por ahora)

3. Una sección que muestre los productos destacadas usando el componente de tarjeta, con datos de ejemplo hardcodeados

4. Una sección informativa explicando los beneficios de adquirir productos escolares en la tienda

5. Un call-to-action final para contacto

La página debe ser la ruta principal ("/") y ser completamente responsive
```

---

### Paso 3.9: Crear Servicio HTTP

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Crea un servicio para consumir la API REST de productos escolares.

El servicio debe:

1. Definir los modelos/DTOs necesarios para representar productos, ventas, respuestas paginadas y filtros de búsqueda

2. Crear una interface con métodos para:
   - Obtener lista de productos escolares con filtros y paginación
   - Obtener un producto por su identificador
   - Obtener productos destacados para la página principal

3. Implementar el servicio usando HttpClient con:
   - Manejo de errores apropiado
   - Serialización JSON
   - URL base configurable

Por ahora, implementa con datos de ejemplo hardcodeados (mock) para poder probar sin la API. Incluye comentarios indicando dónde conectar con la API real
```

---

### Paso 3.10: Crear Página de Catálogo de Productos

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Crea una página completa para listar y buscar productos.

La página necesita:

1. Un encabezado con título, subtítulo y contador de resultados encontrados

2. Una barra de filtros con:
   - Dropdown para filtrar por categoría de producto
   - Dropdown para filtrar por disponibilidad (Disponible/Agotado)
   - Campo de búsqueda por texto
   - Botones para buscar y limpiar filtros

3. Un grid responsive de tarjetas de producto usando el componente creado anteriormente

4. Manejo de diferentes estados de la página:
   - Estado de carga con el indicador
   - Estado vacío cuando no hay resultados
   - Estado de error con opción de reintentar

5. Paginación para navegar entre páginas de resultados

La página debe consumir el servicio de productos escolares e inyectarlo apropiadamente
```

---

### Paso 3.11: Configurar Program.cs del Frontend

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Configura el Program.cs del proyecto web para:

1. Registrar el HttpClient con la URL base de la API:
   - Usa https://localhost:5001 para desarrollo (mismo puerto configurado en la API)

2. Registrar el servicio de productos escolares en el contenedor de inyección de dependencias

3. Cualquier otra configuración necesaria para que la aplicación funcione correctamente
```

---

### Paso 3.12: Actualizar referencias de estilos

**🤖 PROMPT con Agente:**

```
@frontend-anahuac puebla Actualiza src/anahuac puebla.ProductosEscolares.Web/wwwroot/index.html para:

1. Agregar referencia al archivo tema-anahuac puebla.css
2. Agregar Google Fonts (Montserrat y Open Sans)
3. Agregar meta tags apropiados en español
4. Título: "Sistema de Ventas de Productos Escolares - anahuac puebla"

Mantén la estructura existente de Blazor
```

---

### Paso 3.13: Ejecutar el Frontend

**🤖 PROMPT en Modo Agent:**

```
Ejecuta ambos proyectos:
1. Primero inicia anahuac puebla.ProductosEscolares.API en una terminal
2. Luego inicia anahuac puebla.ProductosEscolares.Web en otra terminal
```

**📝 Alternativa manual:**

```powershell
# Terminal 1: Ejecutar API
cd src/anahuac puebla.ProductosEscolares.API
dotnet run

# Terminal 2: Ejecutar Frontend
cd src/anahuac puebla.ProductosEscolares.Web
dotnet run
```

Abre el navegador en la URL indicada (generalmente `https://localhost:5002` o similar).

**✅ Verificar antes de continuar:**
- [ ] El frontend carga sin errores en el navegador
- [ ] Los estilos anahuac puebla se aplican correctamente
- [ ] La página de inicio muestra las secciones diseñadas

---

### 🛠️ Troubleshooting Lab 3

| Problema | Solución |
|----------|----------|
| El agente @frontend-anahuac puebla no responde | Recarga VS Code después de crear el archivo del agente |
| CORS error al conectar con API | Verifica que la API tenga CORS habilitado para localhost |
| Estilos no se aplican | Revisa que `index.html` referencie el archivo CSS correcto |
| Componentes no se renderizan | Verifica los `@using` en `_Imports.razor` |
| HttpClient error | Confirma que la URL base coincida con el puerto de la API |

---

## 🔬 LABORATORIO 4: Pruebas y Documentación (20 min)

> **⚠️ PRERREQUISITO:** Este laboratorio requiere haber completado el **Laboratorio 2**. Necesitas:
> - El proyecto `anahuac puebla.ProductosEscolares.API` con las entidades y controladores creados
> - El proyecto `anahuac puebla.ProductosEscolares.Pruebas` en la solución

### Objetivos
- ✅ Generar pruebas unitarias automáticamente
- ✅ Usar el comando /tests
- ✅ Generar documentación XML
- ✅ Crear README profesional

---

### Paso 4.1: Generar pruebas unitarias con /tests

> **💡 COMANDO ESPECIAL:** El comando `/tests` genera automáticamente pruebas unitarias para el código seleccionado.

**📍 Cómo usar /tests:**
1. Abre el archivo `src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/Producto.cs`
2. Selecciona toda la clase (Ctrl+A en el archivo)
3. Abre Copilot Chat y escribe el prompt

**🤖 PROMPT:**

```
/tests Genera pruebas unitarias completas para esta entidad usando xUnit y FluentAssertions.

Quiero pruebas que cubran:

1. La creación de la entidad con datos válidos e inválidos (nombre vacío, nulo, fechas inconsistentes)

2. Los valores por defecto de las propiedades al crear una nueva instancia

3. Los métodos de comportamiento de la entidad (cambios de estado, validaciones de negocio)

Requisitos generales:
- Patrón Arrange-Act-Assert con comentarios en español
- Nombres de métodos descriptivos que indiquen qué se prueba y qué se espera
- Usar Theory con InlineData cuando haya múltiples casos similares
```

---

### Paso 4.2: Instalar paquetes de pruebas

**🤖 PROMPT en Modo Agent:**

```
Instala los paquetes de pruebas en anahuac puebla.ProductosEscolares.Pruebas:
- FluentAssertions
- Moq
- Microsoft.AspNetCore.Mvc.Testing (para pruebas de integración)
```

**📝 Alternativa manual:**

```powershell
cd src/anahuac puebla.ProductosEscolares.Pruebas
dotnet add package FluentAssertions
dotnet add package Moq
dotnet add package Microsoft.AspNetCore.Mvc.Testing
```

---

### Paso 4.3: Generar pruebas de integración

**🤖 PROMPT en Modo Agent:**

```
@workspace Crea pruebas de integración para el controlador de productos escolares.

Necesito pruebas que verifiquen el comportamiento completo de la API:

1. Pruebas para cada operación CRUD (obtener todos, obtener por id, crear, actualizar, eliminar)

2. Pruebas de casos de error (recurso no encontrado, datos inválidos)

3. Verificación de códigos de estado HTTP correctos para cada escenario

Configuración necesaria:
- Usar WebApplicationFactory para crear un servidor de pruebas en memoria
- Base de datos en memoria aislada para cada prueba
- Helpers para simplificar la creación de requests
```

---

### Paso 4.4: Generar documentación XML con /doc

> **💡 COMANDO ESPECIAL:** El comando `/doc` genera documentación XML automáticamente.

**📍 Cómo usar /doc:**
1. Abre `src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/ProductosController.cs`
2. Selecciona toda la clase
3. Usa el comando /doc

**🤖 PROMPT:**

```
/doc Genera documentación XML completa en español para este controlador.

Para la clase y cada método público incluye:
- Descripción clara de qué hace
- Documentación de todos los parámetros
- Descripción del valor de retorno
- Códigos de respuesta HTTP posibles con su significado

La documentación debe ser profesional, concisa y útil para que se muestre correctamente en Swagger/OpenAPI
```

---

### Paso 4.5: Habilitar documentación XML en el proyecto

**🤖 PROMPT en Modo Agent:**

```
@workspace Configura el proyecto API para que genere documentación XML automáticamente y que Swagger la muestre en la interfaz.

Necesito que:
- El proyecto genere el archivo XML de documentación al compilar
- Swagger lea y muestre los comentarios de documentación en la UI
- Se manejen apropiadamente las advertencias de documentación faltante
```

---

### Paso 4.6: Ejecutar pruebas

**🤖 PROMPT en Modo Agent:**

```
Ejecuta todas las pruebas del proyecto anahuac puebla.ProductosEscolares.Pruebas y muéstrame los resultados
```

**📝 Alternativa manual:**

```powershell
cd src/anahuac puebla.ProductosEscolares.Pruebas
dotnet test --verbosity normal
```

**✅ Verificar antes de continuar:**
- [ ] Todas las pruebas pasan (verde)
- [ ] Swagger muestra la documentación XML
- [ ] Los comentarios aparecen en cada endpoint

---

### 🛠️ Troubleshooting Lab 4

| Problema | Solución |
|----------|----------|
| FluentAssertions no encontrado | Ejecuta `dotnet restore` en el proyecto de pruebas |
| WebApplicationFactory falla | Asegúrate de tener el paquete `Microsoft.AspNetCore.Mvc.Testing` |
| Pruebas fallan por datos | Cada prueba debe usar su propia instancia de BD en memoria |
| Documentación XML no aparece | Verifica `GenerateDocumentationFile` en el .csproj |
| Warnings CS1591 | Agrega `<NoWarn>CS1591</NoWarn>` al .csproj si deseas suprimirlos |

---

## 🔬 LABORATORIO 5: Características Avanzadas (15 min)

> **⚠️ PRERREQUISITO:** Este laboratorio requiere haber completado los **Laboratorios 2 y 3**. Necesitas:
> - La estructura completa del proyecto API
> - El archivo `.github/copilot-instructions.md` configurado
> - Familiaridad con los modos de Copilot (Ask, Agent, Plan)

### Objetivos
- ✅ Traducir código legacy a C# moderno
- ✅ Integrar bibliotecas de terceros
- ✅ Crear agente de revisión de código

---

### Paso 5.1: Traducción de código legacy

> **💡 ESCENARIO:** Tienes código VB.NET antiguo que necesitas migrar a C# moderno.

**📝 Primero crea la carpeta y el archivo de ejemplo:**

```powershell
mkdir legacy
```

**Luego crea el archivo:** `legacy/ConsultaProducto.vb`

```vb
' Código VB.NET legacy de ejemplo - Sistema anterior de anahuac puebla
Imports System.Data.SqlClient

Public Class ConsultaProducto
    Private conexion As String = "Data Source=SERVIDOR;Initial Catalog=PRODUCTOS;Integrated Security=True"
    
    ' Obtiene todas los productos disponibles
    Public Function ObtenerProductosDisponibles() As DataTable
        Dim dt As New DataTable()
        Using conn As New SqlConnection(conexion)
            conn.Open()
            Dim sql As String = "SELECT * FROM Productos WHERE Disponible = 1 ORDER BY Nombre ASC"
            Dim cmd As New SqlCommand(sql, conn)
            Dim adapter As New SqlDataAdapter(cmd)
            adapter.Fill(dt)
        End Using
        Return dt
    End Function
    
    ' Obtiene un producto por su ID
    ' NOTA: Este código tiene una vulnerabilidad de SQL Injection
    Public Function ObtenerProductoPorId(ByVal id As Integer) As DataRow
        Dim dt As New DataTable()
        Using conn As New SqlConnection(conexion)
            conn.Open()
            Dim sql As String = "SELECT * FROM Productos WHERE Id = " & id.ToString()
            Dim cmd As New SqlCommand(sql, conn)
            Dim adapter As New SqlDataAdapter(cmd)
            adapter.Fill(dt)
        End Using
        If dt.Rows.Count > 0 Then
            Return dt.Rows(0)
        Else
            Return Nothing
        End If
    End Function
    
    ' Guarda un nuevo producto
    Public Sub GuardarProducto(ByVal nombre As String, ByVal descripcion As String, ByVal precio As Decimal, ByVal stock As Integer)
        Using conn As New SqlConnection(conexion)
            conn.Open()
            Dim sql As String = "INSERT INTO Productos (Nombre, Descripcion, Precio, Stock, Disponible) VALUES ('" & nombre & "', '" & descripcion & "', " & precio & ", " & stock & ", 1)"
            Dim cmd As New SqlCommand(sql, conn)
            cmd.ExecuteNonQuery()
        End Using
    End Sub
End Class
```

**🤖 PROMPT para traducir:**

```
Traduce este código VB.NET legacy a C# moderno siguiendo los estándares del proyecto anahuac puebla:

Requisitos de la traducción:

1. **Arquitectura**: Implementar como repositorio siguiendo Vertical Slice
   - Crear IProductoRepositorioLegacy.cs
   - Crear ProductoRepositorioLegacy.cs

2. **Modernización**:
   - Convertir todos los métodos a async/await
   - Usar Entity Framework Core en lugar de ADO.NET directo
   - Retornar entidades tipadas en lugar de DataTable/DataRow

3. **Seguridad** (CRÍTICO):
   - Corregir la vulnerabilidad de SQL Injection en ObtenerProductoPorId
   - Corregir la vulnerabilidad en GuardarProducto
   - Usar consultas parametrizadas o LINQ

4. **Mejoras**:
   - Agregar manejo de excepciones apropiado
   - Agregar logging con ILogger
   - Usar nullable reference types
   - Agregar CancellationToken a métodos async

5. **Documentación**:
   - XML comments en español
   - Comentarios explicando cambios importantes

6. **Nomenclatura**:
   - Nombres de métodos en español según estándares del proyecto
   - ObtenerProductosDisponibles -> ObtenerActivasAsync
   - ObtenerProductoPorId -> ObtenerPorIdAsync
   - GuardarProducto -> CrearAsync

Crea los archivos en src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/Legacy/
```

---

### Paso 5.2: Integrar biblioteca externa

**🤖 PROMPT en Modo Plan:**

```
@workspace Quiero agregar funcionalidad para exportar resultados de productos escolares a Excel.

Implementa lo siguiente:

1. **Paquete NuGet**: Agregar ClosedXML al proyecto API

2. **Servicio de Exportación**: 
   Crear en src/anahuac puebla.ProductosEscolares.API/Funcionalidades/Exportacion/
   
   - IExportacionServicio.cs con método:
     Task<byte[]> ExportarProductoAExcelAsync(Guid productoId)
   
   - ExportacionServicio.cs que genere Excel con:
     * Hoja "Resumen": estadísticas generales del producto (ventas, stock, etc.)
     * Hoja "Ventas": historial de ventas del producto con fechas y cantidades
     * Formato con colores institucionales anahuac puebla:
       - Encabezados: fondo verde (#00594C), texto blanco
       - Filas alternas: blanco y gris claro (#F5F5F5)
     * Logo anahuac puebla en esquina superior (placeholder)
     * Fecha de generación

3. **Endpoint**:
   GET /api/v1/productos/{id}/exportar
   - Query param: formato=xlsx (por ahora solo Excel)
   - Retorna archivo para descarga
   - Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
   - Header Content-Disposition con nombre de archivo

4. **Prueba unitaria** para el servicio

Muéstrame el plan primero
```

---

### Paso 5.3: Crear agente de revisión de código

**🤖 PROMPT en Modo Agent:**

```
Crea .github/agents/revisor-codigo.md con un agente especializado en revisión de código:

# Agente: Revisor de Código anahuac puebla (@revisor-codigo)

## Rol
Eres un revisor de código senior especializado en .NET y los estándares de desarrollo de anahuac puebla. Tu trabajo es revisar código y proporcionar retroalimentación constructiva.

## Idioma
Toda la retroalimentación debe estar en **español mexicano**.

## Checklist de Revisión

### Estándares del Proyecto
- [ ] Código en español (variables, métodos, comentarios)
- [ ] Arquitectura Vertical Slice respetada
- [ ] Repository Pattern implementado correctamente
- [ ] Nombres siguen convenciones (PascalCase público, _camelCase privado)

### Calidad de Código
- [ ] Async/await usado correctamente
- [ ] Nullable reference types manejados
- [ ] No hay código duplicado
- [ ] Métodos con responsabilidad única
- [ ] Complejidad ciclomática aceptable

### Seguridad
- [ ] Sin datos sensibles en logs
- [ ] Validación de entradas presente
- [ ] Sin SQL Injection posible
- [ ] Sin secretos hardcodeados

### Rendimiento
- [ ] Consultas optimizadas (no N+1)
- [ ] Uso apropiado de AsNoTracking
- [ ] Paginación implementada en listas

### Documentación
- [ ] XML comments en APIs públicas
- [ ] Comentarios útiles (no obvios)

### Pruebas
- [ ] Cobertura de casos principales
- [ ] Nombres descriptivos
- [ ] Arrange-Act-Assert

## Formato de Respuesta

Al revisar código, responde con este formato:

---

## 📋 Revisión de Código: [Nombre del archivo]

### ✅ Aspectos Positivos
- Punto positivo 1
- Punto positivo 2

### ⚠️ Sugerencias de Mejora (Opcionales)
| Línea | Sugerencia | Razón |
|-------|------------|-------|
| 15 | Cambiar X por Y | Mejora legibilidad |

### ❌ Problemas a Corregir (Obligatorios)
| Línea | Problema | Solución |
|-------|----------|----------|
| 23 | SQL Injection | Usar parámetros |

### 📝 Código Sugerido

(código corregido aquí)

### 📊 Resumen
- Calidad general: ⭐⭐⭐⭐☆ (4/5)
- Seguridad: ✅ Aprobado / ⚠️ Revisar / ❌ Rechazado
- Listo para merge: Sí / No / Con cambios menores

---

## Severidad de Problemas

- 🔴 **Crítico**: Bloquea merge (seguridad, errores graves)
- 🟠 **Mayor**: Debe corregirse antes de merge
- 🟡 **Menor**: Sugerencia de mejora
- 🟢 **Info**: Comentario informativo
```

---

### Paso 5.4: Usar el agente revisor

**🤖 PROMPT con Agente:**

```
@revisor-codigo Revisa el archivo src/anahuac puebla.ProductosEscolares.API/Funcionalidades/ProductosEscolares/ProductosController.cs

Evalúa:
1. Cumplimiento de estándares del proyecto anahuac puebla
2. Calidad y legibilidad del código
3. Posibles problemas de seguridad
4. Rendimiento de las consultas
5. Completitud de la documentación
6. Cobertura de casos de error

Proporciona retroalimentación detallada con sugerencias de mejora específicas.
```

**✅ Verificar al finalizar el workshop:**
- [ ] Código legacy traducido compila sin errores
- [ ] El endpoint de exportación genera archivo Excel válido
- [ ] El agente @revisor-codigo proporciona feedback útil

---

### 🛠️ Troubleshooting Lab 5

| Problema | Solución |
|----------|----------|
| ClosedXML no instala | Verifica conexión a internet y ejecuta `dotnet restore` |
| Error al generar Excel | Asegúrate de que el servicio esté registrado en DI |
| Agente @revisor-codigo no funciona | Verifica la ruta `.github/agents/revisor-codigo.md` |
| Traducción de VB.NET incompleta | Proporciona más contexto en el prompt sobre los estándares |

---

## 📖 Referencia Rápida

### Comandos de Copilot Chat

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `@workspace` | Contexto del proyecto completo | `@workspace ¿cómo se implementan los repos?` |
| `/tests` | Generar pruebas unitarias | Selecciona código → `/tests` |
| `/doc` | Generar documentación XML | Selecciona clase → `/doc` |
| `/fix` | Proponer corrección de errores | Selecciona error → `/fix` |
| `/explain` | Explicar código seleccionado | Selecciona código → `/explain` |
| `/new` | Crear nuevo archivo | `/new crear servicio de exportación` |
| `@frontend-anahuac puebla` | Agente de frontend | `@frontend-anahuac puebla crea componente` |
| `@revisor-codigo` | Agente de revisión | `@revisor-codigo revisa este archivo` |

### Atajos de Teclado

| Atajo | Acción |
|-------|--------|
| `Ctrl+I` | Abrir Copilot inline en el editor |
| `Ctrl+Shift+I` | Abrir panel de Copilot Chat |
| `Tab` | Aceptar sugerencia de Copilot |
| `Esc` | Rechazar sugerencia |
| `Alt+]` | Ver siguiente sugerencia |
| `Alt+[` | Ver sugerencia anterior |
| `Ctrl+Enter` | Abrir Copilot Completions Panel |

### Modos de Copilot

| Modo | Cuándo Usar |
|------|-------------|
| **Ask** 💬 | Explorar, entender, planificar (no modifica archivos) |
| **Agent** 🤖 | Implementar, crear archivos, hacer cambios |
| **Plan** 📋 | Tareas complejas multi-archivo (con aprobación) |

---

## ✅ Checklist Final del Workshop

Al terminar el workshop, deberías tener:

### Documentación
- [ ] `docs/especificaciones/especificacion-sistema.md`
- [ ] `docs/especificaciones/modelo-dominio.md`
- [ ] `docs/especificaciones/contratos-api.md`

### Backend (API)
- [ ] Solución .NET con estructura Vertical Slice
- [ ] `Funcionalidades/ProductosEscolares/` completo (entidad, DTOs, repo, controller)
- [ ] `Funcionalidades/Ventas/` implementado
- [ ] `Datos/ProductosDbContext.cs` configurado
- [ ] Swagger funcionando en `/swagger`

### Frontend
- [ ] Proyecto Blazor WebAssembly
- [ ] Archivo CSS con estilos institucionales anahuac puebla
- [ ] `Components/Layout/MainLayout.razor`
- [ ] `Components/Pages/Inicio.razor`
- [ ] `Components/Pages/Productos.razor`
- [ ] Componentes compartidos (TarjetaProducto, etc.)

### Pruebas
- [ ] Pruebas unitarias para entidad Producto
- [ ] Pruebas de integración para ProductosController

### Configuración de Copilot
- [ ] `.github/copilot-instructions.md`
- [ ] `.github/agents/frontend-anahuac puebla.md`
- [ ] `.github/agents/revisor-codigo.md`

### Extras
- [ ] Código legacy traducido a C# moderno
- [ ] Servicio de exportación a Excel

---

## 📚 Recursos Adicionales

### Documentación Oficial
- [GitHub Copilot Docs](https://docs.github.com/en/copilot)
- [VS Code + Copilot](https://code.visualstudio.com/docs/copilot/overview)
- [.NET 8 Documentation](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-8)
- [Blazor Documentation](https://learn.microsoft.com/en-us/aspnet/core/blazor/)

### Patrones y Arquitectura
- [Vertical Slice Architecture](https://www.jimmybogard.com/vertical-slice-architecture/)
- [Repository Pattern](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/infrastructure-persistence-layer-design)

### anahuac puebla
- [Portal anahuac puebla](https://www.anahuac puebla.org.mx/)
- [Catálogo de Entidades Federativas](https://www.anahuac puebla.org.mx/app/ageeml/)

---

## 🙋 Preguntas Frecuentes

### ¿Por qué Copilot no sigue mis instrucciones del archivo copilot-instructions.md?
Asegúrate de que:
1. El archivo esté en `.github/copilot-instructions.md`
2. Hayas recargado VS Code después de crearlo
3. Estés usando `@workspace` para que tome contexto

### ¿Cómo hago que Copilot genere código en español?
1. Inclúyelo explícitamente en el prompt: "Todo en español"
2. Configúralo en `copilot-instructions.md`
3. Proporciona ejemplos en español en tu código existente

### ¿El Modo Plan no me muestra el plan, ¿qué hago?
- Verifica que tengas la última versión de la extensión
- Intenta con tareas más complejas (el plan es más útil para múltiples archivos)
- Usa Modo Agent si solo necesitas crear un archivo

### ¿Los agentes personalizados no funcionan?
- Verifica la ruta: `.github/agents/nombre-agente.md`
- El nombre del archivo (sin .md) es el nombre del agente
- Recarga VS Code después de crear el archivo

### ¿Por qué usamos base de datos en memoria?

Este taller usa `Microsoft.EntityFrameworkCore.InMemory` por las siguientes razones:

| Ventaja | Descripción |
|---------|-------------|
| **Sin instalación** | No requiere SQL Server, SQLite ni ningún motor de BD |
| **Rápido** | Operaciones instantáneas, ideal para desarrollo |
| **Portable** | Funciona igual en cualquier máquina |
| **Aislado** | Cada ejecución inicia limpia con datos semilla |

**Limitaciones a considerar:**
- Los datos se pierden al detener la aplicación
- No soporta algunas características avanzadas de SQL
- Para producción, cambiar a SQL Server o PostgreSQL

**¿Cómo cambiar a SQL Server en producción?**
1. Cambiar paquete: `Microsoft.EntityFrameworkCore.SqlServer`
2. Actualizar Program.cs: `UseInMemoryDatabase` → `UseSqlServer(connectionString)`
3. Agregar connection string en appsettings.json

---

## 👥 Créditos

**Workshop desarrollado para:** Instituto Nacional de Estadística y Geografía (anahuac puebla)

**Tecnologías:** GitHub Copilot, .NET 8, Blazor WebAssembly, C#

**Duración:** 3 horas

---

*¿Preguntas o comentarios? Contacta al equipo de capacitación.*
