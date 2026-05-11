## HISTOS-QA

**HISTOS-QA: Artificial Intelligence System for Slide Quality Assurance and Preprocessing for National Digital Pathology**

A Turkish-led, European-aligned, globally-benchmarked corporate startup developing a regulated AI medical device software (SaMD) for whole slide image quality assurance, preprocessing and downstream readiness in digital pathology. Funded under the TUSEB 2026-C4 programme. Designed and operated to ISO 13485 QMS, IEC 62304 software lifecycle, ISO 14971 risk management, IVDR 2017/746, EU AI Act high-risk obligations, KVKK and GDPR.

```
+------------------------------------------------------+
|   HISTOS-QA  |  Histology Quality Assurance, by AI   |
|              |  TUSEB 2026-C4  |  TR + EU + Global   |
+------------------------------------------------------+
```

## Table of Contents

1. About HISTOS-QA
2. Mission, Vision and Values
3. Project Status
4. What We Build
5. Team and Workstreams
6. Repository Index
7. Tech Stack
8. Engineering Principles
9. Standards and Regulatory Alignment
10. Security and Responsible Disclosure
11. Privacy and Data Protection
12. AI Governance and Responsible AI
13. Quality Management and Auditability
14. Contributing and Code of Conduct
15. Releases and Versioning
16. Roadmap
17. Partners and Clinical Sites
18. Recognition and References
19. License and Intellectual Property
20. Contact
21. Document Control

## 1. About HISTOS-QA

HISTOS-QA is an AI-driven Software as a Medical Device (SaMD) designed to evaluate the technical and analytical quality of whole slide images (WSI) produced by digital pathology scanners before those images are routed to pathologists for diagnosis. The system addresses focus quality, tissue coverage, scanning artifacts, stain consistency, contamination, magnification and metadata integrity. By rejecting or flagging non-conforming slides earlier in the workflow, HISTOS-QA helps laboratories increase throughput, reduce re-scan rates, decrease pathologist cognitive load and improve diagnostic safety.

The project is delivered by a 20-person corporate team operating in startup mode while applying the full discipline of a Class B medical device manufacturer. We are funded by the Turkish Health Institutes Association (TUSEB) under call 2026-C4 and we target three regulated markets in sequence: Turkey via TITCK, the European Union via Notified Body conformity assessment under IVDR and AI Act, and the United States via a subsequent FDA pathway.

## 2. Mission, Vision and Values

### 2.1 Mission

To establish an evidence-based, fair, safe and clinically useful AI gatekeeper that elevates the quality, traceability and efficiency of digital pathology at national and international scale.

### 2.2 Vision

A digital pathology ecosystem in which every slide that reaches a pathologist meets a documented quality bar, every quality decision is explainable, every model is auditable, and every patient benefits from consistent, equitable and timely diagnostic preparation regardless of site, scanner or stain protocol.

### 2.3 Core Values

- Patient safety first.
- Privacy by design, transparency by default.
- Engineering rigor on every pull request.
- Clinical relevance over benchmark vanity.
- Equity across sites, scanners, stains, geographies.
- Open standards, closed PHI.
- Responsible AI from problem framing through post-market vigilance.

## 3. Project Status

- Phase: Year 1 (foundations, federated baseline, internal validation).
- Programme: TUSEB 2026-C4, project HISTOS-QA, duration 2026-02-01 to 2028-01-31 (24 months).
- Headcount: 20 slots (17 active, 3 open data scientist positions).
- Funding: budget 19.7M of 20.0M TL committed plan with 300K reserve.
- TRL: 4 (baseline) to 6 (clinical validation) by month 18, 7 (early deployment) by month 24.
- Regulatory: Turkey TITCK Class B target 2027 Q4; EU IVDR plus AI Act target 2028 Q1; FDA pathway scoped for 2028 to 2029.
- Risk classification: IVDR Class B (with Class C escalation path), EU AI Act high-risk under Annex III, IEC 62304 Software Safety Class B.

## 4. What We Build

### 4.1 Core Capabilities

- WSI ingestion adapters for major scanner manufacturers and DICOM-WSI compliant feeds.
- Lossless normalization to DICOM-WSI and OME-TIFF with metadata preservation.
- Tissue masking and region-of-interest detection.
- Focus quality estimation across the slide surface.
- Artifact detection: pen marks, air bubbles, tissue folds, dust, out-of-focus regions, scanning stripes, color casts, contamination.
- Stain normalization for hematoxylin-eosin and immunohistochemistry workflows.
- Magnification and resolution verification against the requested scanning protocol.
- Pathology report text understanding in Turkish to support quality-evidence pairing.
- Federated learning client and aggregator for cross-site model improvement without raw data exchange.
- Pathologist-facing console with explainable quality verdicts and override workflows.
- FHIR DiagnosticReport rendering for integration with laboratory information systems and PACS.
- Triton-based inference server packaged for hospital-grade deployment.

### 4.2 What HISTOS-QA Is Not

- HISTOS-QA does not provide a diagnosis. It does not predict disease, grade tumors or replace pathologist interpretation. It does not store personally identifiable information beyond the minimum technical metadata required for the quality decision.

## 5. Team and Workstreams

HISTOS-QA is organized into eleven workstreams under a Steering Committee chaired by the PI/CEO.

| Workstream | Lead | Mission |
| --- | --- | --- |
| Program and PMO | Ceren Kaya, PMP (HQ-MBR-003) | Plan, deliver, govern. |
| Core Platform | Co-PI/CTO (HQ-MBR-002) | Shared services, monorepo, integration. |
| Data Engineering | Hande Arslan (HQ-MBR-007) | Ingestion, normalization, lakehouse. |
| Computer Vision | Mert Aydin (HQ-MBR-004) | Models, evaluation, fairness. |
| Federated Learning | Yagmur Erdogan (HQ-MBR-009) | Cross-site training without data exchange. |
| MLOps and SRE | Onur Kilic (HQ-MBR-010) | CI/CD, infra, reliability, security. |
| Clinical NLP | Deniz Yildiz (HQ-MBR-011) | Turkish pathology report understanding. |
| Frontend and UX | Naz Tan (HQ-MBR-015) | Pathologist console. |
| Clinical Affairs | Ahmet Can (HQ-MBR-012) | Sites, protocols, evidence. |
| Regulatory | Esra Ozkan (HQ-MBR-013) | TITCK, NB, FDA, AI Act, KVKK, GDPR. |
| Quality Assurance | Berk Aksoy (HQ-MBR-014) | QMS, verification, audit. |

Leadership: Ozkan Gunalp, MSc (PI / CEO) and Dr. Gustav Olaf Yunus Laitinen-Fredriksson Lundström Imanov, MD, RA, PhD (Co-PI / CTO).

## 6. Repository Index

This organization hosts the source of truth for code, infrastructure, machine learning pipelines, evaluation harnesses and selected documentation bundles. Below is the high-level index. The authoritative inventory with ownership, visibility and purpose is maintained in `HQ-DOC-0009 GitHub Setup and Repository Strategy` in Notion.

### 6.1 Platform and Services

- `histos-qa/platform-monorepo` (Bazel monorepo, shared services).
- `histos-qa/qa-report-service` (FHIR DiagnosticReport renderer).
- `histos-qa/inference-server` (Triton bundles and serving wrapper).
- `histos-qa/console-frontend` (Pathologist console, React).

### 6.2 Data

- `histos-qa/wsi-ingestion` (Scanner and site adapters).
- `histos-qa/wsi-normalize` (DICOM-WSI and OME-TIFF pipeline).
- `histos-qa/wsi-lakehouse` (Delta or Iceberg schemas).
- `histos-qa/datasets-public` (Sanitized data cards, no PHI, public).
- `histos-qa/sample-data` (Synthetic and public WSI samples).

### 6.3 Models

- `histos-qa/cv-focus-qa` (Focus QA model).
- `histos-qa/cv-artifact-detect` (Artifact detection).
- `histos-qa/cv-stain-norm` (Stain normalization).
- `histos-qa/cv-tissue-mask` (Tissue masking).
- `histos-qa/cv-shared-lib` (CV utilities and augmentations).
- `histos-qa/fed-stack` (Federated learning client and aggregator).
- `histos-qa/nlp-path-reports` (Pathology report NER for Turkish).

### 6.4 Evaluation and Validation

- `histos-qa/eval-harness` (Canonical evaluation harness and frozen reference sets).
- `histos-qa/eval-fairness` (Subgroup performance and fairness audit).

### 6.5 Infrastructure and Operations

- `histos-qa/infra-iac` (Terraform, Helm, Argo CD).
- `histos-qa/infra-runners` (Self-hosted runner images).
- `histos-qa/release-tooling` (Release bot, changelog, tagging).
- `histos-qa/sbom-archive` (Archived SBOMs and provenance attestations).

### 6.6 Quality, Regulatory and Security

- `histos-qa/qms-docs` (SOPs and IEC 62304 controlled artifacts).
- `histos-qa/regulatory-pack` (IVDR technical file and AI Act Annex IV).
- `histos-qa/security-policy` (Disclosure policy, [SECURITY.md](http://SECURITY.md), public).

### 6.7 Organizational

- `histos-qa/.github` (Org workflow templates, issue templates, this profile README).
- `histos-qa/onboarding-playground` (Sandbox for new joiners).

## 7. Tech Stack

### 7.1 Languages and Runtimes

- Python 3.11 and 3.12 (data, ML, services).
- TypeScript and React (frontend).
- Go and Rust (selected high-performance components).
- Bash and Make for local orchestration.

### 7.2 Machine Learning and Data

- PyTorch 2.x.
- Lightning, Hydra, MMEngine, MMSegmentation for selected research workflows.
- ONNX and Triton for serving.
- OpenSlide, Bio-Formats, pydicom, dicom-wsi, OME-Zarr for image handling.
- HuggingFace Transformers for NLP components in Turkish.
- Flower or NVFlare evaluated for federated orchestration.
- DVC and LakeFS for data and experiment versioning.
- MLflow for experiment tracking; Weights and Biases for selected workflows.
- Apache Arrow, Parquet, Delta Lake or Apache Iceberg for the lakehouse.

### 7.3 Infrastructure

- Kubernetes (production), Argo CD (delivery), Argo Workflows (pipelines).
- Terraform and Helm.
- GitHub Actions (CI and most CD).
- Hashicorp Vault (secrets).
- Keycloak (SSO and SCIM).
- Postgres, Redis, ClickHouse (selected analytics).
- Object storage (S3-compatible, EU region).
- Observability: OpenTelemetry, Prometheus, Grafana, Loki, Tempo.

### 7.4 Quality and Security Tooling

- CodeQL, Semgrep, gitleaks.
- Trivy and Grype.
- Sigstore cosign, gitsign, fulcio, rekor.
- CycloneDX SBOM.
- in-toto and SLSA provenance.
- OpenSSF Scorecard.
- OWASP ZAP for DAST.

## 8. Engineering Principles

1. Trunk-based development. `main` is always releasable.
2. Conventional Commits. Every commit is a sentence and a story.
3. Tests are not optional. Coverage and behavior matter; flaky tests are bugs.
4. CI tells the truth. If CI is green, the change is ready for review.
5. Reviews are conversations. Approvals are not rubber stamps.
6. Reproducible by construction. Pin versions, lock files, hash everything.
7. Secrets are kept by Vault, not by humans, not by repos.
8. Sign artifacts. Provenance is a feature.
9. Document decisions as ADRs. Future-us will not remember the room.
10. Prefer boring technology where it serves patient safety.
11. Measure to manage. DORA and quality metrics on dashboards, not in heads.
12. Privacy is engineering, not paperwork.
13. Fairness is measured, not assumed.
14. Human oversight is designed in, not bolted on.
15. Post-market is a feature, not an afterthought.

## 9. Standards and Regulatory Alignment

### 9.1 Medical Device

- ISO 13485:2016 Quality Management System.
- ISO 14971:2019 Risk Management.
- IEC 62304:2006/AMD1:2015 Software Lifecycle (Class B baseline).
- IEC 62366-1:2015/AMD1:2020 Usability Engineering.
- IEC 81001-5-1:2021 Health Software Cybersecurity Activities.
- IEC 82304-1:2016 Health Software product safety.
- EU IVDR 2017/746 (Annex I GSPR, Annex II technical file, Annex III post-market, Annex XIII performance evaluation).
- MDCG 2019-11, MDCG 2019-16 Rev.1, MDCG 2022-2, MDCG 2023-4.
- TITCK Tibbi Cihaz Yonetmeligi and IVD Yazilim sınıflandırma.
- FDA SaMD and Good Machine Learning Practice (GMLP) Guiding Principles, PCCP guidance.

### 9.2 Artificial Intelligence

- EU AI Act (high-risk obligations, Annex III healthcare AI, Annex IV documentation).
- ISO/IEC 42001:2023 AI Management System.
- ISO/IEC 23894:2023 AI Risk Management.
- ISO/IEC 5259 series (data quality for analytics and machine learning).
- ISO/IEC TR 24028 (trustworthiness in AI).
- NIST AI Risk Management Framework 1.0.
- IMDRF AI Medical Device Working Group documents.

### 9.3 Information Security and Privacy

- ISO/IEC 27001:2022 Information Security Management.
- ISO/IEC 27002:2022 Controls.
- ISO/IEC 27005:2022 Information Security Risk Management.
- ISO/IEC 27701:2019 Privacy Information Management.
- ISO/IEC 27018:2019 Cloud PII Processors.
- NIST SSDF v1.1 (SP 800-218) Secure Software Development.
- SLSA v1.0 Supply Chain Levels for Software Artifacts.
- KVKK (Law No. 6698) and secondary legislation (VERBIS, ROPA, DSR).
- EU GDPR (Articles 9 special categories, 26 joint controllers, 28 processors, 35 DPIA).
- EO 14028 (SBOM alignment).
- EU Cyber Resilience Act (CRA) draft, vulnerability handling expectations.

### 9.4 Pathology and Clinical Laboratory

- ISO 15189:2022 Medical laboratories quality and competence.
- CAP and CLIA references for analytical concepts (informative).
- DICOM Supplement 145 (WSI), DICOM PS3 specifications, OME-TIFF.
- HL7 FHIR R4 DiagnosticReport, ServiceRequest, Observation profiles.
- IHE Anatomic Pathology Workflow profiles.

A detailed crosswalk lives in `HQ-DOC-0014 Standards and Regulatory Compliance Matrix` in Notion.

## 10. Security and Responsible Disclosure

We operate a Coordinated Vulnerability Disclosure (CVD) programme.

- Read our policy in `histos-qa/security-policy` and in `SECURITY.md` of every repository.
- Acknowledgement target: 72 hours.
- Patch SLAs: Critical 14 days, High 30 days, Medium 60 days, Low 180 days.
- Please do not file public issues for security reports.
- Use the private vulnerability reporting feature on GitHub or contact `security@histos-qa.tr`.
- We support PGP-encrypted reports; the current public key is published in `security-policy`.
- We thank researchers on the Acknowledgements list with explicit consent.

Our supply chain controls include SHA-pinned third-party actions, signed artifacts via Sigstore, SLSA Build Level 3 target, SBOM (CycloneDX) for every release, provenance attestations, and ephemeral hardened runners.

## 11. Privacy and Data Protection

- HISTOS-QA processes special categories of personal data (health data) at clinical sites under joint controller or processor arrangements, depending on site.
- No PHI is ever pushed to GitHub. Datasets used in public repositories are synthetic or public.
- DPIAs are performed for the system and refreshed per clinical site under KVKK and GDPR Article 35.
- We apply pseudonymisation at source, key separation, federated learning with secure aggregation, minimum necessary metadata, strict access controls and full audit trails.
- International transfers use Standard Contractual Clauses with Transfer Impact Assessments.
- Data subject rights are honored via the documented DSR pipeline maintained by the Regulatory function.
- Detailed posture lives in `HQ-DOC-0005 Data Strategy and Governance` and `HQ-DOC-0007 Regulatory and Compliance Plan` in Notion.

## 12. AI Governance and Responsible AI

We treat AI as a first-class risk class. Our governance applies ISO/IEC 42001 AI Management System, ISO/IEC 23894 AI Risk Management and NIST AI RMF 1.0.

- Every released model carries a Model Card and a Data Card.
- Every model is versioned with full lineage from training run to dataset snapshot to evaluation report to deployed artifact.
- Subgroup performance and fairness gaps are measured per release; release gates are defined in `HQ-DOC-0006 Clinical Validation Plan`.
- Distribution shift and calibration are monitored continuously in production.
- A Predetermined Change Control Plan (PCCP) is filed with the Notified Body to manage post-deployment model updates under controlled conditions.
- Human oversight is designed in: clinicians can always override, and the system fails safe to manual review.
- Red-team and adversarial robustness campaigns are run quarterly.

## 13. Quality Management and Auditability

GitHub is a regulated tool in our QMS. We maintain the following traceability chains:

- Notion Task to GitHub PR to Commit to Tag to Release Authorization Record (in `qms-docs`).
- Risk (HQ-RSK) to mitigation PR.
- Requirement (in `qms-docs`) to test (in repo) to test result (CI artifact) to release.
- Architecture Decision Record (ADR) to deployment configuration.
- AI Act Annex IV documentation generated from repository artifacts and signed.

Audit evidence is exported quarterly and on Notified Body audit windows: access reviews, branch-protection snapshots, lists of bypasses, released versions with attestations, CVEs and time-to-patch, CAPAs from code.

## 14. Contributing and Code of Conduct

### 14.1 Contributing

Most repositories are private. External contributions are welcome on public sanitized repositories where indicated.

- Read `CONTRIBUTING.md` in the target repository.
- Use Conventional Commits and DCO sign-off.
- Reference the linked Notion task in commit body and PR description.
- For substantial changes, open an RFC first.
- All contributors must comply with our Code of Conduct.

### 14.2 Code of Conduct

We adopt the Contributor Covenant v2.1 with project-specific extensions covering patient safety, clinical respect, data protection and professional courtesy. Violations may be reported to `conduct@histos-qa.tr` and are handled confidentially under our anti-retaliation policy.

## 15. Releases and Versioning

- Semantic Versioning 2.0.0 per repository.
- Conventional Commits inform automated changelogs.
- Releases are signed via Sigstore cosign; SBOM (CycloneDX) and SLSA provenance are attached.
- For the medical device build, a Release Authorization Record (RAR) is filed in `qms-docs` referencing tag, verification evidence, risk file delta, regulatory impact and approver.
- Production releases require approval by two release-managers and a successful staging plus validation deployment.
- Hotfixes are cut from the most recent release tag with minimal scope and require Steering or QA Lead approval.

## 16. Roadmap

High-level milestones from `HQ-DOC-0007 Regulatory and Compliance Plan` and `HQ-DOC-0001 Project Charter`:

| Window | Milestone |
| --- | --- |
| 2026 Q1 | Programme inception, QMS established, VERBIS registration, baseline models, federated stack alpha. |
| 2026 Q2 to Q3 | Data pipeline production-grade, internal validation, scanner-agnostic generalization tests, DPIA finalized. |
| 2026 Q4 | First clinical site shadow-mode deployment, model card v1.0 set, IVDR technical file v0.5. |
| 2027 Q1 to Q2 | Multi-site validation, fairness audits, post-market surveillance design, Notified Body Stage 1 audit. |
| 2027 Q3 | Notified Body Stage 2 audit. |
| 2027 Q4 | TITCK Class B submission and approval target. |
| 2028 Q1 | EU CE marking under IVDR, AI Act conformity for high-risk, EUDAMED registration. |
| 2028 Q2 to Q3 | First PSUR cycle, broader rollout, FDA pre-submission and submission. |
| 2028 Q4 to 2029 | FDA decision target window, international expansion. |

## 17. Partners and Clinical Sites

- Funder: Turkish Health Institutes Association (TUSEB), call 2026-C4.
- Clinical Advisory Board with representatives from leading Turkish university hospitals.
- Multi-site clinical validation across academic and reference laboratories in Turkey, with planned EU partner sites for external validation.
- Industrial collaborators on scanner integration disclosed under NDA at appropriate stage gates.

Specific partner names and site identifiers are confidential and disclosed only through controlled channels to the Notified Body and regulators.

## 18. Recognition and References

- Project HISTOS-QA acknowledges the foundational work of the digital pathology community, including DICOM Working Group 26, the OME consortium, the OpenSlide project, the Bio-Formats project, the HuggingFace community and the broader open source pathology ecosystem.
- We publish select sanitized findings, data cards and methodological notes through `histos-qa/datasets-public` and through peer-reviewed publications.
- Citations to our work, when permitted, will be listed in `histos-qa/.github/profile/CITATIONS.md`.

## 19. License and Intellectual Property

- Default repository license: proprietary (All Rights Reserved) with internal-use grant.
- Sanitized public repositories use Apache-2.0 only after explicit approval by the PI and CTO, recorded as an `HQ-DEC` decision.
- Inbound license allow-list (examples): MIT, Apache-2.0, BSD 2/3-Clause, ISC, MPL-2.0 (file-level), LGPL (linking reviewed), Python-2.0.
- Disallowed by default: AGPL, SSPL, BUSL, Commons Clause modified licenses, unknown or custom restrictive licenses.
- Third-party content (datasets, weights) must carry compatible licenses; recorded in `LICENSES-THIRD-PARTY.md` in each consuming repository.
- Trademark: HISTOS-QA and associated logos are trademarks of the project legal entity; use requires written permission.

## 20. Contact

- General inquiries: `hello@histos-qa.tr`.
- Engineering: `engineering@histos-qa.tr`.
- Security: `security@histos-qa.tr` (PGP available).
- Privacy and Data Protection: `dpo@histos-qa.tr`.
- Regulatory: `regulatory@histos-qa.tr`.
- Clinical Affairs: `clinical@histos-qa.tr`.
- Media and Press: `press@histos-qa.tr`.
- Conduct and Ethics: `conduct@histos-qa.tr`.
- Postal: address listed on our corporate website.

We respond to security and conduct inquiries with the highest priority. Other inquiries are handled within 5 business days.

## 21. Document Control

| Field | Value |
| --- | --- |
| Document ID | HQ-DOC-0009-A (Annex to HQ-DOC-0009) |
| Title | HISTOS-QA GitHub Organization Profile README |
| Version | 1.0 (Final) |
| Status | Approved |
| Classification | Public-facing on [github.com/histos-qa](http://github.com/histos-qa) |
| Owner | HQ-MBR-002 (CTO) |
| Co-Owner | HQ-MBR-010 (MLOps/SRE) |
| Approver | HQ-MBR-001 (PI / CEO) |
| Effective Date | 2026-02-15 |
| Next Review | 2026-05-15 |
| Source Repo | `histos-qa/.github` at `profile/README.md` |
| Notion Reference | `HQ-DOC-0009 GitHub Setup and Repository Strategy` |

### Version History

| Version | Date | Author | Reviewer | Approver | Summary |
| --- | --- | --- | --- | --- | --- |
| 0.1 | 2026-02-05 | HQ-MBR-002 | HQ-MBR-010 | HQ-MBR-003 | Draft outline. |
| 0.5 | 2026-02-10 | HQ-MBR-002 | HQ-MBR-010, HQ-MBR-014 | HQ-MBR-001 | Internal review draft. |
| 1.0 | 2026-02-15 | HQ-MBR-002 | HQ-MBR-010, HQ-MBR-014, HQ-MBR-013, HQ-MBR-004 | HQ-MBR-001 | Final approved version, public-facing. |
