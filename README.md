```mermaid
gitGraph
    branch feature-1
    checkout main
    commit id: "처음"
    checkout feature-1
    commit id: "커밋 3" type: REVERSE tag: "123123"
    checkout main
    commit id: "커밋 2"
```

