# Cisco CML lab files

Export a versioned CML topology after each approved milestone and place it in this directory.

Recommended Phase 1 filename:

```text
space-city-architects-phase1-topology-v1.yaml
```

Recommended Phase 2 filename:

```text
space-city-architects-phase2-baseline-v1.yaml
```

Keep the working Phase 2 export private unless its saved device configurations have been sanitized. A public milestone export must not contain credential hashes, private keys, or reusable secrets.

Before committing a CML export:

1. Confirm that no passwords, private keys, API tokens, or real public IP addresses are present.
2. Keep the Phase 1 export unconfigured if it is intended to represent the topology-only baseline.
3. Start a new version rather than overwriting evidence from a completed milestone.
4. Record the matching export filename in the relevant phase MOP.
