# Aproximaciones numéricas para la equivalencia de tasas

Este proyecto analiza la equivalencia entre dos esquemas de amortización de préstamos:

- **Saldos globales**: la tasa de interés se aplica sobre el monto original durante toda la vida del préstamo.
- **Saldos insolutos**: la tasa se aplica sobre el saldo pendiente en cada período (amortización francesa).

Dado que ambos esquemas producen la misma cuota mensual pero tienen estructuras de costo distintas, el notebook resuelve numéricamente —usando el método de Brent— la tasa equivalente de saldos insolutos que iguala el costo total de un crédito bajo el esquema de saldos globales. Al final se comparan las tasas, las cuotas y el costo total bajo ambas modalidades.

## Contenido

```
aprox.ipynb      # Notebook principal con la solución
requirements.txt # Dependencias del proyecto
```

## Requisitos previos

- Python 3.10 o superior
- `pip`

## Instalación

### 1. Clonar o descargar el repositorio

```bash
git clone <url-del-repo>
cd <nombre-del-directorio>
```

### 2. Crear y activar un ambiente virtual

```bash
python3 -m venv .venv
```

- **macOS / Linux**
  ```bash
  source .venv/bin/activate
  ```
- **Windows**
  ```bash
  .venv\Scripts\activate
  ```

### 3. Instalar las dependencias

```bash
pip install -r requirements.txt
```

Las dependencias son:

| Paquete      | Versión  | Uso                                          |
|--------------|----------|----------------------------------------------|
| `numpy`      | 2.4.4    | Arreglos numéricos y generación de rangos    |
| `matplotlib` | 3.10.8   | Graficación de la función transcendente      |
| `scipy`      | 1.17.1   | Método de Brent (`brentq`) para hallar raíces|

## Ejecución

### Con VS Code

1. Abre `aprox.ipynb` en VS Code.
2. Selecciona como kernel el intérprete del ambiente virtual (`.venv`).
3. Ejecuta todas las celdas con **Run All**.

### Con Jupyter en terminal

```bash
jupyter notebook aprox.ipynb
```

> Si `jupyter` no está instalado, agrégalo al ambiente virtual:
> ```bash
> pip install jupyter
> ```

## Resultados esperados

- **Celda 1**: gráfica de la función transcendente $f(x) = -1 + n(x - i) + \frac{1 + ni}{(1+x)^n}$ y la raíz numérica encontrada.
- **Celda 2**: comparativa de tasas (mensual y anual), cuotas y costo total bajo ambos esquemas, junto con la diferencia absoluta entre costos.
