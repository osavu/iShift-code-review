# TS template structure (new unified template, all RICEFW types)

Source: "TS Template - Unified document" (Oct 2026). Reference only; read when reviewing a TS.
Title placeholder: `<TSD Name>` / "technical specification design document".

## Header and footer
- Header: `<Stream> | <Implementation type> | <RICEFW ID>`
- Footer: "Technical specification for <name of the TS>" and page x/y.

## Front matter
- History & Validation Matrix: columns JIRA US / SNow change | Version | Date | Modified by | Description of main changes.
  Versioning: V0.xx intermediate, V1.0 / V2.0 final.
- Related Documents: Document Name | Description | Document Location (template rows: GPDDXXXX, FDXXXX with a SOLMAN link).
- Document Location: "This document located in SOLMAN" (SolDoc is part of SolMan: same thing).

## Chapters (purpose from the template's own guidance)
1. Document Information
   - 1.1 Overview: high-level technical description, approach, high-level requirements summary.
   - 1.1.1 Entry point: table (type, name) of main objects / T-codes / Fiori tiles that trigger the development.
2. Development Overview (HLD)
   - 2.1 Technical requirements overview: technologies/frameworks, technical needs, reusability.
   - 2.2 Assumptions / Prerequisites (incl. expected behaviour of configuration or other developments feeding this one).
   - 2.3 Dependencies / Constraints (internal/external, access, time, data restrictions, schedule dependencies such
     as jobs that must run first); 2.3.1 Data maintenance requirements / cutover activities.
   - 2.4 Applications, objects or transactions affected.
   - 2.5 Technical flow diagram (screen sequence, drill-downs, navigation).
   - 2.6 Trigger event. 2.7 Execution mode (background / foreground).
3. Detailed Technical Specifications (3.2-3.4 optional: keep only the relevant one)
   - 3.1 Technical object list: Type | Technical name | Description. Only relevant, no minor objects
     (data elements, methods). Types: enhancement/BAdI, user exit, BTE, validation & substitution, screen exit,
     class, table, CDS, structure, domain...
   - Enhancement: program logic (most essential and complex topics only).
   - Form design: driver program logic; form logic (Adobe scripts / Smartforms snippets and conditions).
   - Report details: data selection logic and report flow; input/output file path; additional details.
   - Workflow technical info: definition table (business object/event, template ID, configuration, approval
     levels); template diagram; step/task table (repeated per step); deadline monitoring.
   - 3.5 Integration with other applications.
4. Testing Requirement: 4.1 Performance considerations (mass processing / big volumes).
5. Error Handling: 5.1 error processing logic (+ condition/description table); message logging (application log,
   SRT_MONI, job log, AIF, spool, output log).
6. Transport / Security
   - 6.1 Transport numbers: sequence | SolMan number | TR number | description.
   - 6.2 Security and authorization; 6.2.1 authority checks (object | field value | activity | implication);
     6.2.2 access control for CDS.
7. Appendix: glossary; additional supporting / reference documentation.

Numbering inconsistencies in the template itself are ignored (the actual TS differs; do not check numbering).
