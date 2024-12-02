# Математический Анализ | Лекция 12 | Формула Тейлора и Остаточные Члены

---

## Оглавление

1. [Введение](#введение)
2. [Приближение функций многочленами](#приближение-функций-многочленами)
   - 2.1. [Первые попытки приближения](#первые-попытки-приближения)
   - 2.2. [Необходимость более точных приближений](#необходимость-более-точных-приближений)
3. [Построение многочлена Тейлора](#построение-многочлена-тейлора)
   - 3.1. [Определение многочлена Тейлора](#определение-многочлена-тейлора)
   - 3.2. [Многочлен Маклорена](#многочлен-маклорена)
4. [Формула Тейлора с остаточным членом](#формула-тейлора-с-остаточным-членом)
   - 4.1. [Остаточный член в форме Пеано](#остаточный-член-в-форме-пеано)
   - 4.2. [Доказательство формулы Тейлора с остаточным членом в форме Пеано](#доказательство-формулы-тейлора-с-остаточным-членом-в-форме-пеано)
5. [Единственность многочлена Тейлора](#единственность-многочлена-тейлора)
   - 5.1. [Теорема о единственности](#теорема-о-единственности)
   - 5.2. [Доказательство теоремы](#доказательство-теоремы)
6. [Остаточный член в других формах](#остаточный-член-в-других-формах)
   - 6.1. [Теорема о характеристике остаточного члена](#теорема-о-характеристике-остаточного-члена)
   - 6.2. [Остаточный член в форме Лагранжа](#остаточный-член-в-форме-лагранжа)
   - 6.3. [Остаточный член в форме Коши](#остаточный-член-в-форме-коши)
7. [Примеры разложения функций в ряд Тейлора](#примеры-разложения-функций-в-ряд-тейлора)
   - 7.1. [Разложение функции $ \sin x $](#разложение-функции--sin-x-)
   - 7.2. [Разложение функции $ e^x $](#разложение-функции--ex-)
8. [Применение формулы Тейлора](#применение-формулы-тейлора)
   - 8.1. [Вычисление приближённых значений функций](#вычисление-приближённых-значений-функций)
   - 8.2. [Оценка погрешности приближения](#оценка-погрешности-приближения)
9. [Заключение](#заключение)
10. [О чём была эта лекция?](#о-чём-была-эта-лекция)

---

## Введение

Сегодня мы завершаем изучение раздела о дифференцировании и переходим к **формуле Тейлора** — одному из важнейших инструментов математического анализа. Формула Тейлора позволяет приближать функции многочленами, учитывая значения производных функции в определённой точке. Это приближение играет ключевую роль в решении множества прикладных задач, включая вычисление пределов, приближённое вычисление функций и анализ поведения функций.

---

## Приближение функций многочленами

### Первые попытки приближения

При изучении функций часто возникает потребность в их приближении более простыми функциями. Одним из самых простых приближений является постоянная функция:

$$
G_0(x) = f(x_0).
$$

Это приближение совпадает с функцией $f(x)$ в точке $x_0$, но не учитывает изменения функции в окрестности этой точки.

Следующим шагом является линейное приближение с использованием касательной к графику функции в точке $x_0$:

$$
G_1(x) = f(x_0) + f'(x_0)(x - x_0).
$$

Это приближение учитывает не только значение функции в точке $x_0$, но и скорость её изменения.

### Необходимость более точных приближений

Однако для многих функций линейное приближение недостаточно точно на большом интервале вокруг точки $x_0$. Например, для функции $ \sin x $ или $ e^x $ линейное приближение быстро теряет точность при удалении от $x_0$.

Для улучшения приближения можно добавить квадратичный член:

$$
G_2(x) = f(x_0) + f'(x_0)(x - x_0) + \frac{f''(x_0)}{2!}(x - x_0)^2.
$$

Этот многочлен второго порядка учитывает кривизну графика функции в точке $x_0$ и лучше приближает функцию на большем интервале.

---

## Построение многочлена Тейлора

### Определение многочлена Тейлора

**Задача:** Найти многочлен степени $n$:

$$
P_n(x) = a_0 + a_1(x - x_0) + a_2(x - x_0)^2 + \dots + a_n(x - x_0)^n,
$$

такой, что в точке $x_0$ значения функции $f(x)$ и её производных до $n$-го порядка совпадают со значениями соответствующих производных многочлена $P_n(x)$:

$$
\begin{cases}
P_n(x_0) = f(x_0), \\
P_n'(x_0) = f'(x_0), \\
P_n''(x_0) = f''(x_0), \\
\vdots \\
P_n^{(n)}(x_0) = f^{(n)}(x_0).
\end{cases}
$$

**Решение:** Коэффициенты $a_k$ находятся из условий совпадения производных. Вычисляя производные многочлена и подставляя $x = x_0$, получаем систему уравнений:

$$
\begin{align*}
a_0 &= f(x_0), \\
a_1 &= f'(x_0), \\
a_2 &= \frac{f''(x_0)}{2!}, \\
&\vdots \\
a_n &= \frac{f^{(n)}(x_0)}{n!}.
\end{align*}
$$

Таким образом, многочлен Тейлора имеет вид:

$$
P_n(x) = f(x_0) + f'(x_0)(x - x_0) + \frac{f''(x_0)}{2!}(x - x_0)^2 + \dots + \frac{f^{(n)}(x_0)}{n!}(x - x_0)^n.
$$

**Определение:** Этот многочлен называется **многочленом Тейлора порядка $n$** функции $f(x)$ в точке $x_0$.

### Многочлен Маклорена

Если в качестве точки $x_0$ взять ноль, то многочлен Тейлора упрощается:

$$
P_n(x) = f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \dots + \frac{f^{(n)}(0)}{n!}x^n.
$$

Этот многочлен называется **многочленом Маклорена**.

---

## Формула Тейлора с остаточным членом

Приближение функции многочленом Тейлора не является точным, поэтому возникает необходимость учесть погрешность, которая возникает при таком приближении. Эта погрешность называется **остаточным членом**.

### Остаточный член в форме Пеано

**Формула Тейлора с остаточным членом в форме Пеано:**

Если функция $f(x)$ имеет все производные до порядка $n$ включительно в точке $x_0$, то:

$$
f(x) = P_n(x) + o\left((x - x_0)^n\right), \quad \text{при } x \to x_0.
$$

Здесь $o\left((x - x_0)^n\right)$ — это бесконечно малая величина более высокого порядка малости по сравнению с $(x - x_0)^n$.

### Доказательство формулы Тейлора с остаточным членом в форме Пеано

**Доказательство:**

1. **Построение многочлена Тейлора:** Используя совпадение производных функции и многочлена в точке $x_0$, строим многочлен $P_n(x)$.
   
2. **Определение остатка:** Рассмотрим разность $R_n(x) = f(x) - P_n(x)$.

3. **Показать, что остаток мал:** Нужно доказать, что:

   $$
   \lim_{x \to x_0} \frac{R_n(x)}{(x - x_0)^n} = 0.
   $$

4. **Использование теоремы Коши:** Применяя теорему Коши о конечных приращениях и учитывая, что все производные до $n$-го порядка совпадают, получаем, что остаток действительно является величиной порядка $o\left((x - x_0)^n\right)$.

---

## Единственность многочлена Тейлора

### Теорема о единственности

**Теорема:** Если функция $f(x)$ представляется в виде:

$$
f(x) = Q_n(x) + o\left((x - x_0)^n\right), \quad \text{при } x \to x_0,
$$

где $Q_n(x)$ — многочлен степени не выше $n$, то многочлен $Q_n(x)$ совпадает с многочленом Тейлора $P_n(x)$.

### Доказательство теоремы

1. **Предположим обратное:** Пусть существует другой многочлен $Q_n(x)$, отличающийся от $P_n(x)$, такой что $f(x) = Q_n(x) + o\left((x - x_0)^n\right)$.

2. **Рассмотрим разность многочленов:** $D(x) = P_n(x) - Q_n(x)$ — это многочлен степени не выше $n$.

3. **Покажем, что $D(x)$ тождественно равен нулю:**

   - Так как $f(x) - P_n(x) = o\left((x - x_0)^n\right)$ и $f(x) - Q_n(x) = o\left((x - x_0)^n\right)$, то их разность $D(x) = o\left((x - x_0)^n\right) - o\left((x - x_0)^n\right)$.

   - Это означает, что $D(x) = o\left((x - x_0)^n\right)$, то есть степень $D(x)$ выше $n$, что противоречит тому, что $D(x)$ — многочлен степени не выше $n$.

4. **Заключение:** Следовательно, $D(x) \equiv 0$, и $Q_n(x) = P_n(x)$.

---

## Остаточный член в других формах

### Теорема о характеристике остаточного члена

**Теорема:** Пусть функция $f(x)$ имеет непрерывную $(n+1)$-ю производную на интервале, содержащем точки $x$ и $x_0$. Тогда остаточный член $R_n(x)$ может быть представлен в виде:

$$
R_n(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x - x_0)^{n+1},
$$

где $\xi$ — некоторая точка между $x$ и $x_0$.

### Остаточный член в форме Лагранжа

**Формула Тейлора с остаточным членом в форме Лагранжа:**

$$
f(x) = P_n(x) + \frac{f^{(n+1)}(\xi)}{(n+1)!}(x - x_0)^{n+1}, \quad \xi \in (x_0, x).
$$

**Доказательство:**

- Применяем теорему Ролля к вспомогательной функции и получаем необходимое представление остаточного члена.

### Остаточный член в форме Коши

**Формула Тейлора с остаточным членом в форме Коши:**

$$
f(x) = P_n(x) + \frac{f^{(n+1)}(\xi)}{n!}(x - x_0)^n(x - \xi), \quad \xi \in (x_0, x).
$$

**Доказательство:**

- Используя интегральную форму остаточного члена и теорему Коши о конечных приращениях, выводим данное представление.

---

## Примеры разложения функций в ряд Тейлора

### Разложение функции $ \sin x $

**Разложение в точке $x_0 = 0$ (ряд Маклорена):**

$$
\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \dots + (-1)^{k}\frac{x^{2k+1}}{(2k+1)!} + R_{2k+1}(x).
$$

**Оценка остаточного члена:**

Используя форму Лагранжа, получаем:

$$
R_{2k+1}(x) = \frac{\sin^{(2k+2)}(\xi)}{(2k+2)!}x^{2k+2}, \quad \xi \in (0, x).
$$

Поскольку $\sin^{(2k+2)}(\xi)$ ограничена, остаток можно оценить.

### Разложение функции $ e^x $

**Разложение в точке $x_0 = 0$:**

$$
e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots + \frac{x^n}{n!} + R_n(x).
$$

**Оценка остаточного члена:**

По формуле Лагранжа:

$$
R_n(x) = \frac{e^{\xi}}{(n+1)!}x^{n+1}, \quad \xi \in (0, x).
$$

---

## Применение формулы Тейлора

### Вычисление приближённых значений функций

**Пример:** Вычислить приближённое значение $\sin(0.1)$ с точностью до $10^{-6}$.

**Решение:**

1. Разложим $\sin x$ до членов порядка $x^5$:

   $$
   \sin x \approx x - \frac{x^3}{6} + \frac{x^5}{120}.
   $$

2. Подставим $x = 0.1$:

   $$
   \sin(0.1) \approx 0.1 - \frac{(0.1)^3}{6} + \frac{(0.1)^5}{120} \approx 0.0998333.
   $$

3. Оценим остаточный член:

   $$
   |R_5(0.1)| \leq \frac{|x|^7}{7!} \leq \frac{(0.1)^7}{5040} \approx 2 \times 10^{-11}.
   $$

   Это меньше заданной точности.

### Оценка погрешности приближения

Формула Тейлора с остаточным членом в форме Лагранжа позволяет получить количественную оценку погрешности приближения. Зная производную $(n+1)$-го порядка и интервал, можно вычислить максимальную возможную ошибку.

---

## Заключение

В этой лекции мы изучили **формулу Тейлора** и способы приближения функций многочленами. Мы узнали, как строить многочлен Тейлора для заданной функции и как использовать различные формы остаточного члена для оценки точности приближения. Формула Тейлора является фундаментальным инструментом в анализе функций и имеет широкое применение в различных областях математики и её приложениях.

---

## О чём была эта лекция?

На этой лекции мы погрузились в изучение **формулы Тейлора**, которая позволяет приближать функции многочленами, используя значения их производных в определённой точке. Мы рассмотрели:

- **Построение многочлена Тейлора**: Вывели общий вид многочлена Тейлора порядка $n$ для функции $f(x)$ в точке $x_0$, используя совпадение значений функции и её производных в этой точке.

- **Многочлен Маклорена**: Специальный случай многочлена Тейлора при $x_0 = 0$.

- **Формула Тейлора с остаточным членом**: Изучили различные формы представления остаточного члена (Пеано, Лагранжа, Коши) и их применение для оценки точности приближения.

- **Единственность многочлена Тейлора**: Доказали, что многочлен Тейлора единственный для заданной функции и порядка.

- **Примеры разложения функций**: Разложили функции $\sin x$ и $e^x$ в ряд Тейлора и оценили остаточный член.

- **Применение формулы Тейлора**: Показали, как использовать разложения для вычисления приближённых значений функций и оценки погрешности.

Формула Тейлора — это мощный инструмент, который позволяет не только приближать функции, но и проводить глубокий анализ их поведения, исследовать сходимость рядов и решать разнообразные задачи в математике и физике.

---

Спасибо за внимание! До встречи на следующей лекции.