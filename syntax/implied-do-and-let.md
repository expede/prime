# Implied do & let

## `do`-notation

I can't tell you many many times I've seen people stuck with a cryptic error because they're missing the two crucial characters "do" at the start of a monadic block.

{% tabs %}
{% tab title="Haskell" %}
```haskell
exclaim :: IO ()
exclaim = do
  text <- getLine
  printLn (text <> "!")
```
{% endtab %}

{% tab title="Prime" %}
```haskell
exclaim : IO ()
exclaim =
  text <- get_line
  print_line (text <> "!")
```
{% endtab %}
{% endtabs %}

## `let...in` and monadic `let`

These constructions also trip many people up, with when you need the `in`, and 

{% tabs %}
{% tab title="Haskell" %}
```haskell
fib :: Int -> Int
fib =
  let 
    fib' 0 = 0
    fib' 1 = 1
    fib' n = fib (n - 1) + fib (n - 2)
  in
    (map fib' [0 ..] !!)
```
{% endtab %}

{% tab title="Prime" %}
```haskell
fib : Natural -> Natural
fib =
  fib' 0 = 0
  fib' 1 = 1
  fib' n = fib (n - 1) + fib (n - 2)
  (map fib' [0 ..] !!)
```
{% endtab %}
{% endtabs %}

In the monadic case, we can still use the `let...in` formulation under the hood. Monadic let is a nice trick of bind, but can be reformulated as:

```haskell
action >>= \x ->
  let
    intermediate = x
  in
    moreStuff imtermediate
```

{% tabs %}
{% tab title="Haskell" %}
```haskell
exclaim :: IO ()
exclaim = do
  text <- getLine
  let
    upcased = upcase text
    bang    = upcased <> "!"
  printLn bang
```
{% endtab %}

{% tab title="Alternate Haskell" %}
```haskell
exclaim :: IO ()
exclaim = do
  text <- getLine
  let
    upcased = upcase text
    bang    = upcased <> "!"
  in
    printLn bang
```
{% endtab %}

{% tab title="Prime" %}
```haskell
exclaim :: IO ()
exclaim =
  text <- get_line
  upcased = upcase text
  bang    = upcased <> "!"
  print_line bang
```
{% endtab %}
{% endtabs %}

