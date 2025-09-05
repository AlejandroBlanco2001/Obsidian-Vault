---
tags:
  - cloud
  - master
---
Los modelos de computación fueron evolucionando con el paso del tiempo de la siguiente manera:
1. *On-Premise* -> *Control total* sobre la plataforma
2. *IaaS* -> Nacimiento de la *virtualization y maquinas virtuales* 
3. *PaaS* ->Ambientes *preparados y auto-gestionados*
4. *CaaS* -> Herramientas como *contenedores*, *K8S* y nace *IaC* (Infrastructure as Code) 

![[Pasted image 20250904215846.png]]

Una arquitectura orientada sin servidores (server-less) es donde tenemos servidores, sin embargo, no nos hacemos cargo de esas preocupaciones sino que le dejamos esas necesidades dinámicas a nuestro proveedor.

![[Pasted image 20250904220031.png]]

Gracias a esto nace *FaaS* (Functions as a Service) donde no buscamos construir un sistema complejo, sino que por el contrario, buscamos tener pequeños fragmentos de código que son auto-suficientes:

- Se aprovisionan solos
- Se mantiene solos
- Se apagan y se prenden solos
- Deben tener responsabilidades definidas

![[Pasted image 20250904220338.png]]

No solo existen las funciones "básicas" como lo pueden ser las lambdas, también contamos con:

- Amazon Cognito <-> Azure Active Directory
- Analytics 
- S3 <->Blob Storage
- Amazon Dynamo DB 
- Lambda <-> Function Apps
- Amazon Route 53 <-> Front Doors
- Azure Mobile Apps Service <-> AWS Amplify
- ...

Que nos permite hacer un BaaS (Backend As Service)

![[Pasted image 20250904232225.png]]
Algunas funciones importantes/categorias son:

- FaaS => Lambda 
$$ C_{total} \propto \#_{invocaciones} \times  \#_{recursos} \times T_{ejecuccion} $$
- AssS (Almacenamiento)

$$ C_{total} \propto S_{Gb} \times  f_{uso}  $$
- BDaaS (Bases de datos)

$$ C_{total} \propto S_{Gb} \times  \#_{Lectura-Escritura} $$

- AUTaaS (Autenticacion)

$$ C_{total} \propto \#_{usuarios} \times  p_{usuario} $$