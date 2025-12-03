# Diagrama de Flujo de Datos: Sistema de Asignación de Salones

## Introducción
El **Diagrama de Flujo de Datos (DFD)** muestra cómo circula la información dentro del Sistema de Asignación de Salones.  
Este modelo permite visualizar:

- Los actores externos que interactúan con el sistema  
- Los procesos principales  
- Los almacenes de datos utilizados  
- El intercambio de información entre componentes  

El DFD representa una vista general del sistema y complementa al diagrama de casos de uso y al modelo de dominio.

---

## Diagrama General

> Ajusta el nombre del archivo si tu imagen tiene otro nombre.

![Diagrama de Flujo de Datos](../diagrama_flujo_datos.png)

---

# Actores Externos

Los actores que interactúan con los procesos del sistema son:

- **Administrador**
- **Profesor**
- **Coordinador de Infraestructura**
- **Coordinador Académico**
- **Servicio de Notificaciones**

Cada uno ejecuta o recibe información de uno o varios procesos según sus permisos y responsabilidades.

---

# Procesos Principales (P1–P7)

### **P1 – Gestión de Usuarios**
Gestiona cuentas, roles, credenciales y activación de usuarios.  
- Entrada: solicitudes del Administrador  
- Datos: **D1 — Usuarios y roles**

---

### **P2 – Gestión Académica**
Gestiona programas, asignaturas, grupos académicos y carga inicial del semestre.  
- Entrada: Coordinador Académico  
- Datos: **D2 — Programas y grupos**

---

### **P3 – Gestión de Infraestructura**
Controla salones, recursos físicos, disponibilidad y restricciones.  
- Entrada: Coordinador de Infraestructura  
- Datos: **D4 — Salones y recursos**

---

### **P4 – Disponibilidad de Profesores**
Permite registrar, actualizar y consultar disponibilidad docente.  
- Entrada: Profesor  
- Datos: **D3 — Profesores y disponibilidad**

---

### **P5 – Motor de Asignación**
Procesa la información para generar propuestas automáticas de horarios.  
- Usa:
  - **D2 — Programas y grupos**  
  - **D3 — Disponibilidad de profesores**  
  - **D4 — Salones y recursos**  
- Resultado: actualiza **D5 — Asignaciones**

---

### **P6 – Conflictos y Ajustes**
Detecta choques de horario y permite realizar ajustes.  
- Entrada: Coordinador Académico  
- Usa **D5 — Asignaciones**  
- Genera alertas hacia el Servicio de Notificaciones

---

### **P7 – Consultas y Reportes**
Genera reportes y visualizaciones para todos los roles según permisos.  
- Lectura de:
  - D1 Usuarios y roles  
  - D2 Programas y grupos  
  - D3 Disponibilidad profesores  
  - D4 Salones y recursos  
  - D5 Asignaciones  
  - D6 Historial  

---

### **P8 – Notificaciones**
Comunica cambios, alertas y conflictos a los usuarios.  
- Entrada: procesos P5 y P6  
- Actor: **Servicio de Notificaciones**

---

# Almacenes de Datos (D1–D6)

### **D1 – Usuarios y roles**
Credenciales, roles, permisos y estados de usuario.

### **D2 – Programas y grupos**
Modelo académico: programas, cursos, grupos.

### **D3 – Profesores y disponibilidad**
Disponibilidad docente por franja horaria.

### **D4 – Salones y recursos**
Capacidad, tipo, recursos disponibles, ubicación.

### **D5 – Asignaciones**
Asignación de cursos a salón, profesor, franja y período.

### **D6 – Historial**
Registro histórico de asignaciones, modificaciones y auditorías.

---

# Código Mermaid (Opcional)

```mermaid
flowchart LR

    %% Actores
    A1([Administrador])
    A2([Profesor])
    A3([Coordinador Infraestructura])
    A4([Coordinador Académico])
    A5([Servicio de Notificaciones])

    %% Procesos
    P1[[P1: Gestión de usuarios]]
    P2[[P2: Gestión académica]]
    P3[[P3: Gestión infraestructura]]
    P4[[P4: Disponibilidad profesores]]
    P5[[P5: Motor de asignación]]
    P6[[P6: Conflictos y ajustes]]
    P7[[P7: Consultas y reportes]]
    P8[[PB: Notificaciones]]

    %% Almacenes de datos
    D1[(D1: Usuarios y roles)]
    D2[(D2: Programas y grupos)]
    D3[(D3: Profesores y disponibilidad)]
    D4[(D4: Salones y recursos)]
    D5[(D5: Asignaciones)]
    D6[(D6: Historial)]

    %% Flujo
    A1 --> P1 --> D1
    A2 --> P4 --> D3
    A3 --> P3 --> D4
    A4 --> P2 --> D2

    P5 --> D5
    P5 --> P6
    P6 --> D5

    P7 --> D1
    P7 --> D2
    P7 --> D3
    P7 --> D4
    P7 --> D5
    P7 --> D6

    P8 --> A5
    P5 --> P8
    P6 --> P8
