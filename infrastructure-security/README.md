# Infraestructura & Security Engineering

## Objetivo

Esta sección muestra mi base técnica en infraestructura y cómo esa experiencia se conecta con la ciberseguridad, la arquitectura, el riesgo y la continuidad operacional.

Mi trayectoria profesional comenzó en áreas de soporte, redes e infraestructura y posteriormente evolucionó hacia seguridad, cloud security, gestión de riesgos y liderazgo de ciberseguridad.

**Infraestructura y Redes → Seguridad → Cloud Security → Riesgo y Gobierno → CISO**

Esta evolución me permite analizar un control de seguridad no solo desde la política o el cumplimiento, sino también desde su implementación, operación, monitoreo y efecto sobre la disponibilidad del servicio.

---

## Áreas de experiencia técnica

### Sistemas y plataformas

- Linux
- Windows Server
- Active Directory
- Virtualización
- VMware
- Docker
- Administración y hardening de servidores
- Servicios de infraestructura

### Redes y conectividad

- Redes LAN/WAN
- Routing & Switching
- Cisco
- Firewalls
- VPN
- DNS
- Segmentación de redes
- Control de tráfico y exposición
- Network Security

### Cloud e infraestructura moderna

- AWS
- EC2
- S3
- IAM
- Lambda
- CloudTrail
- CloudWatch
- EventBridge
- Arquitecturas híbridas
- Contenedores y servicios cloud

### Seguridad aplicada a infraestructura

- Hardening
- Gestión de vulnerabilidades
- EDR/XDR
- SIEM y monitoreo
- IAM/PAM
- Gestión de accesos privilegiados
- MFA
- Logging y trazabilidad
- Gestión de superficie de ataque
- Segmentación y defensa en profundidad
- Respaldo, recuperación y continuidad

---

# Escenario de referencia

Para demostrar el enfoque sin exponer infraestructura de organizaciones reales, utilizo el siguiente escenario ficticio.

Una empresa mantiene servicios corporativos on-premise y aplicaciones desplegadas en AWS. Los usuarios utilizan Active Directory para servicios internos y existen cargas de trabajo cloud que deben ser consumidas desde Internet y desde la red corporativa.

## Arquitectura conceptual

```text
                         INTERNET
                            |
                     [ DNS / EDGE ]
                            |
                      [ WAF / FW ]
                            |
                    [ Load Balancer ]
                            |
                 +----------+----------+
                 |                     |
          [ Aplicación ]          [ API / Servicio ]
                 |                     |
                 +----------+----------+
                            |
                      [ Datos / DB ]

                            ^
                            |
                  Conectividad segura
                            |
+------------------------------------------------------+
|                RED CORPORATIVA                      |
|                                                      |
|  Usuarios -> AD / Identidad -> Servidores -> Apps   |
|                   |                                  |
|                  PAM                                 |
|                   |                                  |
|          Accesos administrativos                     |
+------------------------------------------------------+

        TELEMETRÍA / LOGS / EDR / SIEM / ALERTAS
                            |
                    OPERACIÓN DE SEGURIDAD
```

Este diagrama no representa una arquitectura corporativa real. Es un escenario de referencia para explicar criterios de diseño y seguridad.

---

## Cómo abordaría esta infraestructura

### 1. Identificar la superficie de ataque

Antes de aplicar controles necesito saber qué puede ser alcanzado desde Internet y desde otras zonas de confianza.

Revisaría principalmente:

- Servicios publicados
- Direcciones y endpoints expuestos
- Puertos y protocolos
- Load Balancers
- APIs
- Reglas de firewall y Security Groups
- DNS público
- Accesos administrativos
- Relaciones de confianza

El objetivo es responder una pregunta básica:

> **¿Cuáles son las puertas de entrada a la organización y qué protege cada una?**

### 2. Reducir exposición innecesaria

Un activo no debería estar publicado simplemente porque técnicamente puede estarlo.

Aplicaría principios como:

- Exponer únicamente servicios necesarios
- Evitar reglas de acceso excesivamente amplias
- Segmentar servicios según función y criticidad
- Separar administración de tráfico de usuarios
- Mantener bases de datos y componentes internos fuera de exposición directa cuando sea posible
- Utilizar controles perimetrales apropiados al riesgo

### 3. Controlar identidad y privilegios

La identidad es uno de los principales planos de control de una infraestructura moderna.

El modelo debería considerar:

**Usuario → Autenticación → MFA → Rol → Privilegio → Sesión → Registro → Revisión**

Para accesos administrativos privilegiaría permisos temporales o Just-in-Time cuando el escenario lo permita, reduciendo privilegios permanentes.

### 4. Proteger servidores y endpoints

Los controles preventivos deben complementarse con capacidad de detección.

Consideraría:

- Hardening
- Gestión de parches
- Gestión de vulnerabilidades
- EDR/XDR
- Control de cuentas privilegiadas
- Restricción de servicios innecesarios
- Logging
- Monitoreo de integridad y comportamiento

### 5. Centralizar visibilidad

Una infraestructura que no genera evidencia suficiente es difícil de defender.

La telemetría relevante debe permitir reconstruir eventos y detectar comportamientos anómalos.

```text
Firewall ──────┐
Cloud ─────────┤
Active Directory ─┤
Servidores ────┤
EDR/XDR ───────┤──> SIEM / Correlación ──> Alerta ──> Investigación
Aplicaciones ──┤
IAM/PAM ───────┘
```

### 6. Diseñar para recuperación

La arquitectura de seguridad también debe considerar qué ocurre cuando un control falla o un servicio queda indisponible.

Por eso infraestructura, seguridad y continuidad deben trabajar de forma integrada sobre:

- Backups
- Recuperación
- RTO/RPO
- Dependencias tecnológicas
- Redundancia
- DRP
- Pruebas de recuperación
- Gestión de crisis

---

# De infraestructura a riesgo de negocio

Mi forma de analizar infraestructura busca conectar cada decisión técnica con su consecuencia operacional.

| Situación técnica | Riesgo | Control esperado | Impacto de negocio |
|---|---|---|---|
| Servicio innecesariamente expuesto | Mayor superficie de ataque | Reducir exposición / segmentar | Menor probabilidad de compromiso |
| Privilegios administrativos permanentes | Abuso o compromiso de cuentas | PAM / MFA / JIT / mínimo privilegio | Menor riesgo sobre sistemas críticos |
| Vulnerabilidades sin priorización | Explotación de activos relevantes | Priorización basada en riesgo | Reducción del riesgo explotable |
| Logs distribuidos o insuficientes | Baja capacidad de detección | Centralización / SIEM | Menor tiempo de detección y respuesta |
| Recuperación no probada | Interrupción prolongada | BCP / DRP / pruebas | Mayor resiliencia operacional |

---

## Principio de trabajo

> **Una infraestructura segura no es aquella que tiene más herramientas, sino aquella donde se conoce qué existe, qué está expuesto, quién puede acceder, qué riesgo representa, qué control lo protege y cómo se recupera cuando algo falla.**

---

## Alcance y confidencialidad

Todo el contenido de esta sección es demostrativo y utiliza escenarios genéricos.

No contiene IP, dominios, nombres de servidores, reglas de firewall, vulnerabilidades, diagramas, clientes, configuraciones ni información de infraestructura perteneciente a organizaciones reales en las que he trabajado.
