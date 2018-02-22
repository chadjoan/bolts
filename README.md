## Bolts Meta Poragmming Utility Library

Full API docs available [here](https://aliak00.github.io/bolts/)

Bolts is a utility library for the D programming language that provides templates and compilet time functions that are not available in D's std.traits and/or std.meta packages.

E.g.
```d
struct S {
    void f() {}
    static void sf() {}
    @property int rp() { return m; }
    @property void wp(int) {}
}

static assert( hasProperty!(S, "rp"));
static assert(!isSortedRange!S);
static assert(memberFunctions!S == ["f", "sf"]);

alias R1 = typeof([1, 2, 3].filter!"true");
alias R2 = typeof([1.0, 2.0, 3.0]);

static assert(is(FlattenRanges!(int, R1, R2) == AliasSeq!(int, int, double)));

static assert(is(TypesOf!("hello", 1, 2, 3.0, real) == AliasSeq!(string, int, int, double, real)));
```
