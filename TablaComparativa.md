# Haskell

## Tabla comparativa entre Functor, Applicative y Monad

| Característica         | Functor                       | Applicative                     | Monad                          |
|------------------------|-------------------------------|---------------------------------|--------------------------------|
| **Clase de tipo**      | `class Functor f where`       | `class Functor f => Applicative f where` | `class Applicative m => Monad m where` |
| **Método principal**   | `fmap :: (a -> b) -> f a -> f b` | `(<*>) :: f (a -> b) -> f a -> f b` | `(>>=) :: m a -> (a -> m b) -> m b` |
| **Inyección pura**     | -                             | `pure :: a -> f a`              | `return :: a -> m a` (heredado) |
| **Capacidad clave**    | Transformar valores en contexto | Aplicar funciones en contexto | Secuenciar operaciones con contexto |
| **Dependencia entre operaciones** | Ninguna | Limitada (independientes) | Completa (dependencia de resultados previos) |
| **Modelo de cómputo**  | Transformación simple | Aplicación paralela/independiente | Secuencia lineal dependiente |
| **Leyes**              | 1. Identidad <br> 2. Composición | 1. Identidad <br> 2. Composición <br> 3. Homomorfismo <br> 4. Intercambio | 1. Identidad izquierda <br> 2. Identidad derecha <br> 3. Asociatividad |
| **Operadores comunes** | `<$>`, `<$` | `<*>`, `<*`, `*>`, `liftA2` | `>>=`, `>>`, `=<<`, `>=>` |
| **Sintaxis especial**  | -                             | Expresiones aplicativas        | Notación `do`                 |
| **Ejemplo típico**     | `(+1) <$> Just 3` → `Just 4` | `(+) <$> Just 2 <*> Just 3` → `Just 5` | `Just 2 >>= \x -> Just (x+3)` → `Just 5` |
| **Capacidad para manejar efectos** | Básica | Intermedia | Completa |
| **Relación jerárquica**| Base | Extiende Functor | Extiende Applicative |
| **Complejidad**        | Baja                          | Media                          | Alta                           |
| **Casos de uso típicos** | Transformaciones simples | Validaciones independientes, combinaciones | Flujos de control complejos, operaciones secuenciales |
