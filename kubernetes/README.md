# OpenTelemetry Demo – kpt Package

This directory contains a **kpt package** derived from the official
[OpenTelemetry Demo](https://github.com/open-telemetry/opentelemetry-demo).

The goal of this package is to demonstrate how **kpt pipelines** can be used
to manage, customize, and consistently update large Kubernetes configurations
in a clean and repeatable way.

---

## Problem

In large Kubernetes applications, the same configuration values (for example,
the label `app.kubernetes.io/instance`) are repeated across dozens or even
hundreds of resources.

Manually updating these values:

- Is error-prone  
- Does not scale  
- Makes reviews and long-term maintenance difficult  

---

## Solution

This package uses the **`set-labels` kpt function** to apply the
`app.kubernetes.io/instance` label consistently across **all Kubernetes
resources** in a single step.

By defining this transformation once in the **Kptfile**, the change can be:

- Re-applied safely
- Repeated across environments
- Managed declaratively without editing each manifest manually

---

## Package Structure

```text
kubernetes/
├── Kptfile
├── README.md
├── opentelemetry-demo.yaml
└── package-context.yaml
Usage
1. Get the package
kpt pkg get https://github.com/abhay-codes07/opentelemetry-kpt-demo.git/kubernetes
cd kubernetes
2. View package contents
kpt pkg tree
3. Apply the package
kpt live init
kpt live apply --reconcile-timeout=2m --output=table
Notes

This package is intended as an end-to-end demo for kpt workflows.

The focus is on demonstrating configuration transformation via pipelines,
not on modifying application logic.

The setup can be extended further to support:

Environment-specific overlays

Namespace-level customization

Additional kpt functions

References

https://kpt.dev/

https://github.com/open-telemetry/opentelemetry-demo
