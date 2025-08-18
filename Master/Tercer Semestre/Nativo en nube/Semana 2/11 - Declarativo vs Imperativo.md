---
tags:
  - master
  - cloud
  - k8s
---
Cuando manejamos los recursos a través de *kubectl* (kubernetes control), tenemos dos maneras de manejar nuestros recursos

# Imperativo
Se especifica de manera directa y explícita la acción que se desea realizar. Este enfoque es adecuado cuando quiera ejecutar una operación inmediata y precisa. Por ejemplo:

```bash
kubectl create -f myapp.yaml
```
# Declarativo
Describes el estado deseado del sistema, y k8s se encarga de evaluar y aplicar los cambios necesarios para alcanzar ese estado. Este enfoque es útil para mantener la infraestructura en un estado consistente y reproducible. Por ejemplo:

```bash
kubectl apply -f myservices.yaml
```

En este ejemplo, el archivo myservices.yaml puede contener diferentes componentes como son deployments, pods, services, etc. Kubernetes leerá el archivo, definirá un plan y aplicará los cambios en el ambiente para lograr que los componentes en la infraestructura sean consistentes con los componentes en el archivo.