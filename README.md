💼 Liquidaciones de Sueldo — App de Escritorio para Chile

Aplicación de escritorio desarrollada con Electron, orientada a la gestión, cálculo y emisión de liquidaciones de sueldo para trabajadores en Chile.

La aplicación permite administrar múltiples empresas, registrar trabajadores, calcular remuneraciones según parámetros previsionales y tributarios, y mantener un historial local de las liquidaciones emitidas.

⚠️ Importante: Los valores previsionales y tributarios pueden cambiar periódicamente. El sistema incluye un panel de parámetros para mantener actualizados los valores legales utilizados en los cálculos.

🚀 Características
🏢 Multiempresa

Administra diferentes empresas desde una única aplicación.

Creación y edición de empresas.
Identificación mediante RUT.
Trabajadores asociados mediante empresaId.
Historial independiente por empresa.
Separación de información para evitar cruces de trabajadores y liquidaciones.
👥 Gestión de Trabajadores

Mantén una ficha completa de cada trabajador.

Datos personales.
RUT.
Cargo.
Tipo de contrato.
Fecha de ingreso.
Sueldo base.
AFP.
Sistema de salud: Fonasa / Isapre.
Cargas familiares.
Bonos.
Horas extras.
Información previsional.
💰 Cálculo de Remuneraciones

El sistema permite automatizar diferentes componentes de una liquidación:

Sueldo base.
Horas extraordinarias.
Gratificación legal.
Bonos imponibles.
Bonos no imponibles.
Descuentos previsionales.
Cotización de salud.
Seguro de cesantía.
Impuesto Único de Segunda Categoría.
Total haberes.
Total descuentos.
Sueldo líquido.
⚙️ Parámetros Legales Actualizables

Incluye un módulo para administrar los valores utilizados en los cálculos.

Entre ellos:

UTM.
Ingreso Mínimo Mensual (IMM).
Tasas AFP.
Seguro de Cesantía.
Valores de salud.
Tramos del Impuesto Único de Segunda Categoría.
Otros parámetros necesarios para el cálculo de remuneraciones.

Esto permite adaptar el sistema cuando cambien los valores legales.

🗄️ Almacenamiento Local

La aplicación funciona con almacenamiento 100% local.

Los datos se almacenan en un archivo:

base_datos_liquidaciones.json


No es necesario contratar servidores ni utilizar una base de datos en la nube.

La información contiene:

Configuraciones
├── Parámetros tributarios
├── Parámetros previsionales
└── Valores legales

Empresas
├── Empresa 1
├── Empresa 2
└── Empresa N

Trabajadores
├── Trabajadores asociados a Empresa 1
├── Trabajadores asociados a Empresa 2
└── Trabajadores asociados a Empresa N

Liquidaciones
├── Historial Empresa 1
├── Historial Empresa 2
└── Historial Empresa N

🖨️ Generación de Liquidaciones

Permite generar comprobantes de remuneraciones preparados para:

🖨️ Impresión.
📄 Guardado como PDF.
📁 Archivo histórico.
👤 Entrega al trabajador.
🛠️ Tecnologías
Tecnología	Uso
HTML5	Estructura de la interfaz
CSS3	Diseño y estilos
JavaScript	Lógica de la aplicación
Electron	Aplicación de escritorio
Node.js	Entorno de ejecución
File System (fs)	Persistencia local
JSON	Almacenamiento estructurado
📋 Requisitos

Antes de comenzar, necesitas tener instalado:

Node.js
npm
Windows, Linux o macOS para desarrollo.

Puedes comprobar la instalación con:

node --version
npm --version

📦 Instalación
1. Clonar el repositorio
git clone https://github.com/tu-usuario/tu-repositorio.git

2. Entrar al proyecto
cd tu-repositorio

3. Instalar dependencias
npm install

4. Ejecutar la aplicación
npm start


La aplicación se abrirá automáticamente en una ventana de escritorio de Electron.

🏗️ Crear ejecutable para Windows

Para generar una versión distribuible para Windows puedes utilizar electron-packager.

Opción 1 — Usando npx
npx electron-packager . "Liquidaciones" \
  --platform=win32 \
  --arch=x64 \
  --out=dist


El resultado se encontrará en:

dist/
└── Liquidaciones-win32-x64/
    ├── Liquidaciones.exe
    ├── resources/
    └── ...


El archivo principal para ejecutar la aplicación será:

Liquidaciones.exe

📁 Estructura sugerida del proyecto
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


💡 Se recomienda separar la lógica de cálculo, persistencia y presentación para facilitar el mantenimiento y las futuras actualizaciones.

🔒 Privacidad y seguridad

La aplicación está diseñada para trabajar con información almacenada localmente.

Los datos de:

Empresas.
Trabajadores.
Remuneraciones.
Liquidaciones.
Parámetros.

se mantienen en el equipo donde está instalada la aplicación.

Sin nube
┌─────────────────────────────┐
│       Aplicación Electron   │
│                             │
│  Empresas                   │
│  Trabajadores               │
│  Liquidaciones              │
│  Parámetros                 │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│ base_datos_liquidaciones    │
│           .json             │
└─────────────────────────────┘


🔐 Recomendación: Debido a que el archivo local puede contener información personal y remuneraciones, se recomienda realizar copias de seguridad y proteger el acceso al equipo.

🧮 Flujo de cálculo

De forma general, una liquidación puede seguir el siguiente flujo:

Sueldo Base
     │
     ├── Horas Extras
     ├── Gratificación
     ├── Bonos Imponibles
     │
     ▼
Total Haberes Imponibles
     │
     ├── AFP
     ├── Salud
     ├── Seguro de Cesantía
     ├── Otros descuentos
     └── Impuesto Único
     │
     ▼
Total Descuentos
     │
     ▼
Sueldo Líquido


Los componentes específicos deben calcularse utilizando los parámetros legales correspondientes al período de la liquidación.

📊 Ejemplo de información almacenada

Un registro de trabajador podría tener una estructura similar a:

{
  "id": "trabajador-001",
  "empresaId": "empresa-001",
  "rut": "12.345.678-9",
  "nombre": "Juan Pérez",
  "cargo": "Desarrollador",
  "tipoContrato": "indefinido",
  "sueldoBase": 1200000,
  "afp": "AFP",
  "salud": {
    "tipo": "fonasa"
  },
  "cargasFamiliares": 0
}


Una liquidación podría mantener una estructura como:

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
    "cesantia": 7200,
    "impuesto": 15000
  },
  "liquido": 1213800
}


Los valores anteriores son únicamente ilustrativos y no deben utilizarse como cálculo legal real.

🔄 Actualización de parámetros

Los parámetros legales deberían asociarse al período correspondiente.

Por ejemplo:

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


Esto permite mantener distintos conjuntos de parámetros por período y facilita la generación de liquidaciones históricas.

⚠️ Consideraciones legales

Esta aplicación es una herramienta informática para facilitar la gestión de remuneraciones.

Los cálculos deben validarse con la normativa chilena vigente y los valores oficiales correspondientes al período de cada liquidación.

Antes de utilizar el software en un entorno productivo, se recomienda verificar especialmente:

Tasas previsionales vigentes.
Valores de AFP.
Cotización de salud.
Seguro de cesantía.
Ingreso Mínimo Mensual.
UTM.
Tramos y factores del Impuesto Único de Segunda Categoría.
Topes imponibles.
Gratificación legal.
Horas extraordinarias.
Situaciones contractuales especiales.
🧪 Desarrollo

Para trabajar en el proyecto durante el desarrollo:

npm install
npm start


Si realizas cambios en el código, reinicia Electron cuando sea necesario para cargar las modificaciones.

📌 Roadmap

Algunas funcionalidades que podrían incorporarse en futuras versiones:

 Dashboard general de remuneraciones.
 Exportación masiva a PDF.
 Exportación a Excel.
 Generación de archivos para procesos previsionales.
 Control de asistencia.
 Registro de vacaciones.
 Registro de licencias.
 Finiquitos.
 Centralización de remuneraciones.
 Copias de seguridad automáticas.
 Restauración de respaldos.
 Cifrado de la base de datos local.
 Sistema de usuarios y permisos.
 Actualización de parámetros legales.
 Firma electrónica.
 Historial de modificaciones.
🤝 Contribuciones

Las contribuciones son bienvenidas.

Si quieres mejorar el proyecto:

# 1. Haz un fork del proyecto

# 2. Crea una rama
git checkout -b feature/nueva-funcionalidad

# 3. Realiza tus cambios

# 4. Guarda los cambios
git add .

# 5. Crea un commit
git commit -m "Agrega nueva funcionalidad"

# 6. Sube la rama
git push origin feature/nueva-funcionalidad

# 7. Abre un Pull Request

📄 Licencia

Este proyecto está disponible bajo la Licencia MIT.

Consulta el archivo LICENSE para conocer los términos completos de la licencia.

👨‍💻 Autor

Desarrollado con ❤️ para facilitar la gestión de remuneraciones en Chile.

Si este proyecto te resulta útil, considera darle una ⭐ al repositorio.

⭐ Proyecto

Liquidaciones de Sueldo — Chile

Aplicación de escritorio para administrar empresas, trabajadores y liquidaciones de sueldo de forma local, organizada y segura.
