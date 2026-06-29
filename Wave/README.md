# Ecuación de Onda con PINNs

## Descripción
Este proyecto aborda la resolución de la ecuación de onda utilizando modelos PINN, explorando diferentes enfoques de modelado de dominio y muestreo de puntos.

## Modelo y Flujo (PyTorch)
- **Estructura del Modelo**: Red neuronal profunda en PyTorch (`torch.nn.Module`) para predecir la amplitud de la onda en base a coordenadas espaciotemporales.
- **Función de Pérdida**: Residuos de la ecuación diferencial parcial (EDP) de la onda acoplada con las restricciones iniciales y de frontera.
- **Entrenamiento**: Los puntos de colocación donde se evalúa la función de pérdida dictan la convergencia y precisión física de la red neuronal.

## Notas y Resultados
- Se procedió a estudiar el uso de **muestreos aleatorios** en el dominio en vez de puntos fijos de colocación sobre una grilla.
- También se exploró y estudió el uso de la simulación de la ecuación en dominios más complejos, particularmente **simulación 2D**.
