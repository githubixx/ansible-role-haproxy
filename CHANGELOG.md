<!--
Copyright (C) 2023-2026 Robert Wimmer
SPDX-License-Identifier: GPL-3.0-or-later
-->

# CHANGELOG

## 0.2.2

- replace injected `ansible_*` facts usage with `ansible_facts[...]` (prepares for ansible-core 2.24 where `INJECT_FACTS_AS_VARS` default changes)
- `tasks/main.yml`: fix forbidden implicit octal values
- `meta/main.yml`: fix ansible-lint issue: Tags must contain lowercase letters and digits only., invalid: ha-proxy
- add `.gitignore`

## 0.2.1

- install `haproxy` with Ansible's `package` module instead of `apt` (contribution by @szymon-filipiak)

## 0.2.0

- introduce `haproxy_k8s_api_endpoint_port` variable
- add Github Actions workflow
- add variable comments

## 0.1.0

- initial implementation
