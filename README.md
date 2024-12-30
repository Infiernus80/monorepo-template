# Monorepo con Turborepo: Next.js y NestJS

<p align="center">
    <a href="https://nextjs.org/">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 180 180" width="110"><mask height="180" id=":r8:mask0_408_134" maskUnits="userSpaceOnUse" width="180" x="0" y="0" style="mask-type: alpha;"><circle cx="90" cy="90" fill="black" r="90"></circle></mask><g mask="url(#:r8:mask0_408_134)"><circle cx="90" cy="90" data-circle="true" fill="black" r="90"></circle><path d="M149.508 157.52L69.142 54H54V125.97H66.1136V69.3836L139.999 164.845C143.333 162.614 146.509 160.165 149.508 157.52Z" fill="url(#:r8:paint0_linear_408_134)"></path><rect fill="url(#:r8:paint1_linear_408_134)" height="72" width="12" x="115" y="54"></rect></g><defs><linearGradient gradientUnits="userSpaceOnUse" id=":r8:paint0_linear_408_134" x1="109" x2="144.5" y1="116.5" y2="160.5"><stop stop-color="white"></stop><stop offset="1" stop-color="white" stop-opacity="0"></stop></linearGradient><linearGradient gradientUnits="userSpaceOnUse" id=":r8:paint1_linear_408_134" x1="121" x2="120.799" y1="54" y2="106.875"><stop stop-color="white"></stop><stop offset="1" stop-color="white" stop-opacity="0"></stop></linearGradient></defs></svg>
    </a>
    <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

Este proyecto utiliza **Turborepo** para manejar un monorepo con dos aplicaciones principales:

- **Cliente**: Una aplicación frontend desarrollada con Next.js.
- **API**: Un backend construido con NestJS.

## Estructura del Proyecto

```
.
├── apps
│   ├── client   # Aplicación frontend (Next.js)
│   └── api      # Aplicación backend (NestJS)
├── packages      # Paquetes compartidos (configuración y utilidades)
│   ├── eslint-config
│   └── typescript-config
├── turbo.json    # Configuración de Turborepo
├── package.json  # Scripts del monorepo
```

## Requisitos Previos

Asegúrate de tener instalados:

- Node.js (versión 18 o superior)
- npm (versión 7 o superior)
- Turborepo (versión 2.3.3)

## Instalación

1. Clona el repositorio:

   ```bash
   git clone https://github.com/Infiernus80/monorepo-template.git
   cd monorepo-template
   ```

2. Instala las dependencias:
   ```bash
   npm install
   ```

## Scripts Disponibles

### Monorepo

- `npm run dev`: Inicia el cliente y la API en modo desarrollo.
- `npm run build`: Construye el cliente y la API.
- `npm run lint`: Ejecuta el linter en todo el monorepo.

### Cliente (Next.js)

Ubicado en `apps/client`:

- `npm run dev`: Inicia el servidor de desarrollo de Next.js.
- `npm run build`: Construye la aplicación para producción.
- `npm run start`: Inicia el servidor en modo producción.

### API (NestJS)

Ubicado en `apps/api`:

- `npm run dev`: Inicia el servidor NestJS en modo desarrollo.
- `npm run build`: Construye la API para producción.
- `npm run start`: Inicia el servidor en modo producción.

## Configuración de Turborepo

El archivo `turbo.json` gestiona las tareas del monorepo. La configuración principal incluye:

```json
{
  "tasks": {
    "dev": {
      "cache": false
    },
    "build": {
      "dependsOn": ["^build"],
      "outputs": [".next/**", "dist/**"]
    },
    "lint": {
      "outputs": []
    }
  }
}
```

## Puertos por Defecto

- Cliente (Next.js): `http://localhost:3000`
- API (NestJS): `http://localhost:5000`

**Nota**: Si algún puerto está en uso, Next.js cambiará automáticamente a otro puerto.

## Notas Adicionales

- **Tailwind CSS**: Configurado en el cliente para estilos rápidos y consistentes.
- **CORS**: Habilitado en la API para permitir comunicación entre cliente y servidor.

## Solución de Problemas

### El cliente o la API no se inician correctamente

1. Asegúrate de que los scripts `dev` están definidos en `package.json` de ambas aplicaciones.
2. Verifica que los puertos configurados no estén ocupados.

### Actualizaciones de Dependencias

Mantén las versiones de las dependencias actualizadas en los paquetes compartidos y en las aplicaciones individuales.

## Contribuciones

1. Haz un fork del repositorio.
2. Crea una rama para tu funcionalidad: `git checkout -b feature/nueva-funcionalidad`.
3. Realiza un pull request una vez que esté listo.

## Licencia

Este proyecto está licenciado bajo [MIT](LICENSE).
