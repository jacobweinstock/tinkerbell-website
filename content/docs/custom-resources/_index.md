+++
title = 'Custom Resources'
date = 2023-11-15T21:16:38-07:00
draft = false
collapsibleMenu = true # this adds the expander to the menu entry if not already set in your config.toml
alwaysopen = false
ordersectionsby = 'title'
+++

## Custom Resources

The Tinkerbell stack has 3 core Kubernetes [Custom resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) that are used to define and run workflows: `Hardware`, `Template`, and `Workflow`.

Rufio has 3 Custom Resources: `Machines`, `Jobs`, and `Tasks`.
For details on these Custom resources, see the following:

- https://github.com/tinkerbell/rufio/tree/main/config/crd/bases
- https://doc.crds.dev/github.com/tinkerbell/rufio
