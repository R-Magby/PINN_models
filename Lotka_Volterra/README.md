# Ecuaciones de Lotka-Volterra: Descubrimiento de Parámetros con PINNs

## Descripción
Este proyecto se centra en resolver el problema inverso para el modelo de Lotka-Volterra; es decir, encontrar los parámetros desconocidos del sistema de ecuaciones utilizando una red neuronal informada por la física (PINN).

## Modelo y Flujo (PyTorch)
- **Estructura del Modelo**: Red neuronal estándar (MLP) construida en PyTorch (`torch.nn.Module`), donde los parámetros físicos se definen como variables entrenables (`torch.nn.Parameter`).
- **Función de Pérdida**: Incluye la restricción de las ecuaciones de Lotka-Volterra, además del ajuste a los datos de observación (data loss).
- **Entrenamiento**: Al minimizar la pérdida, la red no solo aproxima la solución de las ecuaciones, sino que también converge hacia los valores reales de los parámetros.

## Notas y Resultados
- La obtención de los parámetros se logró exitosamente.
- Un aprendizaje fundamental fue que la precisión y el éxito del descubrimiento de parámetros dependen bastante de la cantidad de observaciones empíricas que uno incorpore en el entrenamiento.
