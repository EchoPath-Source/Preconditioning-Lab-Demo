# EchoPath Preconditioning Lab Demo

Public-safe visual diagnostic mirror for the EchoPath Preconditioning Lab.

This repository is intentionally small. It publishes browser-viewable demos while keeping the main Preconditioning Lab repository private.

## Live Demo

Landing page:

```text
https://echopath-source.github.io/Preconditioning-Lab-Demo/
```

Static visual diagnostic route:

```text
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v0/
```

Upload-enabled local loader route:

```text
https://echopath-source.github.io/Preconditioning-Lab-Demo/visual-diagnostic-demo-v1/
```

## Source-of-Truth Boundary

```text
private Preconditioning Lab fixtures / JSONL / CI = truth
this public repo = visual diagnostic projection only
```

The browser canvas is not the source of correctness. It is a public-safe visualization of the tested spatial-intelligence chain.

## Current Visual Chain

```text
AABB Training Gym
-> segment / beam boundary behavior
-> SPEC-005 culling / frustum
-> Q-RRG repair event projection
```

## Upload-Enabled v1

Visual Diagnostic Demo v1 supports local-only browser loading for public-safe files:

```text
spec005_culling_scene_v0 JSON
qrrg_repair_event_v0 JSONL
```

The file picker reads local files with the browser FileReader API. It is not uploaded to a backend server.

v1 also includes a built-in stress-sample selector. These built-in samples are fetched from this public repository's `sample-data/` directory and rendered directly in the browser, so users do not need to manually download files just to test the demo.

## Sample Data

Baseline samples:

```text
sample-data/spec005_culling_scene_v0.json
sample-data/qrrg_repair_events_v0.jsonl
```

Public-safe stress samples for EchoPath Preconditioning Lab Demo v1:

```text
sample-data/spec005_boundary_stress_scene_v0.json
sample-data/spec005_carry_retention_scene_v0.json
sample-data/qrrg_repair_stress_events_v0.jsonl
sample-data/mixed_scene_qrrg_pair_spec005_scene_v0.json
sample-data/mixed_scene_qrrg_pair_events_v0.jsonl
```

The stress samples are synthetic and intentionally small enough for browser loading. They cover boundary-touching, inside, outside, intersecting, carry retention, bridge accept, bridge reject, fallback, repair fail, and repair success cases without private lab fixtures, Don source files, or private kernel traces.

### Download and Test Stress Samples

From the live v1 page, use the built-in stress-sample selector and click:

```text
Load selected built-in sample
```

To download a sample instead, use the adjacent download button or open a URL such as:

```text
https://echopath-source.github.io/Preconditioning-Lab-Demo/sample-data/spec005_boundary_stress_scene_v0.json
https://echopath-source.github.io/Preconditioning-Lab-Demo/sample-data/qrrg_repair_stress_events_v0.jsonl
```

From a local checkout, run:

```sh
python3 -m http.server 8000
```

Then open the v1 loader and use either the built-in selector or the file picker to load any stress sample from `sample-data/`:

```text
http://localhost:8000/visual-diagnostic-demo-v1/
```

Quick schema checks from the repository root:

```sh
python3 -m json.tool sample-data/spec005_boundary_stress_scene_v0.json >/dev/null
python3 -m json.tool sample-data/spec005_carry_retention_scene_v0.json >/dev/null
python3 -m json.tool sample-data/mixed_scene_qrrg_pair_spec005_scene_v0.json >/dev/null
python3 - <<'PY'
import json
from pathlib import Path
for path in [
    Path('sample-data/qrrg_repair_stress_events_v0.jsonl'),
    Path('sample-data/mixed_scene_qrrg_pair_events_v0.jsonl'),
]:
    with path.open() as fh:
        for line_number, line in enumerate(fh, 1):
            if line.strip():
                event = json.loads(line)
                assert event.get('schema_version') == 'qrrg_repair_event_v0', (path, line_number)
print('JSONL stress samples parsed successfully')
PY
```

## What the Demo Shows

```text
unit cube / spatial field,
AABB objects,
segment / beam objects,
red / blue carry states,
face / center / overflow states,
SPEC-005 culling region,
inside / intersecting / outside states,
Q-RRG bridge accept / reject / fallback events.
```

## What Is Not Included

```text
no private research notes,
no Don source files,
no private Q-RRG kernel,
no production runtime,
no public SDK,
no Blender/Ogre/OpenGL dependency,
no npm/bundler dependency,
no backend upload.
```

## GitHub Pages Setup

Use repository settings:

```text
Settings -> Pages
Source: Deploy from a branch
Branch: main
Folder: /root
```

If GitHub displays the folder option as `/ (root)`, choose that.
