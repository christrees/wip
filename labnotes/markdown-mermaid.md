markdown-mermaid
[edit](https://github.com/christrees/wip/edit/main/labnotes/markdown-mermaid.md)

- [mermaid cheatsheet https://jojozhuang.github.io/tutorial/mermaid-cheat-sheet/](https://jojozhuang.github.io/tutorial/mermaid-cheat-sheet/)
---

```mermaid

  graph TD; 
  A(Start)-->B(Do some stuff); 
  B(Take some rest)-->C(do more);
  click B "http://www.github.com" "This is a link"
  
```

### Charts in markdown mermaid
- [https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/)
```mermaid
  graph TD;
      A-->B;
      A-->C;
      B-->D;
      C-->D;
```

```mermaid
sequenceDiagram
    participant dotcom
    participant iframe
    participant viewscreen
    dotcom->>iframe: loads html w/ iframe url
    iframe->>viewscreen: request template
    viewscreen->>iframe: html & javascript
    iframe->>dotcom: iframe ready
    dotcom->>iframe: set mermaid data on iframe
    iframe->>iframe: render mermaid
```

```mermaid
stateDiagram
    [*] --> New
    New --> Active : Activate
    New --> Closed : Close
    Active --> Inactive : Deactivate
    Active --> Closed : Close
    Inactive --> Active: Activate
    Inactive --> Closed : Close
```
