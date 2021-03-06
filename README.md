Please, note well: this file and the scaffold were generated from [a
template](https://github.com/kubewarden/policy-rust-template). Make
this project yours!

# Kubewarden policy istio-ingress-mutation-networking-v1beta1

## Description

This policy will reject pods that have a name `invalid-pod-name`. If
the pod to be validated has a different name, or if a different type
of resource is evaluated, it will be accepted.

## Settings

This policy has no configurable settings. This would be a good place
to document if yours does, and what behaviors can be configured by
tweaking them.

## SETUP
```
rustup target add wasm32-unknown-unknown
https://rustwasm.github.io/wasm-pack/installer/

cargo build --target=wasm32-unknown-unknown --release
```

```yaml
apiVersion: policies.kubewarden.io/v1alpha2
kind: ClusterAdmissionPolicy
metadata:
  name: istio-ingress-mutation-networking-v1beta1
spec:
  module: registry://ghcr.io/darren-bell-nanthealth/kubewarden-policies/istio-ingress-mutation-networking-v1beta1:latest
  rules:
  - apiGroups: ["networking.k8s.io"]
    apiVersions: ["v1beta1"]
    resources: ["ingresses"]
    operations:
    - CREATE
    - UPDATE
  mutating: true
  settings:
    error_message: "There is a problem with the ingress that has been applied to the cluster, and it cannot be mutated to support Istio"
```
## License

```
Copyright (C) 2021 Darren Bell <darrenarbell@outlook.com>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
