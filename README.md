# elm-review-noredundantconcat

Helps with preventing redundant usage of concatenation. Expressions like `[ a ]
++ b` can be rewritten as `a :: b`, and expressions like `[ a ] ++ [ b ]` could
be simply `[ a, b ]`.

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

## Currently covered

- [x] Concatenating list literals with `++` (`[ foo ] ++ [ bar ] -> [ foo, bar ]`)
- [x] Concatenating a list literal with some other value (`[ foo ] ++ bar -> foo :: bar`)
- [x] Using `List.concat` with list literals (`List.concat [ [ foo ], [ bar ] ] -> [ foo, bar ]`)
- [x] Using `++` with `String` literals (`"foo" ++ "bar" -> "foobar"`)

## Future work

- [ ] Using `List.append` with list literals
- [ ] Using `String.append` with string literals
- [ ] Using `String.concat` with string literals
- [ ] Using `String.join ""` over `String.concat`

These all follow a common pattern of making the concatenation of literals more
complex than it has to be.
