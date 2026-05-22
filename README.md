# Proyecto-M-dulo-Redes-Locales---lvaro-Gonz-lez
Proyecto Intermodular · 1.º SMR · Curso 2025–2026

¿De qué trata este módulo?

Este módulo forma parte del Proyecto Intermodular del Ciclo Formativo de Grado Medio en Sistemas Microinformáticos y Redes (SMR). Corresponde al módulo Redes Locales (código 0224) de 1.º curso.

El objetivo es diseñar la red de área local (LAN) de una pequeña empresa, incluyendo:

Análisis de necesidades
Diseño de la topología de red
Elección de dispositivos
Plan de direccionamiento IP
Servicios de red
Configuración y diagnóstico básico

Todo el proyecto está aplicado a la empresa TechOficina S.L., utilizada también en el resto de módulos del Proyecto Intermodular.

La empresa: TechOficina S.L.
Campo	Datos
Nombre	TechOficina S.L.
Actividad	Soporte y mantenimiento informático para pequeños negocios
Ubicación	Calle Mayor 14, 2.º A — 28013 Madrid
Instalaciones	1 planta (~120 m²)
Empleados	6 personas
Zonas de red	Área técnica, administración y sala de servidores
Dispositivos	4 PCs, 2 portátiles, NAS, impresora, router, switch y punto Wi-Fi
Documentos creados
1. 07_Redes_Locales.docx — Documento principal

Documento Word con el desarrollo completo del módulo, organizado en siete secciones:

Sección	Contenido
1. Contexto de la empresa	Descripción general y distribución física
2. Análisis de necesidades	Equipos y requisitos identificados
3. Diseño de la red	Topología, dispositivos y cableado
4. Direccionamiento IP	Plan IP y tipos de asignación
5. Servicios de red	Internet, archivos, impresoras y Wi-Fi
6. Configuración y diagnóstico	Comandos y comprobaciones de red
7. Conclusión	Resumen y valoración de la solución
2. 08_Direccionamiento_IP_Red.xlsx — Tablas de red

Libro de Excel compuesto por cinco hojas:

Hoja	Contenido
Plan Direccionamiento IP	Tabla completa de dispositivos e IPs
Parámetros de Red	Explicación de conceptos de red
Tabla ARP Simulada	Ejemplo de salida del comando arp -a
Comandos Diagnóstico	Referencia rápida de comandos
Checklist Verificación	Lista de comprobaciones de funcionamiento
Diseño de red
Topología utilizada

La red utiliza una topología en estrella con un switch gestionable como dispositivo central.

Todos los equipos cableados se conectan al switch, mientras que:

El switch se conecta al router
El router proporciona acceso a Internet
El punto de acceso Wi-Fi conecta dispositivos inalámbricos
Dispositivos de red
ID	Dispositivo	Modelo	Función
RT-001	Router / Firewall	Mikrotik hEX S	NAT, DHCP y acceso a Internet
SW-001	Switch gestionable	TP-Link TL-SG1016DE	Conexión de equipos y VLANs
AP-001	Punto de acceso Wi-Fi	TP-Link EAP225	Red inalámbrica WPA3
SAI-001	SAI / UPS	APC Back-UPS 600 VA	Protección eléctrica
Diagrama simplificado de la red
INTERNET
    │
  RT-001 (192.168.10.1)
  Router Mikrotik
    │
  SW-001
  Switch 16 puertos
    ├── PC-001  (192.168.10.11)  Carlos — Gerencia
    ├── PC-002  (192.168.10.12)  María — Técnica Senior
    ├── PC-003  (192.168.10.13)  Luis — Técnico Junior
    ├── PC-004  (192.168.10.14)  Pedro — Administración
    ├── SRV-001 (192.168.10.20)  NAS Synology
    ├── IMP-001 (192.168.10.30)  Impresora HP
    └── AP-001  (192.168.10.5)
              ├── LT-001 (192.168.10.51)
              └── LT-002 (192.168.10.52)
Plan de direccionamiento IP
Tabla de dispositivos
ID	Dispositivo	Dirección IP	Tipo
RT-001	Router Mikrotik	192.168.10.1	Estática
SW-001	Switch TP-Link	192.168.10.2	Estática
AP-001	Punto Wi-Fi	192.168.10.5	Estática
SRV-001	NAS Synology	192.168.10.20	Estática
IMP-001	Impresora HP	192.168.10.30	Estática
PC-001	Carlos López	192.168.10.11	DHCP + reserva
PC-002	María García	192.168.10.12	DHCP + reserva
PC-003	Luis Torres	192.168.10.13	DHCP + reserva
PC-004	Pedro Sánchez	192.168.10.14	DHCP + reserva
LT-001	Portátil María	192.168.10.51	DHCP dinámica
LT-002	Portátil Luis	192.168.10.52	DHCP dinámica
Parámetros generales de red
Parámetro	Valor
Red	192.168.10.0/24
Máscara	255.255.255.0
Broadcast	192.168.10.255
Gateway	192.168.10.1
DNS principal	8.8.8.8
DNS alternativo	1.1.1.1
Rango DHCP libre
192.168.10.50 – 192.168.10.150
Servicios de red implementados
Acceso a Internet

El router Mikrotik realiza:

NAT para salida a Internet
Asignación DHCP
Funciones básicas de firewall

Las conexiones entrantes no autorizadas quedan bloqueadas.

Compartición de archivos

El servidor NAS Synology utiliza el protocolo SMB para compartir carpetas en red.

Carpetas compartidas
\\192.168.10.20\Documentos_Empresa
\\192.168.10.20\Fichas_Clientes
\\192.168.10.20\Backups
\\192.168.10.20\Administracion
Permisos aplicados
Carpeta	Acceso
Documentos_Empresa	Todos los usuarios
Fichas_Clientes	Solo técnicos
Backups	Escritura automática
Administracion	Carlos y Pedro
Impresora en red

La impresora utiliza IP fija:

192.168.10.30

Todos los equipos pueden imprimir directamente sin depender de otro PC.

Gestión de usuarios en el NAS

Se han definido los siguientes grupos:

Administradores
Técnicos
Administración
Becario

Cada grupo dispone de permisos específicos según sus necesidades.

Copias de seguridad
Estrategia 3-2-1 aplicada
Tipo	Destino
Diaria	PCs → NAS
Semanal	NAS → Disco externo
Continua	OneDrive / Microsoft 365
Red Wi-Fi
Redes inalámbricas configuradas
SSID	Uso
TechOficina-Corp	Empleados
TechOficina-Guest	Invitados
Seguridad aplicada
WPA3 en red corporativa
Red de invitados aislada de la LAN interna
Comandos básicos de diagnóstico
Verificación de conectividad
ping 127.0.0.1
ping 192.168.10.1
ping 192.168.10.20
ping 8.8.8.8
ping www.google.com
Configuración de red
ipconfig /all
Tabla ARP
arp -a
Trazado de ruta
tracert 8.8.8.8
Renovación de DHCP
ipconfig /release
ipconfig /renew
Conclusión

Durante este módulo se ha diseñado una red local funcional para una pequeña empresa, aplicando conceptos fundamentales de redes y administración básica.

La solución propuesta proporciona:

Conectividad estable
Organización eficiente de dispositivos
Seguridad básica de red
Compartición de recursos
Acceso controlado a servicios

El proyecto también permite practicar tareas habituales en entornos reales:

Diseño de redes LAN
Configuración IP
Gestión de dispositivos
Diagnóstico y resolución de problemas
Seguridad y copias de seguridad

Autor:

Álvaro González
