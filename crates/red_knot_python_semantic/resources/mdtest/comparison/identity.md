# Identity tests

```py
class A: ...

def get_a() -> A: ...
def get_object() -> object: ...

a1 = get_a()
a2 = get_a()

n1 = None
n2 = None

o = get_object()

reveal_type(a1 is a1)  # revealed: bool
reveal_type(a1 is a2)  # revealed: bool

reveal_type(n1 is n1)  # revealed: Literal[True]
reveal_type(n1 is n2)  # revealed: Literal[True]

reveal_type(a1 is n1)  # revealed: Literal[False]
reveal_type(n1 is a1)  # revealed: Literal[False]

reveal_type(a1 is o)  # revealed: bool
reveal_type(n1 is o)  # revealed: bool

reveal_type(a1 is not a1)  # revealed: bool
reveal_type(a1 is not a2)  # revealed: bool

reveal_type(n1 is not n1)  # revealed: Literal[False]
reveal_type(n1 is not n2)  # revealed: Literal[False]

reveal_type(a1 is not n1)  # revealed: Literal[True]
reveal_type(n1 is not a1)  # revealed: Literal[True]

reveal_type(a1 is not o)  # revealed: bool
reveal_type(n1 is not o)  # revealed: bool
```