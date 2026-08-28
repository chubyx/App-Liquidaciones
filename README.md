# 💼 Liquidaciones de Sueldo — App de Escritorio para Chile

Aplicación de escritorio desarrollada con **Electron** para la gestión, cálculo y emisión de **liquidaciones de sueldo**, adaptada a la normativa previsional y tributaria chilena.

Permite administrar múltiples empresas, mantener un registro de trabajadores, calcular remuneraciones y generar un historial seguro de los pagos mensuales.

---

## 🚀 Características principales

### 🏢 Soporte Multiempresa

Administra diferentes empresas desde una sola aplicación, manteniendo la información completamente separada.

- Crear y administrar múltiples empresas.
- Registrar RUT y datos de cada empresa.
- Asociar trabajadores mediante `empresaId`.
- Mantener historiales independientes.
- Evitar la mezcla de trabajadores y liquidaciones entre empresas.

---

### 👥 Fichas de Trabajadores

Permite mantener una ficha completa de cada trabajador.

- Datos personales.
- RUT.
- Nombre completo.
- Cargo.
- Tipo de contrato.
- Fecha de ingreso.
- Sueldo base.
- AFP.
- Sistema de salud.
- Fonasa / Isapre.
- Cargas familiares.
- Bonos.
- Horas extras.
- Información previsional.

---

### 💰 Cálculo automático

El sistema permite calcular automáticamente los principales componentes de una liquidación:

- Sueldo base.
- Horas extraordinarias.
- Gratificación legal.
- Bonos imponibles.
- Bonos no imponibles.
- Descuentos previsionales.
- AFP.
- Salud.
- Seguro de Cesantía.
- Impuesto Único de Segunda Categoría.
- Total de haberes.
- Total de descuentos.
- Sueldo líquido.

---

### ⚙️ Parámetros actualizables

La aplicación cuenta con un panel para mantener actualizados los valores utilizados en los cálculos.

Entre ellos:

- UTM.
- Ingreso Mínimo Mensual (IMM).
- Tasas de AFP.
- Seguro de Cesantía.
- Parámetros de salud.
- Tramos del Impuesto Único de Segunda Categoría.
- Topes y valores previsionales.
- Otros parámetros legales.

Esto permite actualizar los valores cuando cambien las condiciones legales.

---

### 🗄️ Almacenamiento local

La aplicación utiliza almacenamiento **100% local**.

No requiere servidores externos ni servicios en la nube.

Toda la información se guarda en un archivo local:

```text
base_datos_liquidaciones.json
```

La estructura general es:

```text
base_datos_liquidaciones.json
│
├── ⚙️ Configuraciones
│   ├── Parámetros tributarios
│   ├── Parámetros previsionales
│   └── Valores legales
│
├── 🏢 Empresas
│   ├── Empresa 1
│   ├── Empresa 2
│   └── Empresa N
│
├── 👥 Trabajadores
│   ├── Trabajadores Empresa 1
│   ├── Trabajadores Empresa 2
│   └── Trabajadores Empresa N
│
└── 📄 Liquidaciones
    ├── Historial Empresa 1
    ├── Historial Empresa 2
    └── Historial Empresa N
```

---

## 🔒 Privacidad y seguridad

La aplicación está diseñada para mantener la información directamente en el equipo donde se encuentra instalada.

Los datos almacenados incluyen:

- 🏢 Empresas.
- 👥 Trabajadores.
- 💰 Remuneraciones.
- 📄 Liquidaciones.
- ⚙️ Parámetros.

### ☁️ Sin nube

La información permanece en el almacenamiento local:

```text
┌──────────────────────────────────────┐
│       🖥️ Aplicación Electron        │
├──────────────────────────────────────┤
│                                      │
│  🏢 Empresas                         │
│  👥 Trabajadores                     │
│  📄 Liquidaciones                    │
│  ⚙️ Parámetros                       │
│                                      │
└──────────────────┬───────────────────┘
                   │
                   ▼
┌──────────────────────────────────────┐
│       💾 Almacenamiento local        │
├──────────────────────────────────────┤
│                                      │
│   base_datos_liquidaciones.json      │
│                                      │
└──────────────────────────────────────┘
```

> 🔐 **Recomendación:** Debido a que el archivo local puede contener información personal y remuneraciones, se recomienda realizar copias de seguridad periódicas y proteger el acceso al equipo.

---

## 🖨️ Exportación de liquidaciones

La aplicación permite generar comprobantes de liquidación preparados para:

- 🖨️ Imprimir.
- 📄 Guardar como PDF.
- 📁 Mantener como respaldo.
- 👤 Entregar al trabajador.

---

## 🧮 Flujo de cálculo

De forma general, una liquidación puede seguir el siguiente proceso:

```text
                    ┌─────────────────────┐
                    │   💰 SUELDO BASE    │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
      ┌──────────────┐ ┌──────────────┐ ┌───────────────┐
      │ Horas Extras │ │ Gratificación│ │Bonos Imponibles│
      └──────┬───────┘ └──────┬───────┘ └───────┬───────┘
             │                │                 │
             └────────────────┼─────────────────┘
                              │
                              ▼
                 ┌─────────────────────────┐
                 │  TOTAL HABERES          │
                 │  IMPONIBLES             │
                 └────────────┬────────────┘
                              │
             ┌────────────────┼─────────────────┐
             │                │                 │
             ▼                ▼                 ▼
       ┌───────────┐    ┌────────────┐    ┌──────────────┐
       │    AFP    │    │   SALUD    │    │   CESANTÍA   │
       └─────┬─────┘    └─────┬──────┘    └──────┬───────┘
             │                │                  │
             └────────────────┼──────────────────┘
                              │
                              ▼
                  ┌────────────────────────┐
                  │ OTROS DESCUENTOS       │
                  │ + IMPUESTO ÚNICO       │
                  └────────────┬───────────┘
                               │
                               ▼
                  ┌────────────────────────┐
                  │  TOTAL DESCUENTOS      │
                  └────────────┬───────────┘
                               │
                               ▼
                  ┌────────────────────────┐
                  │    💵 SUELDO LÍQUIDO   │
                  └────────────────────────┘
```

> 📌 Los componentes específicos deben calcularse utilizando los parámetros legales correspondientes al período de la liquidación.

---

# 🛠️ Tecnologías utilizadas

| Tecnología | Uso |
|---|---|
| 🟧 **HTML5** | Estructura de la interfaz |
| 🎨 **CSS3** | Diseño y estilos |
| 🟨 **JavaScript** | Lógica de la aplicación |
| ⚡ **Electron** | Aplicación de escritorio |
| 🟢 **Node.js** | Entorno de ejecución |
| 📂 **File System (`fs`)** | Persistencia local |
| 📄 **JSON** | Almacenamiento estructurado |

---

# 📋 Requisitos previos

Antes de ejecutar el proyecto debes tener instalado:

- **Node.js**
- **npm**
- Sistema operativo compatible con Electron.

Puedes verificar la instalación ejecutando:

```bash
node --version
npm --version
```

---

# 📦 Instalación

## 1. Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/tu-repositorio.git
```

## 2. Entrar a la carpeta del proyecto

```bash
cd tu-repositorio
```

## 3. Instalar dependencias

```bash
npm install
```

## 4. Ejecutar la aplicación

```bash
npm start
```

La aplicación se abrirá en una ventana de escritorio de Electron.

---

# 🏗️ Empaquetado para Windows

Para generar un ejecutable independiente para Windows puedes utilizar **electron-packager**.

### Usando `npx`

```bash
npx electron-packager . "Liquidaciones" --platform=win32 --arch=x64 --out=dist
```

El ejecutable se generará dentro de:

```text
dist/
│
└── Liquidaciones-win32-x64/
    │
    ├── Liquidaciones.exe
    ├── resources/
    └── ...
```

El archivo principal para iniciar la aplicación será:

```text
Liquidaciones.exe
```

---

# 📁 Estructura del proyecto

Una estructura recomendada para el proyecto es:

```text
Liquidaciones/
│
├── 📁 assets/
│   ├── icons/
│   └── images/
│
├── 📁 css/
│   └── styles.css
│
├── 📁 js/
│   ├── calculos.js
│   ├── empresas.js
│   ├── trabajadores.js
│   ├── liquidaciones.js
│   └── parametros.js
│
├── 📄 index.html
├── 📄 main.js
├── 📄 preload.js
├── 📄 package.json
├── 📄 base_datos_liquidaciones.json
├── 📄 LICENSE
└── 📄 README.md
```

---

# 🗃️ Estructura de datos

El sistema utiliza un archivo JSON local para almacenar la información.

### Empresa

```json
{
  "id": "empresa-001",
  "rut": "76.123.456-7",
  "razonSocial": "Empresa de Ejemplo SpA",
  "direccion": "Santiago, Chile"
}
```

### Trabajador

```json
{
  "id": "trabajador-001",
  "empresaId": "empresa-001",
  "rut": "12.345.678-9",
  "nombre": "Juan Pérez",
  "cargo": "Desarrollador",
  "tipoContrato": "indefinido",
  "fechaIngreso": "2026-01-01",
  "sueldoBase": 1200000,
  "afp": "AFP",
  "salud": {
    "tipo": "fonasa"
  },
  "cargasFamiliares": 0
}
```

### Liquidación

```json
{
  "id": "liq-2026-08-001",
  "empresaId": "empresa-001",
  "trabajadorId": "trabajador-001",
  "periodo": "2026-08",

  "haberes": {
    "sueldoBase": 1200000,
    "horasExtras": 85000,
    "gratificacion": 100000,
    "bonosImponibles": 50000,
    "bonosNoImponibles": 30000
  },

  "descuentos": {
    "afp": 145000,
    "salud": 84000,
    "seguroCesantia": 7200,
    "impuesto": 15000
  },

  "totales": {
    "totalHaberes": 1465000,
    "totalDescuentos": 251200,
    "sueldoLiquido": 1213800
  }
}
```

> ⚠️ Los valores utilizados en este ejemplo son únicamente ilustrativos y **no deben utilizarse para calcular remuneraciones reales**.

---

# ⚙️ Gestión de parámetros

Los parámetros legales pueden asociarse a un período determinado.

Ejemplo:

```json
{
  "parametros": {
    "periodo": "2026-08",

    "utm": 0,

    "ingresoMinimoMensual": 0,

    "seguroCesantia": {
      "trabajador": 0,
      "empleador": 0
    },

    "afp": {},

    "impuestoSegundaCategoria": []
  }
}
```

Mantener los parámetros asociados a un período permite generar liquidaciones históricas utilizando los valores correspondientes a cada mes.

---

# 🔄 Flujo general de la aplicación

```text
┌───────────────────┐
│   🏢 EMPRESAS     │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ 👥 TRABAJADORES   │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ ⚙️ PARÁMETROS     │
│   LEGALES         │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ 🧮 CÁLCULO        │
│ REMUNERACIONES    │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ 📄 LIQUIDACIÓN     │
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ 🖨️ PDF / IMPRESIÓN│
└─────────┬─────────┘
          │
          ▼
┌───────────────────┐
│ 🗄️ HISTORIAL       │
└───────────────────┘
```

---

# 🔐 Seguridad

Aunque la información se almacena localmente, se recomienda implementar buenas prácticas de seguridad.

### Recomendaciones

- Realizar copias de seguridad periódicas.
- Proteger el equipo mediante contraseña.
- No compartir el archivo JSON públicamente.
- Mantener el sistema operativo actualizado.
- Evitar almacenar el archivo de datos dentro del repositorio Git.
- Agregar `base_datos_liquidaciones.json` al `.gitignore`.

Ejemplo:

```gitignore
node_modules/
dist/
base_datos_liquidaciones.json
*.log
.env
```

> 🔒 Si el proyecto será utilizado en producción, se recomienda implementar cifrado o una base de datos local segura en lugar de almacenar información sensible directamente en JSON.

---

# ⚠️ Consideraciones legales

Esta aplicación es una herramienta informática destinada a facilitar la gestión y cálculo de remuneraciones.

Los valores previsionales y tributarios pueden cambiar, por lo que **deben verificarse siempre con la normativa chilena vigente y las fuentes oficiales correspondientes al período de la liquidación**.

Se recomienda validar especialmente:

- Tasas de AFP.
- Cotización de salud.
- Seguro de Cesantía.
- Ingreso Mínimo Mensual.
- UTM.
- Impuesto Único de Segunda Categoría.
- Tramos y factores tributarios.
- Topes imponibles.
- Gratificación legal.
- Horas extraordinarias.
- Cargas familiares.
- Situaciones contractuales especiales.

> ⚠️ Este software no reemplaza la asesoría de un contador, profesional de remuneraciones o especialista tributario.

---

# 🧪 Desarrollo

Para trabajar con el proyecto en modo desarrollo:

```bash
npm install
npm start
```

Después de realizar cambios importantes en el código puede ser necesario reiniciar la aplicación Electron.

---

# 🗺️ Roadmap

Funcionalidades planificadas o posibles mejoras:

- [ ] 📊 Dashboard de remuneraciones.
- [ ] 📄 Exportación masiva a PDF.
- [ ] 📊 Exportación a Excel.
- [ ] 📁 Generación de archivos previsionales.
- [ ] 🕐 Control de asistencia.
- [ ] 🏖️ Gestión de vacaciones.
- [ ] 🏥 Registro de licencias médicas.
- [ ] 📑 Generación de finiquitos.
- [ ] 💼 Centralización de remuneraciones.
- [ ] 💾 Copias de seguridad automáticas.
- [ ] ♻️ Restauración de respaldos.
- [ ] 🔐 Cifrado de información sensible.
- [ ] 👤 Sistema de usuarios.
- [ ] 🔑 Roles y permisos.
- [ ] 🔄 Actualización de parámetros legales.
- [ ] ✍️ Firma electrónica.
- [ ] 📝 Auditoría de modificaciones.
- [ ] 📈 Reportes mensuales y anuales.

---

# 🤝 Contribuciones

Las contribuciones son bienvenidas.

Si quieres colaborar:

### 1. Haz un Fork

Realiza un Fork del proyecto desde GitHub.

### 2. Crea una nueva rama

```bash
git checkout -b feature/nueva-funcionalidad
```

### 3. Realiza tus cambios

Modifica el código y prueba la aplicación.

### 4. Agrega los cambios

```bash
git add .
```

### 5. Crea un commit

```bash
git commit -m "Agrega nueva funcionalidad"
```

### 6. Sube la rama

```bash
git push origin feature/nueva-funcionalidad
```

### 7. Crea un Pull Request

Desde GitHub, crea un Pull Request explicando los cambios realizados.

---

# 📄 Licencia

Este proyecto está bajo la **Licencia MIT**.

Consulta el archivo [`LICENSE`](LICENSE) para conocer los términos completos de la licencia.

---

# 👨‍💻 Autor

Desarrollado con ❤️ para facilitar la gestión de remuneraciones en Chile.

Si este proyecto te resulta útil, considera darle una ⭐ al repositorio.

---

## ⭐ Liquidaciones de Sueldo — Chile

Aplicación de escritorio para administrar:

```text
🏢 Empresas
      │
      ▼
👥 Trabajadores
      │
      ▼
⚙️ Parámetros
      │
      ▼
🧮 Cálculos
      │
      ▼
📄 Liquidaciones
      │
      ▼
🗄️ Historial
```

**Electron + JavaScript + JSON + almacenamiento local**
