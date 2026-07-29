# emeland-ui mocks 

The `emeland-ui` development mock data (`src/mocks/*.ts`) converted to EmELand YAML.

| File                 | Kinds                        | Documents |
| -------------------- | ---------------------------- | --------- |
| `00_contexts.yaml`   | ContextType, Context         | 5 + 11    |
| `01_nodes.yaml`      | NodeType, Node               | 4 + 6     |
| `02_systems.yaml`    | System, SystemInstance       | 9 + 8     |
| `03_apis.yaml`       | API                          | 9         |
| `04_components.yaml` | Component, ComponentInstance | 6 + 10    |
| `05_findings.yaml`   | FindingType, Finding         | 3 + 4     |

The numeric prefix fixes the apply order: `scanDir` in `modelsrv/pkg/filesensor` reads directory
entries in name order, so types are applied before the resources referencing them and systems
before their instances.

## What the findings file does and does not contain

`modelsrv/pkg/model/finding/finding_kind.go` declares currently six finding kinds and derives each
FindingType UUID as `uuid.NewSHA1(c3d4e5f6-a7b8-9012-cdef-012345678901, kind)`. 

**A FindingType is written only if modelsrv knows the kind** and only if its UUID equals the derived one.