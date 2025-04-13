# Sistema de Gestión de Glamping

Sistema web para la gestión de reservas de glampings desarrollado con JavaScript vanilla, HTML y CSS utilizando el patrón de arquitectura MVC (Modelo-Vista-Controlador).

## 📋 Descripción

Este proyecto implementa un sistema completo para la gestión de un negocio de glamping, permitiendo administrar:

- Clientes
- Glampings (alojamientos)
- Reservas

El sistema funciona completamente en el lado del cliente (frontend) utilizando localStorage para la persistencia de datos, lo que permite su funcionamiento sin necesidad de un servidor backend.

## 🚀 Tecnologías utilizadas

- HTML5
- CSS3
- JavaScript (ES6+)
- localStorage para persistencia de datos
- Arquitectura MVC (Modelo-Vista-Controlador)

## 📁 Estructura del proyecto

```
/
├── controller/              # Controladores para la lógica de negocio
│   ├── ClienteController.js
│   ├── GlampingController.js
│   └── ReservaController.js
├── model/                   # Modelos de datos
│   ├── Cliente.js
│   ├── Glamping.js
│   └── Reserva.js
└── view/                    # Vistas y scripts de interfaz
    ├── css/                 # Estilos CSS
    │   └── styles.css
    ├── js/                  # JavaScript para las vistas
    │   ├── clientes.js
    │   ├── glampings.js
    │   ├── reservas.js
    │   └── init-data.js     # Script para inicialización de datos
    ├── clientes.html        # Página de gestión de clientes
    ├── glampings.html       # Página de gestión de glampings
    ├── reservas.html        # Página de gestión de reservas
    └── index.html           # Página principal
```

## 🏗️ Arquitectura MVC

### 🧩 Modelos (Model)

Los modelos representan las entidades principales del sistema:

- **Cliente.js**: Gestiona la información de los clientes
- **Glamping.js**: Gestiona la información de los alojamientos
- **Reserva.js**: Gestiona las reservas relacionando clientes con glampings

### 🎮 Controladores (Controller)

Los controladores implementan la lógica de negocio:

- **ClienteController.js**: Operaciones CRUD para clientes
- **GlampingController.js**: Operaciones CRUD para glampings
- **ReservaController.js**: Operaciones CRUD para reservas y validación de disponibilidad

### 👁️ Vistas (View)

Las vistas son la interfaz de usuario:

- **HTML**: Estructura las páginas y formularios
- **CSS**: Estilos visuales del sistema
- **JavaScript de vistas**: Maneja eventos, renderizado y comunicación con controladores

## 💾 Persistencia de datos

El sistema utiliza el localStorage del navegador para almacenar todos los datos. La estructura de almacenamiento es:

- `clientes`: Array JSON con los datos de los clientes
- `glampings`: Array JSON con los datos de los glampings
- `reservas`: Array JSON con los datos de las reservas

## 🔍 Funcionalidades principales

### Gestión de Clientes
- Registro de nuevos clientes
- Listado de clientes
- Edición de información de clientes
- Eliminación de clientes (con validación de reservas asociadas)

### Gestión de Glampings
- Registro de nuevos glampings
- Listado de glampings (formato tabla y tarjetas)
- Edición de información de glampings
- Visualización detallada de características
- Eliminación de glampings (con validación de reservas asociadas)

### Gestión de Reservas
- Creación de nuevas reservas
- Verificación de disponibilidad de glampings por fechas
- Listado de reservas con filtros (cliente, glamping, estado)
- Cálculo automático de precios según duración y tarifa
- Cambio de estado de reservas (pendiente, confirmada, cancelada)
- Visualización de calendario de reservas

## 🔧 Validaciones

El sistema incluye validaciones para:

- Campos obligatorios en formularios
- Formato de email en clientes
- Disponibilidad de fechas en reservas
- Verificación de relaciones antes de eliminación
- Valores numéricos positivos para precios y capacidades

## 🏃‍♂️ Cómo ejecutar el proyecto

1. Clona el repositorio o descarga los archivos del proyecto
2. Abre el archivo `view/index.html` en un navegador web moderno
3. El sistema inicializará automáticamente con datos de prueba la primera vez

## 📝 Desarrollo y ampliación

Para desarrollar nuevas funcionalidades:

1. Modifica o crea nuevos modelos en la carpeta `/model/`
2. Implementa la lógica de negocio en controladores dentro de `/controller/`
3. Diseña la interfaz de usuario en archivos HTML y CSS en `/view/`
4. Implementa la interacción con JavaScript en archivos JS en `/view/js/`

## ⚠️ Consideraciones

- Este proyecto está diseñado para navegadores modernos con soporte para ES6
- Los datos se almacenan localmente en el navegador. El uso de modo incógnito o limpiar datos del navegador eliminará toda la información
- Para un entorno de producción, se recomienda implementar una base de datos y backend adecuados

## 🔧 Solución a problemas comunes

### Error "Uncaught ReferenceError: module is not defined"

Este error ocurre porque el código originalmente estaba diseñado para funcionar con Node.js (utilizando module.exports), pero el proyecto actual funciona completamente en el navegador.

**Solución aplicada:**
- Se eliminaron todas las referencias a `module.exports` en los archivos de modelo
- Se adaptaron los métodos de persistencia para usar localStorage en lugar de archivos físicos
- Se añadió un script de inicialización (init-data.js) para crear datos de prueba automáticamente

### Error "Uncaught SyntaxError: redeclaration of let [Class]"

Este error ocurre cuando se intenta redeclarar una clase que ya ha sido definida en otro archivo.

**Solución aplicada:**
- Se aseguró el orden correcto de carga de los scripts en los archivos HTML
- Se eliminaron las importaciones explícitas de modelos en los controladores

### Error "ReservaController is not defined"

Este error ocurre cuando se intenta usar una clase controlador que no ha sido cargada todavía.

**Solución aplicada:**
- Se incluyeron todos los controladores necesarios en cada página HTML donde se requieren
- Se modificó el orden de carga para asegurar que las dependencias se cargan correctamente 