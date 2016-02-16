# Elixir Notes

## Coolness

Guard clauses on function definitions allow for some nice, clean separation of
different behavior for edge cases, etc.

## Oddities

Lists are odd in that Elixir (because Erlang?) treats lists that can be as
though they were character lists.

The boolean operators are "or", "and", and "not". They require the first
argument to be a boolean and they return a boolean. They short-circuit, only
evaluating the second argument if the first isn't sufficient to know the result.
There are also the operators "||", "&&", and "!". They also short-circuit, but
they don't require boolean arguments. The "!" operator always returns a boolean,
but the other two will return the value of the last argument evaluated. During
evaluation, Elixir treats `false` and `nil` as false. Anything else is
considered true.

You can compare different types. Numbers are always less than atoms, which are
less than references, and so on. The result is always defined. Whether it makes
actual sense or not for `1 < :an_atom` to be `true` is another question.

`=` is the "match operator". It can almost be read as, "Make the left side equal
the right side, if it doesn't already and it's possible to do so." Because of
this, it can be used to map multiple variables at a time via lists or tuples.

## Cautions

A set of characters surrounded by double quotes is a string. Using single quotes
makes it a character list.

Don't forget immutability. Since `tuple` isn't reassigned here, it still points
to the original tuple:

```elixir
iex> tuple = {:ok, "hello"}
{:ok, "hello"}
iex> put_elem(tuple, 1, "world")
{:ok, "world"}
iex> tuple
{:ok, "hello"}
```

