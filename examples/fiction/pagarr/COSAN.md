# COSAN — pagarr

> Grammar source: ../소설용_코산_v0_5.md
> COSAN = Coding + 散文(prose)
> File extension: .cosan

## Role Rules

```
Writer      reads:  designated .cosan files + THEME.cosan
            writes: .cosan files
            does NOT simulate

Simulator   reads:  .cosan + .state
            writes: .state + .trace
            CANNOT write .cosan
            CANNOT read ACT / THEME

Renderer    reads:  INDEX.cosan + .trace + THEME.cosan
            writes: prose
            CANNOT change delta
```

## Prohibitions (COSAN PROHIBITIONS — copy as-is, do not rewrite)

1.  Values that are sentences are a violation. Values must be names.
2.  Do not fill ??. Values that set direction are set by humans.
3.  Do not invent what is not in .cosan. STOP and report.
4.  Do not change state not declared in delta.
5.  Nothing enters without ground. "Plausible" is not ground.
6.  Do not create symbols or structures not in grammar. STOP and request.
7.  Unreferenced fields are description. Code-like form is not enough.
8.  Do not write comments without code. Comments are bypass routes.
9.  If not written to file, it does not exist. Do not work in memory.
10. Unrolled cosan is unverified. Always roll.
