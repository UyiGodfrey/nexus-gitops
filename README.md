# Nexus GitOps State Exercise

A small, manual exercise for comparing declared application state with observed state.

## Files

- `gitops/phase-0/desired-state.txt` — the requested state
- `gitops/phase-0/actual-state.txt` — the observed state

The desired state asks for three replicas. The actual state starts at two replicas to make drift visible.

## Compare state

From the repository root:

```bash
diff -u gitops/phase-0/desired-state.txt gitops/phase-0/actual-state.txt
```

The diff shows the replica-count mismatch. A non-zero exit status from `diff` is expected while the files differ.

## Reconcile manually

For this exercise, update `actual-state.txt` so its values match `desired-state.txt`, then run the comparison again:

```bash
diff -u gitops/phase-0/desired-state.txt gitops/phase-0/actual-state.txt
```

No output means the two files match.

## Scope

This repository demonstrates the desired-state comparison manually. It does not yet run a Kubernetes controller or Argo CD reconciliation loop. The next step is to connect the desired manifest to a local cluster and record a real sync and drift-recovery run.
