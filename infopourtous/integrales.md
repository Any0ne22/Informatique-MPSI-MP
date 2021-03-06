# Méthodes de calcul numérique d'une intégrale


## Méthode des rectangles

La méthode d'approximation la plus simple, on approxime l'aire sous la courbe de la fonction f entre a et b par n rectangles.

```python
def rectangle(f, a, b, n):
    I = 0
    T = b - a
    h = T/n
    for i in range(n):
        I += f(a + i * h)
    return h * I
```

## Méthode des points milieux

On approxime l'aire sous la courbe de la fonction f entre a et b par n rectangles de hauteur la moyenne de la fonction aux extrémités du rectangle.

```python
def pointsMilieux(f, a, b, n):
    I = 0
    T = b - a
    h = T/n
    for i in range(n):
        I += f(a + i * h + (h / 2))
    return h * I
```

## Méthode des trapèzes

On approxime l'aire sous la courbe de la fonction f entre a et b par n trapèzes.

```python
def trapezes(f, a, b, n):
    I = (f(a) + f(b))/2
    T = b - a
    h = T/n
    for i in range(n - 1):
        I += f(a + i * h)
    return h * I
```

## Méthode de Simpson

On fait une moyenne pondérée de la méthode des trapèzes et des points milieux pour réduire l'erreur d'approximation.

```python
def simpson(f, a, b, n):
    t = trapezes(f, a, b, n)
    pm = pointsMilieux(f, a, b, n)
    return t/3 + (2*pm)/3
```