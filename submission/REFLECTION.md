# Reflection

An anti-pattern relevant to an LLM application is treating the vector index as an independent source of truth. A document may be erased from the lakehouse while its embedding remains searchable in a stale index. The lab reproduces this inconsistency: deleting table rows does not automatically update an external index.

I would keep the lakehouse authoritative and treat the index as rebuildable. A change-data-feed consumer should process inserts, updates and deletes, with durable offsets, idempotent eviction and monitoring of synchronization lag. Search results should also be checked against current access rules. A periodic reconciliation should compare indexed IDs against live table IDs and remove stale entries.

Current-version deletion is only one stage: historical snapshots, object retention, backups and model-training lineage need separate policies. Retention must protect active readers without keeping erased data indefinitely. Zero-retention cleanup in this scratch lab would be inappropriate for a shared production table.

AI assisted execution, verification and drafting; see AI_USAGE.md. This reflection is an AI-assisted draft for the student to review against their own experience.
