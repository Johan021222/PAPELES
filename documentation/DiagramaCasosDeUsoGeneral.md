flowchart TD
    %% ======== ACTORES ========
    A1([Servicio de Notificaciones])
    A2([Administrador])
    A3([Coordinador Académico])
    A4([Coordinador de Infraestructura])
    A5([Profesor])

    %% ======== CASOS DE USO ========
    CU1([Enviar notificaciones de cambios y recordatorios])
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
    CU12([Consultar horarios grupo/profesor/salon])

    CU13([Gestionar salones])
    CU14([Gestionar recursos de salones])
    CU15([Gestionar disponibilidad de salones])

    CU16([Registrar o actualizar disponibilidad de profesor])
    CU17([Consultar mi horario])
    
    CU18([Recibir notificaciones de cambios])

    %% ======== RELACIONES ========
    A1 --> CU1
    CU1 -. "include" .-> CU18

    A2 --> CU2
    A2 --> CU3
    A2 --> CU4
    A2 --> CU5
    A2 --> CU6
    A2 --> CU7
    A2 --> CU8
    A2 --> CU9

    A3 --> CU10
    A3 --> CU11
    A3 --> CU12

    A4 --> CU12
    A4 --> CU13
    A4 --> CU14
    A4 --> CU15

    A5 --> CU16
    A5 --> CU17

    CU10 -. "include" .-> CU18
    CU11 -. "include" .-> CU18
    CU12 -. "include" .-> CU18
    CU15 -. "include" .-> CU18
