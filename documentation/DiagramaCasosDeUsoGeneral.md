# Diagrama de Casos de Uso: Sistema de Asignación de Salones

## Introducción
Este documento presenta el **diagrama general de casos de uso** del Sistema de Asignación de Salones. Su propósito es mostrar todas las interacciones principales entre los actores y el sistema.

## Diagrama General

![Diagrama General](../caso de uso general.png)
 
## Descripción General
El diagrama muestra los siguientes actores:
- **Administrador**
- **Coordinador Académico**
- **Coordinador de Infraestructura**
- **Profesor**
- **Servicio de Notificaciones**

Cada uno interactúa con casos de uso como:
- Gestión de usuarios
- Gestión de roles y permisos
- Resolver conflictos de horario
- Gestionar programas y grupos
- Registrar disponibilidad de profesores
- Ajustar asignación manual
- Ejecutar asignación automática
- Consultar horarios

---

## Código Mermaid (opcional)
Puedes reemplazar este Mermaid con uno real si lo deseas:

```mermaid
flowchart TD
    %% ======== ACTORES ========
    A1([Servicio de Notificaciones])
    A2([Administrador])
    A3([Coordinador Académico])
    A4([Coordinador de Infraestructura])
    A5([Profesor])

    %% ======== CASOS DE USO ========
    CU1([Enviar notificaciones de cambios/recordatorios])
    CU2([Gestionar usuarios])
    CU3([Gestionar roles y permisos])
    CU4([Resolver conflictos de horario])
    CU5([Consultar historial de asignaciones])

    CU6([Configurar parámetros generales])
    CU7([Gestionar programas y grupos])
    CU8([Gestionar asignaturas y grupos-asignatura])
    CU9([Gestionar períodos académicos])

    CU10([Ejecutar asignación automática])
    CU11([Ajustar asignación manual])
    CU12([Consultar horarios (grupo/profesor/salón)])

    CU13([Gestionar salones])
    CU14([Gestionar recursos de salones])
    CU15([Gestionar disponibilidad de salones])

    CU16([Registrar/actualizar disponibilidad de profesor])
    CU17([Consultar mi horario])
    
    CU18([Recibir notificaciones de cambios])

    %% ======== RELACIONES ========
    %% Servicio de Notificaciones
    A1 --> CU1
    CU1 -. include .-> CU18

    %% Administrador
    A2 --> CU2
    A2 --> CU3
    A2 --> CU4
    A2 --> CU5
    A2 --> CU6
    A2 --> CU7
    A2 --> CU8
    A2 --> CU9

    %% Coordinador Académico
    A3 --> CU10
    A3 --> CU11
    A3 --> CU12

    %% Coordinador Infraestructura
    A4 --> CU12
    A4 --> CU13
    A4 --> CU14
    A4 --> CU15

    %% Profesor
    A5 --> CU16
    A5 --> CU17

    %% ======== INCLUDES ========
    CU10 -. include .-> CU18
    CU11 -. include .-> CU18
    CU12 -. include .-> CU18

    CU15 -. include .-> CU18
