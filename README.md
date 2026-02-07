# Polynomial Interpolation: Equidistant 📉 vs Gauss-Lobatto Nodes 📈

This project implements Lagrange polynomial interpolation using two different node grids:

- **Equidistant Nodes**: uniformly distributed across the interval of interest. Simple to implement but can lead to unwanted oscillations (Runge's phenomenon).
  
- **Gauss-Lobatto Nodes**: non-uniformly distributed, concentrated more heavily at the interval endpoints. Reduces Runge's phenomenon and improves accuracy.

## What will you find in the code?

- Interpolation of user-defined mathematical functions
- Interpolation of real datasets (example: CO2 emissions)
- Automatic interpolation error calculation
- Graphical visualization of results
- Quantitative comparison between the two strategies
- Study of extrapolation behavior outside the interpolation interval
- Symbolic generation of interpolating polynomials

This project was developed as an educational tool to:
- Understand Runge's phenomenon
- Study the importance of node selection in interpolation
- Compare different numerical methods
- Visualize theoretical concepts in numerical analysis

##  Requirements

```bash
numpy>=1.21.0
matplotlib>=3.4.0
sympy>=1.9.0
```

### Required inputs

The script will prompt you to enter:

1. **Function to interpolate**: use NumPy syntax (e.g., `np.sin(x)`, `1/(1+25*x**2)`, `x**2`)
2. **Left endpoint of interval (a)**: numeric value
3. **Right endpoint of interval (b)**: numeric value  
4. **Polynomial degree (n)**: integer number

### Example functions

Functions that highlight the differences between the two grids:


#### Runge's function 
(shows strong Runge phenomenon with equidistant nodes)

$$f(x) = \frac{1}{1 + 25x^2}$$


#### Oscillating function
$$f(x) = \sin(10x)$$

#### Polynomial function
$$f(x) = x^3 - 2x^2 + x$$

## Output

The program generates:

1. **Comparative plots** showing:
   - Original function vs interpolations
   - Position of nodes used
   - Interpolation error
   - Visual comparison between the two strategies

2. **Numerical metrics**:
   - Maximum error
   - Mean error
   - Interpolating polynomials in symbolic form

3. **Extrapolation study**:
   - Behavior outside the interval [a, b]
   - Comparison of extrapolation errors

## 📐 Theory

### Lagrange Interpolation

The interpolating polynomial is defined as:

$$P(x) = \sum_{i=0}^{n} y_i \cdot L_i(x)$$

where the Lagrange polynomials $L_i(x)$ are:

$$L_i(x) = \prod_{\substack{j=0 \\ j \neq i}}^{n} \frac{x - x_j}{x_i - x_j}$$

Each $L_i(x)$ equals 1 at $x_i$ and 0 at all other $x_j$ with $j \neq i$, ensuring that $P(x_i) = y_i$.

### Gauss-Lobatto Nodes

The nodes are initially calculated on the standard interval $[-1, 1]$ using:

$$x_j = -\cos\left(\frac{\pi j}{n}\right), \quad j = 0, \ldots, n$$

These nodes always include the endpoints $-1$ and $1$.

They are then transformed to the desired interval $[a, b]$ via affine mapping:

$$x_j^{[a,b]} = \frac{b - a}{2} x_j + \frac{a + b}{2}$$

## Example: CO2 Emissions

The project includes a real dataset of CO2 emissions from 1972 to 2021 to demonstrate practical application of interpolation on real-world data.

## Limitations and Notes

- High-degree polynomial interpolation can lead to numerical instabilities
- Extrapolation (evaluation outside the interval [a, b]) is generally inaccurate
- Gauss-Lobatto nodes are more effective for smooth functions but may not be optimal for very noisy data





## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
