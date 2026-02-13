# Plataforma competitiva para Operation 7 Latino (propuesta)

## Visión
Crear una plataforma competitiva tipo Faceit/ESEA para Operation 7 Latino: matchmaking competitivo, ranking y clanes, grabación de partidas, anticheat básico para Windows 11 y un dashboard web para administración y seguimiento.

## Objetivo
Ofrecer un entorno competitivo confiable sin hacks, con herramientas para detección básica de trampas, almacenamiento de evidencia y un sistema de reputación y ranking para la comunidad latinoamericana de OP7.

## Componentes principales
- Cliente de escritorio (Windows 11)
- Sistema anticheat (MVP realista)
- Backend + API
- Web (ranking, clanes, estadísticas)
- Sistema de grabación de partidas
- Matchmaking y ELO

## Realismo técnico — niveles de alcance
- **Nivel 1 (MVP, viable)**: detección de procesos conocidos de cheat, integridad del cliente, launcher obligatorio, grabación de partidas, subida de logs.
- **Nivel 2 (intermedio)**: driver en kernel, memory scanning, anti-debug, detección de overlays (más complejo y con riesgos legales).
- **Nivel 3 (pro)**: kernel + heurística con ML, detección comportamental y anti-VM (requiere equipo dedicado).

Recomendación: empezar por Nivel 1 para validar producto y comunidad.

## Arquitectura propuesta

### 1. Cliente de escritorio (Windows)
- **Tecnologías sugeridas**: C# .NET 8 + WPF (ideal). Rust o Electron son alternativas (Electron no apto para anticheat).
- **Funciones**: login, lanzar el juego, verificar integridad, monitor de procesos, grabar partidas, enviar logs.
- **Módulos**: 
  - Launcher
  - Monitor de procesos
  - Recorder
  - Anticheat básico
  - Telemetría

### 2. Backend
- **Stack sugerido**: Kotlin + Spring Boot (arquitectura hexagonal), PostgreSQL, Redis.
- **Servicios**: 
  - Auth service
  - Users service
  - Match service (ELO)
  - Clan service
  - Anticheat service (recibe logs y marca sospechosos)
  - Replay service
  - Admin panel

### 3. Web
- **Frameworks**: Next.js / React (preferible)
- **Secciones**: ranking global, clanes, perfil jugador, historial, reportes, leaderboard.

## Diseño del anticheat (MVP realista)
No intentar kernel desde el inicio. MVP recomendado:
1. **Detección de procesos**: lista negra, hashes de ejecutables, rutas sospechosas.
2. **Detección de inyección DLL** y procesos hookeados.
3. **Integridad del juego**: validar archivos mediante launcher obligatorio.
4. **Grabación automática**: integración con OBS o recorder embebido, captura a 720p, subida al servidor.
5. **Sistema de confianza**: score del jugador, reportes y historial para decisiones manuales/automáticas.

## Roadmap por fases

### Fase 1 — Validación (1–2 meses)
- Landing page
- Discord comunidad
- Encuestas a jugadores
- Lista de interesados
- Mockups UI

### Fase 2 — MVP competitivo (3–4 meses)
- Login
- Ranking
- Clanes
- Launcher básico
- Subir resultados manuales

### Fase 3 — Anticheat básico (3 meses)
- Cliente Windows con monitor de procesos
- Logs
- Grabación automática
- Backend de análisis

### Fase 4 — Matchmaking real
- Colas
- ELO
- Servidores dedicados

### Fase 5 — Anticheat avanzado
- Heurística
- Detección por patrones
- IA/ML

## Stack recomendado
- **Cliente Windows**: C# (.NET 8) + WPF
- **Backend**: Kotlin + Spring Boot
- **DB**: PostgreSQL, Redis
- **Infra**: AWS/GCP, S3 para videos, WebSockets para telemetría en tiempo real
- **Web**: Next.js + React

## Modelo de negocio (futuro)
- Suscripción premium
- Torneos pagos
- Skins
- Sponsors

## Riesgos legales y privacidad
- Escaneo de procesos e inspección del sistema conllevan riesgos legales y de privacidad.
- Requerir consentimiento claro en el launcher y Términos de Uso.
- Evitar técnicas intrusivas sin asesoría legal; documentar claramente qué datos se recogen y por qué.

## Preguntas clave (para definir alcance)
1. ¿Quieres hacerlo solo o en equipo? Esto define ritmo y alcance.
2. ¿Objetivo: hobby, proyecto real o startup?
3. ¿Cuántos jugadores activos tiene OP7 Latino hoy?
4. ¿Tienes comunidad o contactos iniciales?
5. ¿Te interesa programar el anticheat tú mismo?
6. ¿Qué nivel quieres alcanzar (MVP simple / competitivo serio / Faceit real)?
7. ¿Tiempo disponible semanal?

## Opinión rápida
Este es un proyecto fuerte y viable si se evita intentar hacer el anticheat profesional desde el día 1. Priorizar comunidad, ranking, launcher y grabación dará tracción y evidencia para invertir en seguridad avanzada.

## Siguiente paso
Dime qué nivel de seriedad quieres (hobby / proyecto real / startup competitiva) y si quieres que lo enfoquemos tipo Faceit real para OP7 Latino. Puedo preparar:
- Arquitectura técnica completa
- Diagrama de componentes
- Modelo de datos
- Roadmap detallado por semanas
- Diseño del cliente Windows y pasos del anticheat MVP

---

*Documento generado como propuesta inicial para orientar el desarrollo y priorización del proyecto.*
