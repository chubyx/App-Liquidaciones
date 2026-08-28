Markdown
# Liquidaciones de Sueldo - App de Escritorio (Chile)

Aplicación de escritorio desarrollada con Electron para la gestión, cálculo y emisión de liquidaciones de sueldo, adaptada a la normativa previsional y tributaria chilena. Permite administrar múltiples empresas, mantener un registro de trabajadores y generar un historial seguro de los pagos mensuales.

## 🚀 Características Principales

*   🏢 **Soporte Multiempresa:** Crea y gestiona diferentes empresas desde una sola interfaz sin mezclar a los trabajadores ni el historial.
*   👥 **Fichas de Trabajadores:** Registro de empleados con cálculo automatizado según su tipo de contrato, AFP, sistema de salud (Fonasa/Isapre), cargas familiares y sueldo base.
*   ⚙️ **Parámetros Actualizables:** Panel de configuración para actualizar valores legales vigentes (UTM, Ingreso Mínimo Mensual, tasas de AFP, Seguro de Cesantía y tramos del Impuesto Único).
*   💰 **Cálculo Automático:** Procesamiento de horas extras, gratificación legal, bonos imponibles/no imponibles, descuentos previsionales e impuesto de segunda categoría.
*   🗄️ **Privacidad y Almacenamiento Local:** Los datos no viajan a la nube. Toda la información se guarda de forma segura en un archivo `base_datos_liquidaciones.json` en el disco duro local.
*   🖨️ **Exportación:** Generación de comprobantes listos para imprimir o guardar como PDF.

## 🛠️ Tecnologías Utilizadas

*   **Frontend:** HTML5, CSS3, JavaScript (Vanilla)
*   **Backend / Contenedor:** [Electron](https://www.electronjs.org/)
*   **Almacenamiento:** File System (`fs`) de Node.js (JSON local)

## 📦 Requisitos Previos

Asegúrate de tener instalado [Node.js](https://nodejs.org/) en tu sistema.

## ⚙️ Instalación y Ejecución Local

1. Clona este repositorio:
   ```bash
   git clone [https://github.com/tu-usuario/tu-repositorio.git](https://github.com/tu-usuario/tu-repositorio.git)
Navega a la carpeta del proyecto:

Bash
cd tu-repositorio
Instala las dependencias necesarias:

Bash
npm install
Ejecuta la aplicación en modo desarrollo:

Bash
npm start
🏗️ Empaquetado (Crear archivo .exe)
Para generar un ejecutable independiente para Windows, puedes usar electron-packager.

Instala el empaquetador globalmente o ejecútalo mediante npx:

Bash
npx electron-packager . "Liquidaciones" --platform=win32 --arch=x64 --out=dist
El ejecutable compilado y listo para distribuir se generará dentro de la carpeta dist/Liquidaciones-win32-x64/.

🔒 Estructura de Datos
La aplicación utiliza un sistema de persistencia local que lee y escribe sobre un archivo físico generado automáticamente (base_datos_liquidaciones.json). Este archivo almacena de forma estructurada:

Configuraciones y parámetros tributarios globales.

Lista de empresas registradas.

Directorio de trabajadores vinculados por empresaId.

Historial inmutable de liquidaciones emitidas.

📄 Licencia
Este proyecto está bajo la Licencia MIT - mira el archivo LICENSE para más detalles.
