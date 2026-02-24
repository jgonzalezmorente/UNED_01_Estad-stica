# Demostración de la recurrencia de los desarreglos

Queremos demostrar que el número de desarreglos de $ n $ elementos satisface:

$$
!n = (n-1)(!(n-1) + !(n-2))
$$

---

## Definición

Un **desarreglo** es una permutación $ \pi $ de $ \{1, \dots, n\} $ tal que:

$$
\pi(i) \neq i \quad \text{para todo } i
$$

---

## Paso 1: fijamos la imagen de 1

Sea $ \pi $ un desarreglo. Entonces:

$$
\pi(1) = k, \quad k \neq 1
$$

Hay $ n-1 $ posibles valores de $ k \in \{2, \dots, n\} $.

---

## Paso 2: distinguimos casos

### Caso A: $ \pi(k) = 1 $

Entonces $ 1 $ y $ k $ forman un 2-ciclo:

$$
(1\ k)
$$

Eliminamos $ 1 $ y $ k $. La restricción de $ \pi $ a:

$$
\{1, \dots, n\} \setminus \{1, k\}
$$

es un desarreglo de $ n-2 $ elementos.

Por tanto:

$$
|\text{Caso A}| = !(n-2)
$$

---

### Caso B: $ \pi(k) \neq 1 $

Sea $ j $ el único índice tal que:

$$
\pi(j) = 1
$$

Como estamos en el Caso B:

$$
j \neq k
$$

---

## Paso 3: construcción de la biyección

Definimos una aplicación:

$$
\sigma : \{2, \dots, n\} \to \{2, \dots, n\}
$$

por:

$$
\sigma(i) =
\begin{cases}
\pi(i), & i \neq j \\
k, & i = j
\end{cases}
$$

---

## Verificaciones

### 1. $ \sigma $ es permutación

- Eliminamos el valor $ 1 $
- El valor $ k $ queda disponible (antes lo tenía $ \pi(1) $)

No hay repeticiones ni pérdidas de imagen.

---

### 2. $ \sigma $ es desarreglo

- Si $ i \neq j $:

$$
\sigma(i) = \pi(i) \neq i
$$

- Si $ i = j $:

$$
\sigma(j) = k \neq j
$$

Si $ k = j $, entonces $ \pi(k) = 1 $, contradicción con el Caso B.

---

## Paso 4: construcción inversa

Dado $ \sigma' $ desarreglo de $ \{2, \dots, n\} $:

Sea:

$$
j = (\sigma')^{-1}(k)
$$

Definimos $ \pi : \{1, \dots, n\} \to \{1, \dots, n\} $:

- $ \pi(1) = k $
- $ \pi(j) = 1 $
- $ \pi(i) = \sigma'(i) $ si $ i \neq 1, j $

---

## Verificaciones

- $ \pi $ es permutación
- $ \pi $ es desarreglo
- $ \pi(k) \neq 1 $, pues el único que manda a 1 es $ j \neq k $

---

## Paso 5: conclusión

Para cada $ k \neq 1 $:

$$
!(n-2) + !(n-1)
$$

Multiplicando por los $ n-1 $ valores posibles de $ k $:

$$
!n = (n-1)(!(n-2) + !(n-1))
$$

---

## Condiciones iniciales

$$
!0 = 1, \quad !1 = 0
$$


---

# Fórmula general (no recursiva)

Aplicando el principio de inclusión–exclusión:

$$
!n = n! \sum_{k=0}^{n} \frac{(-1)^k}{k!}
$$

---

## Demostración por inclusión–exclusión

Sea $A_i$ el conjunto de permutaciones con $i$ fijo:

$$
A_i = \{ \pi : \pi(i) = i \}
$$

Queremos contar:

$$
!n = n! - \left| \bigcup_{i=1}^{n} A_i \right|
$$

---

### Intersecciones

Si fijamos $k$ posiciones:

$$
\left| A_{i_1} \cap \cdots \cap A_{i_k} \right| = (n-k)!
$$

Hay:

$$
\binom{n}{k}
$$

formas de elegirlas.

---

### Inclusión–exclusión

$$
!n = \sum_{k=0}^{n} (-1)^k \binom{n}{k} (n-k)!
$$

Factorizando:

$$
\binom{n}{k}(n-k)! = \frac{n!}{k!}
$$

obtenemos:

$$
!n = n! \sum_{k=0}^{n} \frac{(-1)^k}{k!}
$$

---

# Aproximación asintótica

Como:

$$
e^{-1} = \sum_{k=0}^{\infty} \frac{(-1)^k}{k!}
$$

se sigue que:

$$
!n \approx \frac{n!}{e}
$$

Más precisamente:

$$
!n = \left\lfloor \frac{n!}{e} + \frac{1}{2} \right\rfloor
$$

---

# Valores pequeños

$$
!1 = 0
$$

$$
!2 = 1
$$

$$
!3 = 2
$$

$$
!4 = 9
$$

$$
!5 = 44
$$

$$
!6 = 265
$$