# Resumo 2 Paradigmas de Programação

## Nome: Vitor Augusto de Medeiros  
## RA:   11201720112

# Semana 3

### QuickCheck

```haskell
import Test.QuickCheck
[...]
>> teste ou formulação
[...]
quickCheck prop_seuTeste
```

- Serve como uma forma de testar o codigo para garantir que esteja realizando aquilo que se espera (similar a unit/integTest) , é possivel, inclusive, testar
matematicamente a corretude do algoritmo através dessa biblioteca. Faz uso de propriedades e funcoes para atingir esse resultado.


# Funções de Alta Ordem

- Funcoes que recebem outra funcaode argumento, ou retorna funcoes (ou ambas), sendo uteis para criar funcoes genéricas.

```haskell
-- efine soma de inteiros
soma :: Int -> Int -> Int
soma x y = x + y

-- define funcao que retorna resultado de outra funcao
soma :: Int -> (Int -> Int)
soma3 = soma 3
soma3 2 
```
Outra forma de declarar funcao com parametro generico:

```haskell
-- parametro de entrada na esquerda
dobra = (*2) 
-- parametro na direita
reciproco = (1/)
```

Existem várias funcoes que podem ser utilizadas dentro desses programas tais como:

- Map: Aplica uma funcao para elemento da lista (igual map em java) f :: (a -> b)
- Filter: tambem parecido com java, serve como filter pra reduzir a quantidade de elementos dada uma condicao
- foldr (fold-right): importante para definir funcoes de soma/multiplicacao e concatenacao: concatDigits = foldl (\acc d -> d + acc * 10) 0
- foldl (fold-left): similar ao foldr mas a partir da esquerda: foldl (-) 0 [1..10] = -55 porque (((((((((0-1)-2)-3)-4)-5)-6)-7)-8)-9)-10
ps: Quando a função f é associativa, a aplicação de foldr e foldl não faz diferença. mas foldr (-) 0 [1..10] , por ex, difere de foldl (-) 0 [1..10] 
- length: tamanho de uma lista finita
- reverse: inverte a ordem da lista
- product: produto de todos os elementos da lista 
- sum: soma dos produtos da lista
- even: true se valor par/false se impar


---

# Semana 4 - Tipos de Dados Algébricos

### 7.1: Type
Serve como um alias/criacao de uma estrutura nova simples

```haskell
type Produto = (Integer, String, Double)
type Cliente = (Integer, String, Double)

troco :: Produto -> Cliente -> Double
```

### 7.2 e 7.3: Tipos de Dados Algébricos
- Tipos novos e primitivos.
- Permite checagem em tempo de compilação.

tipos:
- soma: formado pela uniao de diferentes valores data Dir = Norte | Sul | Leste | Oeste
- produto: Double com Double (distancia de pontos) data Ponto = MkPonto Double Double
- maybe: Nothing ou "Just/apenas" utilizado em computacoes que podem falhar
- either: Left ou Right (um ou otro), para funcoes que retornem valores diferentes.
- recursivos: como arvore binaria data Tree a = Leaf a | Node (Tree a) a (Tree a) com repeticao de folha
 
### 7.4 Álgebra dos Tipos


- data Zero -- Sem valor (void)
- data Um = () -- Possui um unico valor. (unit)
- either: soma de tipos
- pair: representa produto data Pair a b = (a, b)

### 7.5 Zippers


### 7.6 Classes de Tipo

Utiliza keyword class para criar a classe personalizadas assim como as implementacoes de cada uma das funcoes. Exemplo:
Classes:

- EQ: tipo comparavel (true/false)
```haskell
(==) :: a -> a -> Bool
(/=) :: a -> a -> Bool
```
- Ord: tipo ordenavel por parametro (maior,menor,min,max)
```haskell
(<) :: a -> a -> Bool
(>) :: a -> a -> Bool
min :: a -> a -> a
```
- Show: Tipos printaveis (nao invalidos, como string)
```haskell
show :: a -> String
```
- Read: Tipos legíveis (parecido com show)
- Num: Tipos numericos
```haskell
(+) :: a -> a -> a
(-) :: a -> a -> a
(*) :: a -> a -> a
abs :: a -> a
```
- Integral: (int) numeros inteiros
```haskell
quot :: a -> a -> a
rem :: a -> a -> a
div :: a -> a -> a
mod :: a -> a -> a
quotRem :: a -> a -> (a, a)
divMod :: a -> a -> (a, a)
toInteger :: a -> Integer
```

- Fractional (fracionados), nao inteiros
```haskell
(/) :: a -> a -> a
recip :: a -> a
```

-Enum: enumeráveis
```haskell
succ, pred, toEnum, fromEnum
```
