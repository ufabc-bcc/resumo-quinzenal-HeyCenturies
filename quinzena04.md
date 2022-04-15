# Resumo 4 Paradigmas de Programação

## Nome: Vitor Augusto de Medeiros  
## RA:   11201720112

### Monads

- Similar a monoid ( extensões de applicative functors )
- Operador  (>=>) -- report falha

``` 
 (>>=) ::     m a -> (a ->     m b) ->     m b
 (>=>) :: Monad m => (a -> m b) -> (b -> m c) -> (a -> m c)
 
 class Applicative m => Monad m where
   return :: a -> m a
   (>>=)  :: m a -> (a -> m b) -> m b

   return = pure
```
- fish (>=>) / bind (>>=)
```
m1 >>= \x1 ->
m2 >>= \x2 ->
...
mn >>= \xn ->
f x1 x2 ... xn

-- ou

do x1 <- m1
    x2 <- m2
    ...
    xn <- mn
    f x1 x2 ... xn
    
```

#### Exemplos

```
> [1,2,3] >>= \x -> [4,5,6] >>= return (x,y)
[(1,4), (1,5), (1,6), (2,4), (2,5), (2,6), (3,4), (3,5), (3,6)]

> [1,2,3] >>= \x -> [4,5,6] >>= return (y)
[1, 1, 1, 2, 2, 2, 3, 3, 3] 

> [1,2,3] >>= \x -> [4,5,6] >>= return (x)
[4, 5, 6, 4, 5, 6, 4, 5, 6]
```

Funcoes Impuras:

- Parcialidade: Funcao pode nao terminar
- Não determinismo: pode dar return de resultados diferentes dependendo das condicoes
- Either (Exception): Identificar o problema com base na exception
- Efeitos colaterais: Read only, Write only, Read/Write
- IO: Alteram estado/ recebem input.


### Funcao de Alta Ordem

- mapM e filterM: 
- filter seleciona e filtra elementos de uma lista com base em uma condicao(similar ao map)
- filterM seleciona eventos possivel de uma sequencia.
```
filterM (\x -> [True, False]) [1,2,3]
[[1,2,3],[1,2],[1,3],[1],[2,3],[2],[3],[]]
```

