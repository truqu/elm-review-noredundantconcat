# elm-review-noredundantconcat

Helps with preventing redundant usage of list concatenation. Expressions like `[ a ] ++ b` can be rewritten as `a :: b`, and expressions like `[ a ] ++ [ b ]` could be simply `[ a, b ]`.

## Configuration

```elm
module ReviewConfig exposing (config)

import NoRedundantConcat
import Review.Rule exposing (Rule)

config : List Rule
config =
    [ NoRedundantConcat.rule
    ]
```
