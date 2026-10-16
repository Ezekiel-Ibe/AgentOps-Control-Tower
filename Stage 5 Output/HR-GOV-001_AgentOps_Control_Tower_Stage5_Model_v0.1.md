---
title: "AgentOps Control Tower - Stage 5 Model Deliverable"
stage: "Stage 5 - Model"
capabilityId: "HR-GOV-001"
capabilityName: "AgentOps Control Tower"
version: "0.1"
status: "Draft - Review Ready"
classification: "KPMG Confidential"
language: "en-GB"
---

# Document Control

| Field | Value | Evidence |
|---|---|---|
| Capability | Continuous Agent Workforce Management | [SRC-04, Part 1 table] |
| Business agent | HR-GOV-001 AgentOps Control Tower | [SRC-04, section 6.7] |
| Stage | Stage 5 - Model | [SRC-01, Stage 5 heading] |
| Scope | Model all data required within workflow steps and between workflow steps | [SRC-01, Stage 5 Objective] |
| Authoring baseline | Stage 4 classified workflow and handovers | [SRC-06, Workflow Decomposition Catalogue; Handover Register] |

# Contents

1. Stage 5 - Model
2. Common Principles
3. Key Success Factors
4. Common Pitfalls
5. Appendix A - Agent Directory
6. Appendix B - ABBA and Reused Asset References
7. Appendix C - Workflow Step Data Model
8. Appendix D - Entities Consumed by Agents
9. Appendix E - Data Classification Summary
10. Appendix F - Data Gap Log Summary
11. Appendix G - Between-Step Handover Map
12. Appendix H - Assumptions, Constraints and Open Questions
13. Appendix I - Referenced Artefacts
14. Appendix J - Stage 5B Handover Note

# Stage 5 - Model

## 3.1 Objective

Identify and model all data required within each workflow step and between workflow steps for the AgentOps Control Tower workflow (W01-W12), including lineage, ownership, availability classification, and gap capture. [SRC-01, Stage 5 Objective; SRC-06, W01-W12]

## 3.2 Model at Two Levels

### Within each workflow step

Data exchanged between agents, controls and human participants:
- agent execution data and evidence payloads;
- control inputs and outputs;
- human approval records and rationale;
- registry write-back confirmation and closure evidence. [SRC-01, Model at two levels; SRC-06, W01-W12]

### Between workflow steps

Data handed from one step to the next, preserving shared keys and status transitions:
- input package -> validation result -> metric calculations -> governance summary -> eligibility/recommendation -> decision -> registry commit -> closure evidence. [SRC-06, H-001 to H-009]

## 3.3 Data Classification

All data items are classified using Stage 5 categories:
- Enterprise model;
- Other source;
- Not available;
- Agent created;
- Human provided. [SRC-01, Data classification]

## 3.4 Inputs

| Input ID | Input | Usage in this Stage 5 output | Evidence |
|---|---|---|---|
| IN-01 | Workflow steps | Base process decomposition W01-W12 | [SRC-06, Workflow Decomposition Catalogue] |
| IN-02 | Agent inventory | Defines producer/consumer mapping by step | [SRC-06, A-001 to A-012] |
| IN-03 | Component frameworks | Supplies per-agent input/output semantics | [SRC-06, Appendix A] |
| IN-04 | Internal orchestration | Sequences within-step exchanges | [SRC-06, Internal orchestration map] |
| IN-05 | Workflow handovers | Defines between-step data contracts | [SRC-06, H-001 to H-009] |
| IN-06 | Control points | Defines control-consumed data and evidence | [SRC-06, C-001 to C-012] |
| IN-07 | Overall AI framework | Context and governance boundary | [SRC-06, Overall AI Framework] |
| IN-08 | Enterprise data model | Canonical entities and governance objects | [SRC-02, sections 2, 10, 11, 13] |
| IN-09 | ABBA reference | Reuse-aware data schema alignment | [SRC-05, rows for VA-1172, VA-1304, VA-1334] |
| IN-10 | External enterprise-data-model reference | Layer model and canonical table patterns (Silver/Gold/Magenta) | [SRC-03, README and SQL excerpts] |

## 3.5 Actions (1-10) and Completion Evidence

| Action | Applied outcome for HR-GOV-001 | Evidence |
|---|---|---|
| 1. Identify input data for each agent and control | Input sets identified for W01-W12 and A-001 to A-012 | [SRC-06, W01-W12; Appendix A in SRC-06] |
| 2. Identify data created or updated | Created/updated data listed in Appendix C per step | [SRC-06, W11-W12 outcomes; SRC-04, section 6.7] |
| 3. Identify data consumed by controls | C-001 to C-012 data needs mapped | [SRC-06, Control register] |
| 4. Identify data passed to other agents | Within-step transfer chains mapped | [SRC-06, internal orchestration map] |
| 5. Identify data handed to next step | H-001 to H-009 payloads normalised in Appendix G | [SRC-06, Handover register] |
| 6. Define entity, attributes, relationships | Entities and key attributes modelled in Appendices C and D | [SRC-02, sections 10-11; SRC-03, silver.worker/policy/approval/audit_event] |
| 7. Classify data availability | Classification register completed in Appendix E | [SRC-01, Data classification] |
| 8. Log missing data | Missing fields logged as G-01 to G-08 | [Appendix F] |
| 9. Add missing data to model | Gaps represented in model narrative with status | [Appendix C, F, H] |
| 10. Record source and ownership | Ownership fields populated or marked TBC with ACO links | [SRC-06, carry-forward ACO-01/08; Appendix H] |

## 3.6 Outputs

| Output ID | Output | Delivery status |
|---|---|---|
| OUT-01 | Data model per workflow step | Complete (Appendix C) |
| OUT-02 | Entity and attribute definitions | Complete with controlled TBC fields (Appendix D) |
| OUT-03 | Relationships | Complete baseline and gaps logged (Appendix D, F) |
| OUT-04 | Data classifications | Complete (Appendix E) |
| OUT-05 | Data gap log (added to model) | Complete (Appendix F) |
| OUT-06 | Source and ownership | Complete with explicit pending ownership items (Appendix D, H) |
| OUT-07 | Within-step and between-step data flows | Complete (Appendix C, G) |

## 3.7 Practitioner Guidance Applied

- Data traced through each step and onward handover path. [SRC-01, Practitioner guidance]
- Entity and attribute naming aligned to canonical enterprise model conventions where possible (singular snake case). [SRC-03, config/enterprise_model.yml]
- Unsupported items classified as Not available or Other source and logged as gaps. [SRC-01, Data classification; Appendix F]
- ABBA candidates used to avoid duplicate schema assumptions. [SRC-05, selected rows]

## 3.8 Controls and Evidence

| Control evidence requirement | Implementation evidence |
|---|---|
| Evidence of data trace | Appendix C and G link each step payload to source and consumer |
| Data classification recorded | Appendix E |
| Missing data logged and added | Appendix F entries referenced in Appendix C |
| Data lineage documented | Appendix C and D (source lineage fields) |
| Source and ownership recorded | Appendix D ownership columns and Appendix H for unresolved ownership |

## 3.9 Exit Criteria

Exit criteria statement: every agent, control and handover has data requirements modelled with availability classified and gaps added.

Status: Partially met (review-ready; governance ownership and trigger-cadence evidence still pending).

| Exit item | Status | Evidence |
|---|---|---|
| All workflow steps modelled | Pass | [Appendix C, W01-W12] |
| All handovers modelled | Pass | [Appendix G, H-001 to H-009] |
| Classification complete | Pass | [Appendix E] |
| Missing data logged | Pass | [Appendix F] |
| Ownership fully confirmed | Pending | [SRC-06, ACO-01 and ACO-08; Appendix H] |

## 3.10 Deliverable

A complete Stage 5 model package for AgentOps Control Tower, ready for Stage 5B consolidation, with explicit unresolved items carried forward.

## 3.11 Key Tools

- Enterprise data model references (Delivery-Control enterprise object overview and fabric-layer model references);
- ABBA assets;
- Stage 4 handover artefacts;
- Entity and attribute catalogues derived from canonical model patterns. [SRC-01; SRC-02; SRC-03; SRC-05; SRC-06]

# Common Principles

- Model both within-step and between-step exchanges.
- Classify every data item.
- Log and include missing data rather than omitting it.
- Preserve lineage, ownership and control evidence. [SRC-01, Common principles]

# Key Success Factors

- Complete trace from source to consumer.
- Consistent canonical entities and attributes.
- Early capture of gaps and ownership uncertainty.
- Clear control evidence and handover integrity. [SRC-01, Key success factors]

# Common Pitfalls

- Missing handover payload attributes.
- Inconsistent entity naming across steps.
- Assuming data exists without classification.
- Under-specifying ownership and source of control evidence. [SRC-01, Common pitfalls]

# Appendix A - Agent Directory

| Agent ID | Agent name | Agent type | Stage 5 role |
|---|---|---|---|
| A-001 | Fleet Intake and Evidence Validation | Task | Curate and validate governance input package |
| A-002 | Fleet Cost Metering Agent | Task | Derive deterministic cost metrics |
| A-003 | SoD Compliance Control Agent | Control | Check initiator/approver segregation |
| A-004 | Drift Surveillance Agent | Insight | Detect drift signals and severity |
| A-005 | Conformance Coverage Agent | Control | Compute conformance coverage and gaps |
| A-006 | Fleet Governance Summary Agent | Insight | Consolidate metric outputs |
| A-007 | Certification Eligibility Agent | Control | Evaluate in-policy certification eligibility |
| A-008 | Governance Treatment Recommender | Insight | Recommend tune/restrict/retire |
| A-009 | Human Decision Orchestration Agent | Experience | Capture attributable human decisions |
| A-010 | Registry Write-back Agent | Task | Commit approved outcome to registry |
| A-011 | Closure and Audit Evidence Agent | Control | Validate close-out and evidence completeness |
| A-012 | Governance Workflow Orchestrator | Orchestration | Route and sequence all workflow steps |

Evidence: [SRC-06, Workflow Decomposition; Appendix A]

# Appendix B - ABBA and Reused Asset References

| ABBA ID | Asset name | Stage 5 modelling relevance | Data modelling implication |
|---|---|---|---|
| VA-1172 | Data validation agent | Input evidence validation patterns | Reuse validation status and exception fields |
| VA-1304 | Data governance monitor | Compliance control patterns | Reuse policy/check/evidence structures |
| VA-1301 | Data repository manager | Write-back control patterns | Reuse commit/reference/audit fields |
| VA-1334 | System governance orchestrator | Workflow sequencing patterns | Reuse orchestration state payloads |
| VA-1338 | System compliance monitor | Compliance and closure checks | Reuse conformance + closure evidence fields |

Evidence: [SRC-05, referenced rows; SRC-06, Appendix B]

# Appendix C - Workflow Step Data Model

## C.1 Step-level model register

| Step | Inputs consumed | Data created/updated | Control-consumed data | Between-step output | Key entities |
|---|---|---|---|---|---|
| W01 | telemetry_event, agent_activity_log, registry_record, policy_ref | intake_batch_id, intake_status | completeness_flags | validated_input_package_candidate | agent_registry_snapshot (Other source), policy (Enterprise model), audit_event (Enterprise model) |
| W02 | validated_input_package_candidate | validation_result, missing_evidence_list | mandatory_input_rules | validated_input_package | approval (Enterprise model), policy (Enterprise model), missing_evidence_item (Agent created) |
| W03 | validated_input_package | fleet_cost_metric, cost_trace | deterministic_calc_rules | fleet_cost_context | cost_usage_record (Other source), audit_event (Enterprise model) |
| W04 | fleet_cost_context, action_approval_log | sod_violation_flag, sod_evidence_pack | sod_check_rules | sod_checked_context | approval (Enterprise model), audit_event (Enterprise model) |
| W05 | sod_checked_context, eval_telemetry | drift_indicator, drift_severity | drift_threshold_rules | drift_context | model_eval_signal (Other source), audit_event (Enterprise model) |
| W06 | drift_context, conformance_inputs | coverage_percent, conformance_gap_flag | compliance_coverage_rules | conformance_context | policy (Enterprise model), approval (Enterprise model), conformance_result (Agent created) |
| W07 | fleet_cost_metric, sod_violation_flag, drift_indicator, coverage_percent | governance_summary, condition_index | summary_integrity_rule | governance_summary_context | governance_summary_record (Agent created) |
| W08 | governance_summary_context, certification_policy | eligibility_result, policy_boundary_flag | policy_boundary_rules | eligibility_or_review_route | policy (Enterprise model), approval (Enterprise model), eligibility_record (Agent created) |
| W09 | governance_summary_context | treatment_recommendation, recommendation_rationale | recommendation_quality_check | recommendation_pack | recommendation_record (Agent created), audit_event (Enterprise model) |
| W10 | recommendation_pack, eligibility_or_review_route | human_decision_record, approver_rationale | approval_authority_rules | authorised_decision | worker (Enterprise model), approval (Enterprise model), decision_record (Human provided) |
| W11 | authorised_decision or eligibility_result | registry_commit_ref, commit_status | writeback_authorisation_check | committed_outcome | agent_registry_snapshot (Other source), audit_event (Enterprise model) |
| W12 | committed_outcome, trace_logs | closure_record, audit_package, replay_marker | closure_validation_rule | closed_case_evidence | audit_event (Enterprise model), approval (Enterprise model), closure_evidence (Agent created) |

## C.2 Within-step data flows (sample mapping)

| Flow ID | Step | Producer | Consumer | Payload |
|---|---|---|---|---|
| WF-01 | W01 | A-012 | A-001 | trigger_context, source pointers |
| WF-02 | W02 | A-001 | A-003 | validation_candidate_package |
| WF-03 | W04 | A-002 | A-003 | cost_context and activity log |
| WF-04 | W07 | A-003/A-004/A-005 | A-006 | SoD, drift, conformance outputs |
| WF-05 | W10 | A-008 | A-009 | recommendation_pack |
| WF-06 | W12 | A-010 | A-011 | committed_outcome and trace references |

# Appendix D - Entities Consumed by Agents

| Entity ID | Canonical name | Layer/class | Key attributes | Source | Owner | Classification |
|---|---|---|---|---|---|---|
| E-01 | silver.worker | Enterprise model | worker_id, worker_status, organisation_id | enterprise model | TBC - source required | Enterprise model |
| E-02 | silver.policy | Enterprise model | policy_id, policy_version, policy_status | enterprise model | TBC - source required | Enterprise model |
| E-03 | silver.approval | Enterprise model | approval_id, business_object_id, approver_worker_id, approval_status | enterprise model | TBC - source required | Enterprise model |
| E-04 | silver.audit_event | Enterprise model | audit_event_id, business_object_id, event_type, event_timestamp | enterprise model | TBC - source required | Enterprise model |
| E-05 | silver.business_calendar | Enterprise model | calendar_id, calendar_date, accounting_period | enterprise model | TBC - source required | Enterprise model |
| E-06 | agent_registry_snapshot | External source entity | agent_id, domain, status, drift, sod_ok, escalation | AgentReg source and model cards | TBC - source required | Other source |
| E-07 | model_card_reference | External source entity | model_id, model_version, risk_class, conformance_state | model card repository | TBC - source required | Other source |
| E-08 | governance_summary_record | Derived | summary_id, condition_index, generated_timestamp | agent-created | A-006 owner role TBC | Agent created |
| E-09 | human_decision_record | Decision artifact | decision_id, approver_identity, decision_timestamp, rationale | human approval workflow | approver role | Human provided |
| E-10 | missing_evidence_item | Gap artifact | gap_item_id, required_field, source_expected, reason | agent-created during validation | A-001 owner role TBC | Agent created |

Entity evidence: [SRC-02, sections 10 and 11; SRC-03, silver.worker/policy/approval/audit_event excerpts; SRC-04, section 6.7 AgentReg; SRC-06, W01-W12]

# Appendix E - Data Classification Summary

| Data item | Classification | Rationale | Evidence |
|---|---|---|---|
| worker_id, approver_worker_id | Enterprise model | Present in workforce and approval structures | [SRC-02, section 10; SRC-03, silver.worker and silver.approval] |
| policy_id, policy_version | Enterprise model | Present in governance layer | [SRC-02, section 11; SRC-03, silver.policy] |
| audit_event_id, event_timestamp | Enterprise model | Present in governance traceability model | [SRC-02, section 11; SRC-03, silver.audit_event] |
| agent_registry_snapshot.status/drift/sod_ok | Other source | Exists in AgentReg source, not explicit in enterprise model overview | [SRC-04, section 6.7] |
| model_card_reference fields | Other source | Referenced system of record outside canonical entities | [SRC-04, section 6.7 systems of record] |
| governance_summary_record fields | Agent created | Created during workflow summarisation | [SRC-06, W07] |
| missing_evidence_item fields | Agent created | Created when evidence validation fails | [SRC-06, E-001 path] |
| human decision rationale | Human provided | Captured from approver at W10 | [SRC-06, W10 and HIP table] |
| source-system owner identifier | Not available | Required ownership fields unresolved in sources | [SRC-06, ACO-08] |

# Appendix F - Data Gap Log Summary

| Gap ID | Gap description | Impacted steps | Resolution category | Action | Owner | Status |
|---|---|---|---|---|---|---|
| G-01 | Canonical owner role ambiguity (HR Governance Lead vs AI Governance Lead naming) | W10-W12 | Other source alignment | Confirm canonical owner in governance directory | Stage 5 approver | Open |
| G-02 | Source-system owner for agent registry not formally declared | W01, W11 | Not available | Define source-system owner and stewardship | Data governance lead | Open |
| G-03 | Telemetry cadence and trigger taxonomy not fully specified | W01-W03 | Not available | Publish trigger catalogue with SLA | Operations lead | Open |
| G-04 | Drift threshold definitions not explicitly parameterised | W05 | Not available | Add threshold metadata in policy object | Control owner | Open |
| G-05 | Conformance-coverage denominator definition not explicit | W06 | Not available | Document denominator rules and exclusions | Compliance owner | Open |
| G-06 | Certification boundary rule set for L2/L3 not codified in data model | W08 | Not available | Add policy boundary attributes | Governance policy owner | Open |
| G-07 | Registry commit confirmation payload schema not standardised | W11 | Other source alignment | Define commit/ref confirmation schema | Platform owner | Open |
| G-08 | Closure criteria and re-open taxonomy missing formal reference values | W12 | Not available | Add closure status dictionary | Control owner | Open |

# Appendix G - Between-Step Handover Map

| Handover ID | Source step | Target step | Shared key(s) | Data/state handed |
|---|---|---|---|---|
| H-001 | External sources | W01 | event_id, agent_id | telemetry and registry snapshots |
| H-002 | W01 | W02 | intake_batch_id | candidate input package |
| H-003 | W02 | W03 | validation_batch_id | validated input package |
| H-004 | W03 | W04 | run_context_id | costed activity context |
| H-005 | W04/W05/W06 | W07 | assessment_cycle_id | SoD/drift/conformance outputs |
| H-006 | W07 | W08/W09 | summary_id | governance summary and condition index |
| H-007 | W09 | W10 | recommendation_id | recommendation pack and rationale |
| H-008 | W08 or W10 | W11 | decision_id or eligibility_id | authorised decision/eligibility result |
| H-009 | W11 | W12 | commit_ref_id | committed outcome + trace links |

Evidence: [SRC-06, H-001 to H-009]

# Appendix H - Assumptions, Constraints and Open Questions

| ACO ID | Type | Statement | Impact | Owner | Status | Evidence |
|---|---|---|---|---|---|---|
| ACO-01 | Open question | Owner-role label conflict remains unresolved | Ownership fields and approval routing | Stage 4/5 approver | Open | [SRC-06, Controlled carry-forward] |
| ACO-02 | Open question | L2 versus L3 certification boundary not fully codified | W08 eligibility model | Governance lead | Open | [SRC-06, Controlled carry-forward] |
| ACO-03 | Missing information | Trigger and cadence taxonomy incomplete | W01-W03 event modelling | Operations lead | Open | [SRC-06, Controlled carry-forward] |
| ACO-04 | Missing information | Formal closure criteria not fully defined | W12 closure schema | Control owner | Open | [SRC-06, Controlled carry-forward] |
| ACO-08 | Missing information | Data owner and source-system owner details missing | Ownership and stewardship columns | Data governance lead | Open | [SRC-06, Controlled carry-forward] |
| ACO-10 | Constraint | Informational foreign keys require pipeline-level integrity checks | Referential validation controls | Data engineering lead | Open | [SRC-02, section 11; SRC-03, foreign_keys informational note] |

# Appendix I - Referenced Artefacts

| Source ID | Artefact | Role |
|---|---|---|
| SRC-01 | Delivery-Control/Stage_5.md | Stage 5 and 5B methodology authority |
| SRC-02 | Delivery-Control/Enterprise_Business_Data_Objects_Overview_extracted.txt | Enterprise object model baseline |
| SRC-03 | https://github.com/Neill-KPMG/fabric-layer/tree/main/enterprise-data-model | External enterprise-model reference and canonical layer patterns |
| SRC-04 | Source Documents/HR_Capability_and_Full_Agent_Catalogue_v1.md | Capability semantics and AgentReg definition |
| SRC-05 | ABBA-Reuse-Agents/Annotated_Agents_H2RList.csv | Reuse reference inputs |
| SRC-06 | Stage 4 Output/Agent_Ops_Control_Tower_Stage_4_Classify.md | Stage 4 handover baseline |
| SRC-07 | Source Documents/stage-5-document-generation.instructions.md | Stage 5 structure and quality guidance |
| SRC-08 | Source Documents/stage-5-SKILL.md | Stage 5 modelling workflow guidance |

# Appendix J - Stage 5B Handover Note

| Handover metric | Value |
|---|---|
| Workflow steps modelled | 12 (W01-W12) |
| Entities modelled | 10 core entities/artifacts |
| Between-step handovers | 9 |
| Gaps logged | 8 |
| ACO items carried forward | 6 |
| Stage 5B readiness | Ready for consolidation with pending governance ownership and boundary confirmations |

Stage 5B should focus on:
1. end-to-end consistency checks across all step models;
2. relationship and dictionary unification;
3. closure of ownership and policy-boundary gaps;
4. preparation of Design Authority decision record.
