# June, a safe, gradual systems language

TODO:

- [x] Extend testing system to ensure proper allocation lifetimes are followed


NOTES:

Mutable, shared pointers can not be safely deleted as they may have aliases that exist elsewhere in memory. These would require an `unsafe { }` block to do the deletion.

This is why we'd recommend (and lint for) safe abstractions where multiple, shared pointers do not leak out of the abstractions. This helps the locus of reasoning of how these pointers are used. While we don't ban their use as they have obvious utility, we do lean programmers towards using them carefully.

Safe pointers (owned pointers) could be freed, as could their members that are also owned, once the owned pointer is no longer in scope. This could be done without the need of an `unsafe` keyword, as we know there are no aliases in scope. Any fields that use shared pointers would not be safe to free automatically.
