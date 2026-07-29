# EchoPath Preconditioning Lab Demo

Public-safe visual diagnostic mirror for the EchoPath Preconditioning Lab.

The private Preconditioning Lab owns diagnostic contracts and validation. The private Q-RRG kernel owns route and repair truth. This repository only renders synthetic or explicitly projected public-safe artifacts.

## Demo status

```text
v0 = static diagnostic viewer — complete
v1 = local JSON/JSONL loader + stress fixtures — complete
v2 = scene, bridge-event and Harp correlation — complete
v3 = kernel bridge replay console — specified and deferred
```

V3 is recorded in `docs/PUBLIC_DEMO_V3_DEFERRED_ROADMAP.md`. It is not a prerequisite for the E-Tree Translation and CASE Library bootstrap.

## Live demos

```text
Landing page:
https://echopath-source.github.io/Preconditioning-Lab-Demo/

Demo v2:
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v2/

Demo v1:
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v1/

Demo v0:
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v0/
```

## Demo v2 contract

Inputs:

```text
spec005_culling_scene_v0 JSON
qrrg_preconditioning_bridge_event_v0 JSONL
optional qrrg_harp_repair_event_v0 JSONL
```

Render mapping:

```text
no_repair_needed + transport
  -> solved route / no repair needed

bridge_accept + transport
  -> accepted segment / clean local link

bridge_reject + fallback + unknown
  -> no-path / disconnected component failure

repair_success + component_bridge + seam or carry
  -> repaired stress-route bridge representation
```

The file pickers use local browser APIs. Files are not uploaded. User-provided values are inserted through text nodes rather than unsafe HTML.

## Sample data

```text
sample-data/spec005_culling_scene_v0.json
sample-data/qrrg_repair_events_v0.jsonl
sample-data/spec005_boundary_stress_scene_v0.json
sample-data/spec005_carry_retention_scene_v0.json
sample-data/qrrg_repair_stress_events_v0.jsonl
sample-data/mixed_scene_qrrg_pair_spec005_scene_v0.json
sample-data/mixed_scene_qrrg_pair_events_v0.jsonl
sample-data/qrrg_preconditioning_bridge_events_v0.jsonl
sample-data/qrrg_harp_repair_events_v0.jsonl
```

All samples are synthetic and public-safe.

## Architecture boundary

Correct flow:

```text
kernel adapter / route-card response
-> versioned public-safe bridge events
-> overlay / debugger / report
```

Forbidden coupling:

```text
public demo -> Preconditioning experimental source
public demo -> Don research files
public demo -> private qrrg_kernel internals
public demo -> arbitrary raw kernel diagnostics
```

## Local test

```sh
python3 -m http.server 8000
```

Open:

```text
http://localhost:8000/visual-diagnostic-demo-v2/
```

## Non-claims

```text
no private research notes
no private Q-RRG kernel
no production runtime
no public SDK guarantee
no product benchmark claim
no Hodge or physics proof claim
no backend upload
```

## GitHub Pages

```text
Settings -> Pages
Source: Deploy from a branch
Branch: main
Folder: / (root)
```
