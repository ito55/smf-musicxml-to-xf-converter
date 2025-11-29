## Workflow

# without xf-tools
```mermaid
flowchart LR;
    1[(input.mid)] --> 2[Cubase] --> 3[/pdf/]

```

# with xf-tools
```mermaid
flowchart LR;
    1[(input.mid)] --> 2[Cubase] --> 5[/pdf/]
    1 --> 3[convert.py] --> 4[(converted.musicxml)] --> 2
```
