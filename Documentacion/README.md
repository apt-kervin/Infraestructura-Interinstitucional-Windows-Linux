# infraestructura-interinstitucional-windows-linux

Red gubernamental simulada con 4 instituciones (INA, MEP, ICE, MICITT): Active Directory, LDAP, DNS/DHCP con failover, web HTTPS, correo, VPN WireGuard y VoIP en Windows Server y Linux.



\# Infraestructura Tecnológica Interinstitucional (Windows y Linux)



Proyecto final del CDT Telemática, Instituto Nacional de Aprendizaje (INA),

módulo Servicios de Red Basados en Windows.



Simula una red gubernamental con cuatro instituciones interconectadas por

routers y switches reales: dos sobre Windows Server y dos sobre Linux.



\## Instituciones



| Institución | Sistema | Dominio | Red |

|---|---|---|---|

| INA | Windows Server | ina.cr | 192.168.10.0/24 |

| ICE | Linux | inicio.ice.cr | 192.168.20.0/24 |

| MEP | Windows Server | mep.cr | 192.168.30.0/24 |

| MICITT | Linux | micitt.cr | 192.168.40.0/24 |



Las sedes se conectan a un backbone con enlaces seriales /30 y un

DNS raíz académico (gob.cr). Cada institución tiene 3 servidores:

infraestructura principal, respaldo y servicios empresariales.



\## Servicios implementados



\*\*Windows (INA y MEP):\*\* Active Directory, DNS y DHCP con respaldo,

relaciones de confianza, IIS, FTP, certificados y correo (Exchange y MailEnable).



\*\*Linux (ICE y MICITT):\*\* OpenLDAP, DNS Bind9 maestro/esclavo, ISC-DHCP con

failover, FTP, Apache/Nginx, certificados SSL/TLS y correo (iRedMail).



\*\*Todas las sedes:\*\* sitios web con HTTPS, VPN client-to-site con WireGuard

para teletrabajo y resolución de nombres entre instituciones.



\*\*Telefonía:\*\* PBX FreeSWITCH con softphones SIP (prueba de concepto en el MEP).



\## Pruebas realizadas



\- Failover: al apagar el servidor principal, el de respaldo tomó el control de DNS y DHCP sin cortes.

\- Autenticación centralizada con usuarios de Active Directory y LDAP.

\- Correo entre dominios con registros MX.

\- Conectividad cruzada: FTP y nslookup entre entornos Windows y Linux.



\## Problemas resueltos



\- DNS entre instituciones: se configuraron reenviadores condicionales hacia el DNS raíz.

\- Exchange: faltaba el registro MX en el servidor principal.

\- LDAP: el usuario debía crearse en el servidor LDAP del correo.

\- VPN sin acceso a la LAN: se agregaron rutas estáticas y reglas NAT en los routers de borde.



\## Documentación



El informe técnico completo con capturas de cada configuración está en

\[`documentacion/`](documentacion/).



\## Tecnologías

Windows Server, Debian/Ubuntu, Active Directory, OpenLDAP, Bind9, ISC-DHCP,

IIS, Apache, Nginx, iRedMail, Exchange, WireGuard, FreeSWITCH, Cisco (routers y switches)

