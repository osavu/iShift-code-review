# Interfaces

Source: QA/ABAP/Fiori strategy deck (slides 15-16, diagrams). Links to the full Interface Delivery Guidelines and the
detailed integration documentation are referenced in the deck; the documents themselves are to be shared.

## Work split
- I1. The S4 work gets an EFS* RICEFW number (`EFS_XXX_XXX`). Middleware / direct connection work uses `IFS_XXX_XXX`.
- I2. Jira implementation type for the S4 work: Dev - Interface. Optional; created only if there are developments
  related to S4 or AIF.
- I3. If AIF configuration is needed, special AIF subtasks (build and dev tech review) are created.
- I4. The ABAP team is responsible only for the S4 implementation.
- Structure: 1 Epic / partner app -> 1 US / RICEFW per side (S4: Dev - Interface; other side: Dev - <Middleware> /
  Dev - Direct Connection), each with interface enhancement subtasks.

## iShift integration strategy (patterns)
- S1. Check first for an out-of-the-box integration (Pattern 1): SAP cloud, vendor packages, ALE/CIF, SAP Commerce/CPI,
  S4/BW certified connectors, integration flows, value mapping.
- S2. Event-driven: reuse an existing API or IDoc if one is already in place.
- S3. Prefer a standard API (Pattern 2). If none, use a standard IDoc (Pattern 4). If the standard IDoc is not
  suitable, consider building a custom asynchronous API.
- S4. Modified interfaces built on IDocs: always evaluate first whether a standard API is available.
- S5. Direct connection: APIs must use Layer 7; SAP-to-SAP direct connection requires the same Sanofi network.
  Tibco acts as middleware for transformation and routing in Patterns 2 and 4.
- S6. Batch (Pattern 3):
  - Inbound: IICS Mass Ingestion with background processing.
  - Outbound: ODP framework combined with IICS.
  - Use Pattern 3 for analytics and batch integrations.
  - High-frequency, low-volume: consider Pattern 2.
  - Inbound batch: check for a standard bulk API; use Pattern 4.2 if message transformation is needed.
  - Massive outbound: Pattern 3 for consolidated data; Pattern 2 if data is not aligned with the SAP Business Model;
    Pattern 3 if consolidation is required.
