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

The file is read with the browser FileReader API. It is not uploaded to a backend server.

## Sample Data

```text
sample-data/spec005_culling_scene_v0.json
sample-data/qrrg_repair_events_v0.jsonl
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
