# AutoSupport Telemetry — Runtime Toggle

How to enable or disable the `trident-autosupport` sidecar on an existing
Trident installation.

> This fork ships with AutoSupport **disabled by default**.

---

## Enable AutoSupport Telemetry

1. Edit the controller deployment:

```bash
   kubectl edit deployment trident-controller -n trident
```

2. Locate the container whose `command` is `/usr/local/bin/trident-autosupport`.
   In its `args`, change:

```yaml
   - --trident-silence-collector=true
```

   to:

```yaml
   - --trident-silence-collector=false
```

3. Save and exit. Wait for the rollout:

```bash
   kubectl -n trident rollout status deployment/trident-controller
```

---

## Disable AutoSupport Telemetry

1. Edit the controller deployment:

```bash
   kubectl edit deployment trident-controller -n trident
```

2. Locate the container whose `command` is `/usr/local/bin/trident-autosupport`.
   In its `args`, change:

```yaml
   - --trident-silence-collector=false
```

   to:

```yaml
   - --trident-silence-collector=true
```

3. Save and exit. Wait for the rollout:

```bash
   kubectl -n trident rollout status deployment/trident-controller
```

---

## Operator-Managed Installations

If Trident was installed via the Trident Operator, edits to the deployment
will be reverted by the reconciliation loop. Edit the `TridentOrchestrator`
CR instead:

```bash
kubectl edit torc trident
```

Set `spec.silenceAutosupport` to `true` (disable) or `false` (enable), then
save.
