# Diagrama de Casos de Uso: Sistema de Asignación de Salones

## Introducción
Este diagrama de casos de uso representa el funcionamiento general del **Sistema de Asignación de Salones**, mostrando cómo interactúan los principales actores con las funcionalidades del sistema.  
Su propósito es brindar una vista clara y estructurada del flujo de operaciones relacionadas con:

- Gestión de usuarios y roles  
- Gestión académica (grupos, programas, asignaturas)  
- Gestión de profesores y su disponibilidad  
- Gestión de salones y recursos  
- Asignación automática y manual  
- Consulta de horarios  
- Notificaciones  
- Resolución de conflictos  

---

## Diagrama General

![Diagrama General](../caso%20de%20uso%20general.png)

---

## Descripciones de Casos de Uso

A continuación se presenta una descripción general de los principales casos de uso del sistema, organizados por épicas.

### **Épica 1: Usuarios y Autenticación**
- **UC1:** Crear/Gestionar cuentas  
- **UC2:** Iniciar sesión  

### **Épica 2: Grupos**
- **UC3:** Registrar/Editar grupos  

### **Épica 3: Salones**
- **UC5:** Registrar/Gestionar salones  
- **UC6:** Configurar disponibilidad de salones  

### **Épica 4: Profesores**
- **UC7:** Registrar/Gestionar profesores  
- **UC8:** Registrar o actualizar disponibilidad  

### **Épica 5: Asignación Automática**
- **UC9:** Ejecutar asignación automática  
- **UC10:** Configurar parámetros  

### **Épica 6: Asignación Manual**
- **UC11:** Ajustar asignación manual  
- **UC12:** Detectar y visualizar conflictos  

### **Épica 7: Visualización de Información**
- **UC13:** Consultar horario semestral  
- **UC14:** Consultar horario personal  
- **UC15:** Generar reportes  

### **Épica 8: Gestión de Conflictos**
- **UC16:** Registrar conflicto  
- **UC17:** Establecer restricciones  

### **Épica 9: Historial y Auditoría**
- **UC18:** Consultar historial de asignaciones  

---

## Roles del Sistema

Los actores principales que participan en el sistema son:

- **Administrador**  
- **Coordinador Académico**  
- **Coordinador de Infraestructura**  
- **Profesor**  
- **Servicio de Notificaciones**

Cada uno accede a un conjunto específico de funcionalidades según sus permisos.

---

## Código Mermaid (Opcional)

```mermaid
flowchart TD
    A1([Servicio de Notificaciones])
    A2([Administrador])
    A3([Coordinador Académico])
    A4([Coordinador de Infraestructura])
    A5([Profesor])

    CU1([Enviar notificaciones])
    CU2([Gestionar usuarios])
    CU3([Gestionar roles y permisos])
    CU4([Resolver conflictos])
    CU5([Consultar historial])

    CU10([Asignación automática])
    CU11([Ajustar asignación manual])
    CU12([Consultar horarios])

    CU16([Registrar disponibilidad])
    CU17([Consultar horario personal])

    A1 --> CU1
    A2 --> CU2
    A2 --> CU3
    A2 --> CU4
    A2 --> CU5
    A3 --> CU10
    A3 --> CU11
    A4 --> CU12
    A5 --> CU16
    A5 --> CU17
