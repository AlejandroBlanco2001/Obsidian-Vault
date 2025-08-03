---
tags:
  - Agilismo
  - git
  - tips
  - master
---
# No solo el codigo se versiona
Además de versionar el codigo es conveniente ***versionar otros artefactos*** que hacen parte del producto de software, cómo pueden ser:

- Scripts de base de datos
- Documentos de prueba
- Datos de prueba
- La documentación
- Archivos de configuración
- Ejecutables

Siempre es importante definir ***dichos artefactos***.

# Mensajes significativos 
Siempre es bueno manejar un mensaje de commit bastante significativo, que nos diga:
- Que se hizo
- Porque
- Donde
Una alternativa seria usar estándares como ***Conventional commits***
```bash
<Tipo>[alcance(opcional)] <descripcion> [cuerpo<opcional>] [pie del mensaje (opcional)]
```
# Commit = 1 Proposito 
Un commit debe cumplir un unico proposito
- Agregar
- Modificar
- Eliminar
- Mejorar
# Integre frecuentemente los cambios de otros 
Actualiza constantemente tu rama de trabajo local

# Comparte tus cambios frecuentemente
Actualiza tu rama remota constantemente

# No romper el build de los demas
Asegúrate que cuando actualizas, no rompas lo de los demás 

# Bitácora de cambios 
Generar una bitácora de cambios para llevar un registro de los cambios 

# Versionamiento semanttico
Nombrar bajo algun estandar las diferentes versiones del producto. Puede utilizar el versionamiento semantico (SemVer 2.0)

```
1.2.10
Version mayor
Version menor 
Parche
```

- La version mayor aumenta cuando hay incompatibilidades con la version anterior.
- La version menor aumenta cuando se agregan funcionalidades compatibles con la version anterior 
- Los parches, son cuando se corrigen errores con la version anterior


