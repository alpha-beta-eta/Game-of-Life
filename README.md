# Game of Life

This is a simple implementation of Conway's Game of Life
based on an embedded array language inspried by APL.

```
(define conway-kernel
  (<< (Array #(1 1 1 1 0 1 1 1 1))
      (rho2 3 3)))
(define (neighbor grid)
  (<< conway-kernel
      (Convolve2 grid '(1 1))))
(define (step grid)
  (Materialize2
   ((Zip-with
     (λ (x n)
       (if (= x 1)
           (if (or (= n 2) (= n 3)) 1 0)
           (if (= n 3) 1 0))))
    grid (neighbor grid))))
```
