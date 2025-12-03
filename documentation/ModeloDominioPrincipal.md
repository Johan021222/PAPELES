# Modelo de Dominio Principal: Sistema de Asignación de Salones

## Introducción
El **modelo de dominio principal** representa las entidades fundamentales del Sistema de Asignación de Salones y las relaciones necesarias para gestionar correctamente:

- Usuarios, roles y permisos  
- Profesores y su disponibilidad  
- Programas, grupos y asignaturas  
- Períodos académicos  
- Salones y recursos  
- TimeSlots (franjas horarias)  
- Asignaciones académicas  
- Detección y registro de conflictos de horario  

Este diagrama sirve como base conceptual para la base de datos y la lógica del sistema.

---

## Diagrama del Modelo de Dominio

> Ajusta el nombre si tu imagen tiene otro nombre.

![Modelo de dominio principal](../modelo_dominio_principal.png)

---

## Descripción de Entidades

### **Usuario**
Entidad que representa a un usuario del sistema.  
Atributos principales:
- `id`, `nombre`, `email`, `passwordHash`, `activo`

### **Rol**
Define permisos y capacidades dentro del sistema.  
- `id`, `nombre`

### **UsuarioRol**
Permite que un usuario tenga uno o varios roles.  
- `usuario_id`, `rol_id`

### **Programa**
Programas académicos (carreras o áreas).  
- `id`, `nombre`, `facultad`

### **Asignatura**
Materia impartida dentro de un programa.  
- `id`, `codigo`, `nombre`, `creditos`

### **Grupo**
Grupos de estudiantes asociados a un programa.  
- `id`, `codigo`, `semestre`, `numEstudiantes`, `programa_id`

### **GrupoAsignatura**
Relación entre grupos y asignaturas.  
- `id`, `grupo_id`, `asignatura_id`

### **Profesor**
Representa a los docentes del sistema.  
- `id`, `usuario_id`, `codigo`, `titulo`, `tipoContratacion`

### **DisponibilidadProfesor**
Registro de las franjas horarias disponibles para dictar clase.  
- `id`, `profesor_id`, `diaSemana`, `horaInicio`, `horaFin`, `jornada`

### **PeriodoAcademico**
Rango de fechas donde se realiza la programación de horarios.  
- `id`, `nombre`, `fechaInicio`, `fechaFin`

### **TimeSlot**
Franja de tiempo asignable a un curso.  
- `id`, `diaSemana`, `horaInicio`, `horaFin`, `jornada`

### **Salon**
Salón o espacio físico donde se imparten clases.  
- `id`, `codigo`, `capacidad`, `tipo`, `ubicacion`

### **Recurso**
Equipos disponibles (video beam, PC, sonido, etc.).  
- `id`, `nombre`

### **SalonRecurso**
Relación muchos-a-muchos entre salón y recursos.  
- `salon_id`, `recurso_id`

### **Asignacion**
Vincula grupo, profesor, salón, franja temporal y período académico.  
- `id`, `grupoAsignatura_id`, `profesor_id`, `salon_id`, `timeSlot_id`, `periodo_id`, `estado`

### **ConflictoHorario**
Registra choques de horario o restricciones incumplidas.  
- `id`, `tipoConflicto`, `descripcion`

---

## Relaciones Principales

- Un **Usuario** puede ser o no un **Profesor** (1–0..1)  
- Un usuario puede tener **varios Roles** (1–0..*)  
- Un **Programa** tiene múltiples **Grupos** (1–0..*)  
- Un **Grupo** puede tener varias **Asignaturas** (relación muchos-a-muchos)  
- Un **Profesor** tiene múltiples bloques de **Disponibilidad** (1–0..*)  
- Un **TimeSlot**, un **Salón** y un **Profesor** pueden estar asociados a múltiples **Asignaciones**  
- Un **Salón** puede tener múltiples **Recursos** (muchos-a-muchos)  
- Una **Asignación** puede generar múltiples **Conflictos de Horario**

---

## Modelo en Mermaid (opcional)

```mermaid
classDiagram
    class Usuario {
        +int id
        +string nombre
        +string email
        +string passwordHash
        +bool activo
    }

    class Rol {
        +int id
        +string nombre
    }

    class UsuarioRol {
        +int usuario_id
        +int rol_id
    }

    class Programa {
        +int id
        +string nombre
        +string facultad
    }

    class Asignatura {
        +int id
        +string codigo
        +string nombre
        +int creditos
    }

    class Grupo {
        +int id
        +string codigo
        +int semestre
        +int numEstudiantes
        +int programa_id
    }

    class GrupoAsignatura {
        +int id
        +int grupo_id
        +int asignatura_id
    }

    class Profesor {
        +int id
        +int usuario_id
        +string codigo
        +string titulo
        +string tipoContratacion
    }

    class DisponibilidadProfesor {
        +int id
        +int profesor_id
        +string diaSemana
        +time horaInicio
        +time horaFin
        +string jornada
    }

    class PeriodoAcademico {
        +int id
        +string nombre
        +date fechaInicio
        +date fechaFin
    }

    class TimeSlot {
        +int id
        +string diaSemana
        +time horaInicio
        +time horaFin
        +string jornada
    }

    class Salon {
        +int id
        +string codigo
        +int capacidad
        +string tipo
        +string ubicacion
    }

    class Recurso {
        +int id
        +string nombre
    }

    class SalonRecurso {
        +int salon_id
        +int recurso_id
    }

    class Asignacion {
        +int id
        +int grupoAsignatura_id
        +int profesor_id
        +int salon_id
        +int timeSlot_id
        +int periodo_id
        +string estado
    }

    class ConflictoHorario {
        +int id
        +string tipoConflicto
        +string descripcion
    }

    Usuario "1" --> "0..1" Profesor
    Usuario "1" --> "0..*" UsuarioRol
    Rol "1" --> "0..*" UsuarioRol

    Programa "1" --> "0..*" Grupo
    Grupo "1" --> "0..*" GrupoAsignatura
    Asignatura "1" --> "0..*" GrupoAsignatura

    Profesor "1" --> "0..*" DisponibilidadProfesor

    PeriodoAcademico "1" --> "0..*" Asignacion
    TimeSlot "1" --> "0..*" Asignacion
    Salon "1" --> "0..*" Asignacion
    GrupoAsignatura "1" --> "0..*" Asignacion
    Profesor "1" --> "0..*" Asignacion

    Salon "1" --> "0..*" SalonRecurso
    Recurso "1" --> "0..*" SalonRecurso

    Asignacion "1" --> "0..*" ConflictoHorario
