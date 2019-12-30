# Config File

```haskell
module MyAwesomeProject <: Project

  project : Project
  project = 
    {
      version: {
        major: 0,
        minor: 1,
        patch: 0,
        flag: none
      },
      prime: {
        update_by: Minor
        {major: 0, minor: 1, patch: 0}
      },
      maintainers: [
        {
          name: "Brooklyn Zelenka",
          github: "expede"
          email: "hello@brooklynzelenka.com"
        }
      ],
      deps
    }
    where
      deps : [Package]
      deps = []
  
  application : Application 
  application = 
    {
      sub_apps: [logger]
    }
  
  scripts : {Symbol -> Script}
  scripts = 
    {
      quality: Recursive [test, lint],
      
    }
```

