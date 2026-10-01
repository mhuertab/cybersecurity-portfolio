# Cloud Security

## Objective

Demonstrate a practical approach to designing and operating cloud environments where security controls are part of the architecture rather than an additional layer added later.

## Areas of Focus

- AWS identity and access controls
- Network exposure and segmentation
- Public vs. private services
- Logging and traceability
- Cloud security monitoring
- Encryption and data protection
- Secure serverless architectures
- Security controls in deployment pipelines

## Reference Approach

A cloud security review should answer four basic questions:

1. **What is exposed?** — Identify internet-facing assets and entry points.
2. **Who can access it?** — Review identities, roles, privileges and trust relationships.
3. **What protects it?** — Evaluate preventive, detective and recovery controls.
4. **Can we detect and respond?** — Validate logging, monitoring, alerting and incident response capabilities.

## AWS Control Layers

`Identity` → IAM, roles, MFA, least privilege

`Network` → VPC, Security Groups, segmentation, controlled ingress/egress

`Application` → secure configuration, WAF where appropriate, authentication and authorization

`Data` → encryption, access policies, backup and lifecycle controls

`Visibility` → CloudTrail, CloudWatch, security telemetry and centralized monitoring

`Response` → alerts, automation, containment and evidence collection

## Security Principle

Cloud security is not only about preventing compromise. It is also about maintaining visibility over the attack surface and being able to understand **what is exposed, why it is exposed, who owns it and which control reduces its risk**.

> This document is a reference scenario and contains no confidential infrastructure information.