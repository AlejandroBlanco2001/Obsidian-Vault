---
tags:
  - arquitectura-de-software
  - modelos-de-ataque
  - seguridad
  - atributos-de-calidad
  - master
---
Recordemos que la definición del atributo de calidad de seguridad es:

> Medida de la habilidad de un sistema para proteger los datos y la información de accesos no autorizados, mientras que garantiza el acceso a la misma por parte de personas y sistemas autorizados para ellos.

Si definimos la *Confidencialidad*, seria:

> Propiedad de un sistema para garantizar que los datos o servicios estan protegidos de accesos no autorizados.

Por otro lado, la *Integridad* seria:

> Propiedad de un sistema para garantizar que los datos o servicios no pueden ser manipulados sin autorización.

Por ultimo, la *Disponibilidad* seria: 

> Propiedad de un sistema para garantizar que estaria disponible para su uso legitimo.

Si quisiéramos saber un listado de los ataques mas conocidos, contamos con ciertas organizaciones que nos ayudan a detectar y observar ciertos ataques comunes como lo son:

- OWASP 10
- CAPEC
- CWE
- CERT

Donde podemos ver ataques como *Inyección, Ruptura de autenticación, XSS, Monitoreo insuficiente, Fallas en el control de acceso...*

Otro modelo planteado por Microsoft, es el modelo STRIDE:

- ***S***poofing: El arquitecto debe identificar requerimientos y tomar decisiones de diseño que prevengan la suplantación de identidad.
- ***T***ampering: El arquitecto debe revisar las decisiones de diseño que prevengan o detecten la manipulación no autorizado de los datos.
- ***R***epudiation: El arquitecto debe revisar las decisiones de diseño que prevengan que un actor del sistema puede negar su participación o responsabilidad en un acción.
- ***I***nformation disclosure: El arquitecto debe revisar las decisiones de diseño que prevengan que un actor del sistema puede suministrar información sensible a personas no autorizadas.
- ***D***enial of Service: El arquitecto debe revisar las decisiones de diseño que prevengan que el sistema se degrade y no sea visto como disponible por los usuarios.
- ***E***levation of privileges: El arquitecto debe revisar las decisiones de diseño que prevengan que un usuario pueda tener permisos no autorizados.

## Spoofing
![[Pasted image 20250226181226.png]]

## Tampering
![[Pasted image 20250226181305.png]]

## Repudiation
![[Pasted image 20250226181326.png]]

## Information disclosure
![[Pasted image 20250226181348.png]]

## Denial of Service
![[Pasted image 20250226181410.png]]

## Elevation of privileges
![[Pasted image 20250226181443.png]]

## Ejemplo de como diagramar un caso

![[Pasted image 20250226181537.png]]