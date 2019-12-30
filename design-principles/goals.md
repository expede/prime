# Goals & Non-Goals

## Goals

* Full compatibility with GHC-flavoured Haskell
  * Use Haskell from Prime
  * Use Prime from Haskell
* Friendliness
  * Common syntactic elements
    * Dot syntax for record access
    * Pipes
    * Keyword arguments
  * Eliminate common gotchas
    * e.g. Remove explicit `do` and both `let` variants
  * Playful name
* First-class docs
  * Easily parsed out of source
  * Markdown docs
* Kitchen-sink standard library
* Strict data / lazy functions
* Compile targets
  * Improve LLVM pipeline
  * Compile to Wasm \(likely via LLVM\)
* Make it an order of magnitude easier to plug into the compiler 
  * Likely a \(hygienic\) macro system
* Work around the `String` problem
  * Standardize on `Text`
  * `ByteString` at program boundary
  * No direct support for `String` \(signal by dropping the name, e.g. `[Word8]`\)
  * Automatic conversion functions for interacting with Haskell
* First-class effects system
* First-class project configuration
* Safety
  * Test annotations, especially properties on type classes
  * Supervision out-of-the-box
  * Totality checking, overridable with annotation
  * Introduce \(at least limited\) limited dependent types 
    * Dependent tuples
    * Dependent vectors
* Development experience
  * Interpreted mode
  * Interactive development
  * Hot reloading
* Data & helpers
  * Strict data by default
  * String interpolation
  * Map literals
  * Dot-syntax accessors
  * Pipes
  * Infix and postfix operators \(akin to Idris\)
  * First-class row types / extensible records
  * Named argument invocation
* Native effect system
* First-class documentation
  * Markdown
  * Doctests
  * Properties
* ML style module system \(backpack\)
* Standardized project layouts
  * First-class project configuration \(no more `.cabal`/`project.yaml`\)
  * User-defined scripts \(no more `Makefile`\)

## Nice-to-Haves



## Non-Goals

While not against these, we are not optimizing for the following:

* Advancing the type system start of the art
  * Of course we'll port these features back as they become available
* Becoming "Haskell Lite"
* 
