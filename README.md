# EchoPath Preconditioning Lab Demo

Public-safe visual diagnostic mirror for the EchoPath Preconditioning Lab.

This repository publishes browser-viewable diagnostic projections while the private Preconditioning Lab and private Q-RRG kernel remain the tested sources of truth.

## Live Demos

```text
Landing page:
https://echopath-source.github.io/Preconditioning-Lab-Demo/

Demo v2 — scene, bridge-event, and optional Harp residual correlation:
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v2/

Demo v1 — local single-file loader:
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v1/

Demo v0 — static diagnostic projection:
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v0/
```

## Source-of-Truth Boundary

```text
private Preconditioning Lab fixtures / validators / CI = diagnostic contract truth
private Q-RRG kernel responses / tests = route and repair truth
this public repo = public-safe visual projection only
```

The browser canvas is not a correctness source and does not establish product validation.

## Demo v2: Bridge Correlation

Demo v2 loads these inputs together:

```text
spec005_culling_scene_v0 JSON
qrrg_preconditioning_bridge_event_v0 JSONL
optional qrrg_harp_repair_event_v0 JSONL enrichment
```

It correlates `from_address` and `to_address` with scene object IDs and renders the public-safe mapping:

```text
no_repair_needed + transport
  -> solved route / no repair needed

bridge_accept + transport
  -> accepted segment / clean local link

bridge_reject + fallback + unknown
  -> no-path / disconnected component failure

repair_success + component_bridge + seam or carry
  -> future repaired stress-route bridge
```

The file pickers use the browser FileReader API. Files are not uploaded to a backend. User-provided event fields are rendered through DOM text nodes rather than `innerHTML`.

## Sample Data

Baseline and stress scenes/events:

```text
sample-data/spec005_culling_scene_v0.json
sample-data/qrrg_repair_events_v0.jsonl
sample-data/spec005_boundary_stress_scene_v0.json
sample-data/spec005_carry_retention_scene_v0.json
sample-data/qrrg_repair_stress_events_v0.jsonl
sample-data/mixed_scene_qrrg_pair_spec005_scene_v0.json
sample-data/mixed_scene_qrrg_pair_events_v0.jsonl
```

Demo v2 correlated fixtures:

```text
sample-data/spec005_culling_scene_v0.json
sample-data/qrrg_preconditioning_bridge_events_v0.jsonl
sample-data/qrrg_harp_repair_events_v0.jsonl
```

All samples are synthetic and public-safe. They do not contain private lab fixtures, Don source files, private kernel traces, or backend credentials.

## Local Test

```sh
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/visual-diagnostic-demo-v2/
```

Quick fixture checks:

```sh
python3 -m json.tool sample-data/spec005_culling_scene_v0.json >/dev/null
python3 - <<'PY'
import json
from pathlib import Path
for path in [
    Path('sample-data/qrrg_preconditioning_bridge_events_v0.jsonl'),
    Path('sample-data/qrrg_harp_repair_events_v0.jsonl'),
    Path('sample-data/qrrg_repair_stress_events_v0.jsonl'),
]:
    with path.open() as fh:
        for line_number, line in enumerate(fh, 1):
            if line.strip():
                json.loads(line)
print('JSONL fixtures parsed successfully')
PY
```

## Architecture Boundary

Correct downstream flow:

```text
product consumer
-> kernel adapter / route-card response
-> qrrg_preconditioning_bridge_event_v0 stream
-> overlay / debugger / report
```

Forbidden coupling:

```text
product consumer -> Preconditioning Lab experimental source
product consumer -> Don research files
product consumer -> private qrrg_kernel internals
```

## What Is Not Included

```text
no private research notes,
no Don source files,
no private Q-RRG kernel,
no production runtime,
no public SDK guarantee,
no product benchmark claim,
no Hodge or physics proof claim,
no backend upload.
```

## GitHub Pages Setup

```text
Settings -> Pages
Source: Deploy from a branch
Branch: main
Folder: / (root)
```
