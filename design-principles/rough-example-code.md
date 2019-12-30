# Rough Example Code

```haskell
@docs """
This is an example of a module, 
with some helpful markdown docs
"""
module Foo
  import
    Bar <: {convert : Text -> Text}
    Baz as B
    Quux only quux
  
  main : ST ()
  main =
    name <- getLine "What's your name?"
    
    name
      |> length
      |> case
        0 ->
          main
          
        _ ->
          hey = "Welcome"
          punctuation = "!"
          
          `${hey} ${name}${punctuation}`
            |> print
            |> new_line
    
  # Alternate syntax option
  main' : ST ()
  main' =
    "What's your name?"
      |> getLine 
      /> length
      /> case
        0 ->
          main
          
        _ ->
          hey = "Welcome"
          punctuation = "!"
          
          `${hey} ${name}${punctuation}`
            |> print
            |> new_line
            
  explicit data Either a b
    Left  : a -> Either a b
    Right : b -> Either a b
  
  explicit data TTY m
    Read  : TTY m Text
    Write : Text -> TTY m ()

  read : Effects [TTY] m => Effectful m Text
  read = send Read
  
  write 
    :  Effects [TTY] m
    => Text
    -> Effectful m ()
  write txt = 
    txt
      |> Write
      |> send
  
  effect TTY m
    = Read (m Text)
    | Write (Text -> m ())
  
  handle : TTY -> ST Text
  handle Read =
    with std_in case
      Err _ -> ""
      Ok  x -> x
        
  handle Write msg =
    output msg

  type alias Person = {
    name : Text
    age  : Natural
  } is Showable, Equatable
  
  type 
    Showable, 
    Equatable 
  => Person = {
    name : Text
    age  : Natural
  }
  
  type Result err value
    = Error err
    | Ok value
    
  type alias Maybe val = Result () val
  
  none = Error ()
  
  @private
  apply : a -> (a -> b) -> b
  apply a f = f a
  
  @docs """
  An example of named arguments to do out of sequence currying
  """
  foo : Num a => (n -> m) -> m
  foo = apply {a = 42}
  
  repipeline : Foo -> Foo
  repipeline arg =
    arg
      |> foo
      |> \x -> bar x 42
      |> baz
      |> quux 32
      
  repipeline : Foo -> Foo
  repipeline arg =
    arg
      |> foo
      |> bar _ 42
      |> baz
      |> quux 32
  
  docs """
  `math` is an example of a function with complex dependencies.
  As you can see, it works on numbers (`Num a`), 
  """
  math 
    :  Nontotal,
       Num n 
    => n
    -> (n -> n) 
    -> (Nontotal => n -> n)
    -> n
  math some_number f g =
    some_number
      |> f
      |> g
  
  double : Num n => n -> n
  double a = a * 2
    where
      @docs = """
      Doubles a number. This is fairly straightforward.
      Mainly here as a demo of how documentation would work.
      
      Here is an example of it in use:
      
          > double 1
          2
      
      And another example, which is good for explanation:
                  
          > double 1.1
          2.2
      """
      
      @examples =
        double 3 == 6
        double 102 == 204
      
      @properties = is_even

  abstract Semigroup a
    concat : a -> a -> a
      where
        @properties =
          associative

  @docs """
  `Chain` is an extension of `Apply` that defines 
  the classic bind/chain opetator.
  """
  @operator (_ ~> _) ~> _, precidence: 1
  abstract Apply m => Chain m
    chain : m a -> (a -> m b) -> m b
      where
        @operator
          (_ ~> _) ~> _
          precidence: 1
          
        @docs """
        The actual chain operator
        """
  
  abstract Chain m => Monad m
    @properties =
      left_identity
      right_identity

  left_identity : # ...
  left_identity f arg =
    left = 
      arg 
        |> into a 
        |> chain f
    right = f a
    left == right
    
  addUser 
    :  Effects [CryptoHash, KVStore Username PasswordHash] effs
    => Username
    -> Password
    -> Effectful effs ()
  addUser username password =
    hashedPassword <- makeHash password
    writeKV username hashedPassword

  validatePassword 
    :  Effects [CryptoHash, KVStore Username PasswordHash] effs
    => Username
    -> Password
    -> Effectful effs Bool
  validatePassword username password =
    username
      |> lookupKV
      |> bind case
        Just h  -> validateHash password h
        Nothing -> return False
```

