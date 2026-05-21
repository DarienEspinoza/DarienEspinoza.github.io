# Calculadora de Becas y Financiamiento Estudiantil

# Descripción
Página web estática que permite calcular si un estudiante es apto para una beca académica según su promedio, o en su defecto, generar un plan de financiamiento con y sin interés.

# Requisitos
- Navegador web (Chrome, Firefox, Edge, Safari)
- No requiere servidor ni instalación

# Cómo usar
1. Ingresa tu promedio (0 – 100)
2. Ingresa el costo de tu colegiatura
3. Ingresa el número de meses a financiar (solo si no tienes beca)
4. Haz clic en **Calcular**

# Reglas de negocio

| Promedio | Beca |
|---|---|
| 95 – 100 | 100% |
| 90 – 94 | 80% |
| 86 – 89 | 60% |
| 85 o menos | Sin beca → se calcula financiamiento |

- La tasa de interés para financiamiento es del **5%** sobre el total de la colegiatura.
- Se muestra el total y mensualidad **con y sin interés**.

# Lógica del programa
1. El formulario envía los datos por URL usando método GET
2. JavaScript lee los parámetros de la URL con URLSearchParams
3. Se evalúa el promedio con if / else if / else
4. Si promedio > 85 → se calcula y muestra el descuento de beca
5. Si promedio ≤ 85 → se calcula el total con y sin interés según los meses ingresados
6. Los resultados se imprimen con document.write
