# agente-tests

Subagente para [Claude Code](https://docs.claude.com/en/docs/claude-code) que escribe, ejecuta y corrige tests después de cada cambio de código.

## Qué hace

1. Revisa qué ha cambiado (`git diff`, `git status`) y detecta el framework de tests del proyecto.
2. Localiza los tests relacionados y ejecuta primero los relevantes, luego la suite completa.
3. Escribe los tests que falten siguiendo las convenciones del proyecto: casos normales, límites y errores.
4. Ante un fallo, distingue entre bug real (corrige el código) y test incorrecto (corrige el test, explicando por qué).
5. Repite hasta que todo pase y entrega un informe breve.

## Reglas que sigue

- Nunca borra ni desactiva tests para que la suite pase.
- No cambia el comportamiento público del código sin avisar.
- No instala dependencias sin preguntar.

## Supervisión humana

Reviso los tests y las correcciones antes de integrarlos, y decido cuando un cambio afecta al comportamiento público.

## Instalación

Copia `agente-tests.md` en una de estas carpetas:

- `~/.claude/agents/` para usarlo en todos tus proyectos
- `.claude/agents/` dentro de un proyecto concreto

Después aparecerá en `/agents` dentro de Claude Code. Claude lo usará automáticamente tras cambios de código, o puedes pedírselo: *"usa agente-tests para cubrir este cambio"*.

## Licencia

MIT
