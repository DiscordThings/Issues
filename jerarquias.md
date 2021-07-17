**¿Qué es una jerarquía de roles?** Una jerarquía de rol es donde el bot comprueba si la función del autor es menor que la función de los objetivos. Por ejemplo, no desea que los moderadores puedan banear a los administradores.

**¿Cómo puedo habilitar la jerarquía de roles?** Compruebe si la función más alta del autor es menor que la función más alta del objetivo. Si es así, devuelve un error.

**¿Por qué debería agregar esto?**
1. Necesita agregar esto para que su bot sea aprobado.
2. Hace que los ayudantes no puedan advertir / silenciar a los administradores, ya que eso no parece correcto.
