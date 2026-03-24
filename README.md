# Elliptic Curve Point Order Calculator (Baby-step Giant-step)

> **Lab 6** — Methods of Algebraic Geometry in Cryptography (DSTU)

Implementation of elliptic curve arithmetic over a prime finite field **GF(p)** and the **Baby-step Giant-step (BSGS)** algorithm for computing the order of a point on the curve.

---

## EN

### Description

Given an elliptic curve `y² ≡ x³ + ax + b (mod p)`, the program:

1. **Enumerates all rational points** on the curve over GF(p)
2. **Computes the order** of a user-specified point using the Baby-step Giant-step algorithm
3. **Prints detailed step-by-step output** of the BSGS algorithm (baby table, giant steps, matching)

### Implemented Operations

| Function | Description |
|---|---|
| `mod_inv(n, p)` | Modular inverse via Fermat's little theorem |
| `find_points(a, b, p)` | Brute-force enumeration of all curve points |
| `is_on_curve(P, a, b, p)` | Checks if a point lies on the curve |
| `add_points(P, Q, a, p)` | Elliptic curve point addition |
| `double_point(P, a, p)` | Elliptic curve point doubling |
| `scalar_multiply(k, P, a, p)` | Scalar multiplication (double-and-add) |
| `baby_step_giant_step(P, a, p)` | BSGS algorithm for point order computation |

### How It Works

The Baby-step Giant-step algorithm finds the smallest `n` such that `nP = O` (point at infinity):

1. Compute `m = ⌈√N⌉` where `N = p + 1 + 2√p` (Hasse bound)
2. **Baby step**: build a lookup table `{tP : t}` for `t = 1, ..., m`
3. **Giant step**: compute `Q = mP`, then iterate `R = j·(−Q)` for `j = 0, 1, ...`
4. When `R` matches a table entry `i`, the candidate order is `n = j·m + i`
5. Verify that `nP = O`

### Usage

```bash
python main.py
```

```
Введите a, b, p через пробел: 1 6 11
y² ≡ x³ + 1x + 6 (mod 11)
Все точки: [(2, 4), (2, 7), (3, 5), (3, 6), (5, 2), (5, 9), (7, 2), (7, 9), (8, 3), (8, 8), (10, 2), (10, 9)] и О

Введите координаты P (x y): 2 4
```

The program will output a detailed trace of the BSGS algorithm and print the order of point P.

### Requirements

- Python 3.6+
- No external dependencies (uses only `math` standard library)

---

## RU

### Описание

Для эллиптической кривой `y² ≡ x³ + ax + b (mod p)` программа:

1. **Перечисляет все рациональные точки** кривой над GF(p)
2. **Вычисляет порядок** заданной пользователем точки алгоритмом Baby-step Giant-step
3. **Выводит подробную пошаговую трассировку** работы алгоритма BSGS (таблица baby-шагов, giant-шаги, поиск совпадения)

### Реализованные операции

| Функция | Описание |
|---|---|
| `mod_inv(n, p)` | Модулярное обращение через малую теорему Ферма |
| `find_points(a, b, p)` | Перебор всех точек кривой |
| `is_on_curve(P, a, b, p)` | Проверка принадлежности точки кривой |
| `add_points(P, Q, a, p)` | Сложение точек эллиптической кривой |
| `double_point(P, a, p)` | Удвоение точки эллиптической кривой |
| `scalar_multiply(k, P, a, p)` | Скалярное умножение (метод двоичного разложения) |
| `baby_step_giant_step(P, a, p)` | Алгоритм BSGS для вычисления порядка точки |

### Принцип работы

Алгоритм Baby-step Giant-step находит наименьшее `n` такое, что `nP = O` (бесконечно удалённая точка):

1. Вычисляем `m = ⌈√N⌉`, где `N = p + 1 + 2√p` (граница Хассе)
2. **Baby-шаг**: строим таблицу `{tP : t}` для `t = 1, ..., m`
3. **Giant-шаг**: вычисляем `Q = mP`, затем итерируем `R = j·(−Q)` для `j = 0, 1, ...`
4. Когда `R` совпадает с записью таблицы `i`, кандидат на порядок: `n = j·m + i`
5. Проверяем, что `nP = O`

### Запуск

```bash
python main.py
```

```
Введите a, b, p через пробел: 1 6 11
y² ≡ x³ + 1x + 6 (mod 11)
Все точки: [(2, 4), (2, 7), (3, 5), (3, 6), (5, 2), (5, 9), (7, 2), (7, 9), (8, 3), (8, 8), (10, 2), (10, 9)] и О

Введите координаты P (x y): 2 4
```

Программа выведет подробную трассировку алгоритма BSGS и порядок точки P.

### Требования

- Python 3.6+
- Внешние зависимости отсутствуют (используется только стандартная библиотека `math`)

---

### License / Лицензия

MIT
