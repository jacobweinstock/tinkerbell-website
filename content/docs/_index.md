+++
title = 'Docs'
date = 2023-11-15T18:32:47-07:00
draft = false
collapsibleMenu = true
alwaysopen = false
weight = 4
+++

Everything you need to know about Tinkerbell and its major components.

## What is Tinkerbell?

Tinkerbell is an open-source, bare metal provisioning engine, built by the team at Equinix Metal.

Interested in contributing? Check out our [Contributors' Page].

## What's Powering Tinkerbell?

- **[Tink Server]** is responsible for serving workflows to Tink Worker for execution and updating the state of workflows and actions as updates are provided by Tink Worker.

- **[Tink Worker]** is responsible for retrieving and executing workflow actions. It reports the state of actions back to Tink Server. Its container image is pull and started by Hook.

- **[Tink Controller]** is responsible for rendering workflow templates and managing workflow state as Tink Worker reports action statuses. It is an internal component that users generally do not interact with.

- **[Smee]** is Tinkerbell's DHCP server.
  It handles DHCP requests, hands out IPs, and serves up [iPXE].
  It only responds to a predefined set of MAC addresses so it can be deployed in an existing network without interfering with existing DHCP infrastructure.

- **[Hook]** is Tinkerbell's default in-memory installation environment for bare metal. Hook starts the Tink Worker so that workflows can be executed that result in a provisioned machine.

### Optional services

- **[Hegel]** is a metadata service that can be used during the provisioning of an OS and used for cloud-init integrations.

- **[PBnJ]** is a gRPC that can communicate with baseboard management controllers (BMCs) to control power and boot settings.

- **[Rufio]** is a Kubernetes controller that facilitates BMC interactions. It functions similarly to PBnJ but with a Kubernetes focused API.

## First Steps

New to Tinkerbell or bare metal provisioning? Visit the [playground] for functional examples that illustrate Tinkerbell stack deployment.

## Get Help

Need a little help getting started? We're here!

- Check out the [FAQs] - When there are questions, we document the answers.
- Join the [CNCF Community Slack].
  Look for the [#tinkerbell] channel.
- Submit an issue on [Github].

[Smee]: /services/smee
[pbnj]: /services/pbnj
[hook]: /services/hook
[hegel]: /services/hegel
[rufio]: /services/rufio
[tink server]: /services/tink-server
[tink worker]: /services/tink-worker
[tink controller]: /services/tink-controller
[cncf community slack]: https://slack.cncf.io/
[contributors' page]: /community/contributors/
[faqs]: /faq/
[github]: https://github.com/tinkerbell
[ipxe]: https://ipxe.org/
[#tinkerbell]: https://app.slack.com/client/T08PSQ7BQ/C01SRB41GMT
[playground]: https://github.com/tinkerbell/playground