---
name: ubicloud-network-load-balancing
description: Put Ubicloud VMs behind a firewall and load balancer in a private subnet.
api: openapi/ubicloud-openapi.yml
operations:
- createPrivateSubnet
- createLocationFirewall
- createLocationFirewallRule
- actionLocationFirewallAttachSubnet
- createLocationLoadBalancer
- attachVmLocationLoadBalancer
- getLoadBalancerDetails
generated: '2026-10-09'
method: generated
---

# Put Ubicloud VMs behind a firewall and load balancer in a private subnet.

## Steps
1. Create a subnet with `createPrivateSubnet`.
2. Create a firewall with `createLocationFirewall`, add rules with `createLocationFirewallRule`, attach it with `actionLocationFirewallAttachSubnet`.
3. Create a load balancer with `createLocationLoadBalancer` and add VMs with `attachVmLocationLoadBalancer`.
4. Verify with `getLoadBalancerDetails`.

## Rules
- Auth: `Authorization: Bearer <personal access token>` created on the project Tokens page; base URL `https://api.ubicloud.com`.
- Idempotency: resources are addressed by a name unique per project+location, which the API uses as the idempotency token, so retrying a create with the same reference is safe.
- Errors: 403 = unauthorized user access, 419 = invalid token (from https://www.ubicloud.com/docs/api-reference/overview).
