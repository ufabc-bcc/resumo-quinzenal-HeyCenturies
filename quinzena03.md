# Resumo 3 Paradigmas de Programação

## Nome: Vitor Augusto de Medeiros  
## RA:   11201720112

### Monoids

A classe monoide descreve uma operação binária de um certo tipo contendo um conceito de elemento neutro

```haskell
class Monoid a where
   mempty  :: a
   mappend :: a -> a -> a

   mconcat :: [a] -> a
   mconcat = foldr mappend mempty
```

- Monoid é um semi-grupo (semi-grupo nao é monoid)
- permite combinar dois valores de "type a" em um


### Functor

- Uma classe de tipos definida da seguinte forma.

```haskell
class Functor f where
   fmap :: (a -> b) -> f a -> f b
```

- pega funcao e transforma em funcao em outro contexto.
- permite que um tipo genérico aplique uma função internamente sem alterar a estrutura do tipo genérico


### Functor Applicative

Definido por 

```haskell
class Functor f => Applicative f where
  pure  :: a -> f a
  (<*>) :: f (a -> b) -> f a -> f b
```

- é uma estrutura intermediária entre functors e monoids
- tem mais estrutura que um functor e menos que um monoid
- util quando nao é necessario o uso de monoids mas ainda é preciso algumas funcionalidades.

### Traversable

```haskell
class (Functor t, Foldable t) => Traversable t where
  traverse :: Applicative f =>
			    (a -> f b) -> t a -> f (t b)

instance Traversable [] where
  traverse g []     = pure []
  traverse g (x:xs) = pure (:) <*> g x <*> traverse g xs
```

- Tipos podem ser mapeados (como funcao map para cada elemento)
- O "traverse" da funcao pode aplicar um applicative functor para cada elemento
- pode aplicar foldr foldl
