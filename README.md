# Proyecto PINNs (Physics-Informed Neural Networks)

Este repositorio compila varios proyectos y simulaciones realizados utilizando el modelo de Redes Neuronales Informadas por la Física (PINNs), implementado en PyTorch. Contiene exploraciones sobre distintos sistemas dinámicos (Oscilador Armónico, Lotka-Volterra, FitzHugh-Nagumo y la Ecuación de Onda), evaluando el desempeño de la arquitectura neuronal al introducir conocimiento físico a través de funciones de pérdida.

## Flujo General del Modelo PINN
A lo largo de las 4 carpetas, se repite un esquema general al emplear el modelo PINN:
1. **Definición de la Arquitectura**: Se construye una red neuronal profunda (`torch.nn.Module`) empleando funciones de activación no lineales (como `tanh`, la cual dio mejores resultados).
2. **Definición de Función de Pérdida conjunta**: La optimización de la red no depende sólo de los datos, sino que se formula una función de pérdida que castiga los desajustes con respecto a la ecuación diferencial (EDO/EDP) subyacente y las condiciones iniciales/fronteras.
3. **Entrenamiento**: Uso de optimizadores para ajustar los pesos iterativamente evaluando los residuos en puntos de colocación dentro del dominio espacio-temporal.

## Conclusiones y Notas del Proyecto

Tras realizar experimentos en los distintos casos, he recabado las siguientes lecciones clave:

- **Impacto de la Condición Inicial**: La pérdida asociada a la condición inicial (ic) tiene un impacto muy fuerte en los puntos del dominio temporal cercanos a este. Para puntos lejanos, su impacto e influencia se debilita. Debido a esto, **es recomendable el uso de técnicas como el *time marching*** (entrenamiento progresivo en el tiempo) para sistemas prolongados, aunque en mi caso no tuve suerte o grandes resultados al aplicarlo.
- **PINNs para Problemas Inversos**: El modelo PINN demostró tener un desempeño muy superior al añadirle puntos aleatorios. Esto me da a entender que su arquitectura **es especialmente útil para encontrar parámetros ocultos del sistema** (como se logró exitosamente en Lotka-Volterra), más que para observar y recrear la dinámica a lo largo del tiempo de sistemas continuos complejos desde cero.
- **Ruido en la Pérdida**: En los casos donde se usaron puntos aleatorios, se observó que la evolución de la pérdida presenta mucho ruido; esto **es debido a los puntos aleatorios de colocación que cambian en cada epoch**.
