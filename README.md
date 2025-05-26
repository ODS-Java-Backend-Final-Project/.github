# Board Game Meetup Backend

## Project Description
Este proyecto es el backend de una aplicación para organizar quedadas de juegos de mesa. La arquitectura está basada en microservicios, permitiendo una escalabilidad y mantenimiento eficientes.

## Microservices
- **Board-Game Service**: Gestiona la información sobre los juegos de mesa.
- **Events Service**: Gestiona los eventos y quedadas de juegos de mesa.
- **Gateway**: Actúa como punto de entrada único para las solicitudes de los clientes.
- **Discovery Server**: Utiliza Eureka para el descubrimiento de servicios.

## Communication
Los microservicios se comunican entre sí utilizando Feign para realizar llamadas HTTP.

## UML Diagrams
Incluye diagramas UML para visualizar la estructura y relaciones entre los componentes del sistema.

## Setup Steps for Local Development
1. Clona el repositorio:
   ```bash
   git clone <URL_DEL_REPOSITORIO>
   ```
