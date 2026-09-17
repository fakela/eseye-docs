# Scope and boundaries

Connectivity Metrics is deliberately focused on connectivity telemetry rather than application data. The boundaries below are design decisions, and they are what allow the service to scale, stay compliant and behave consistently across a global footprint.

### What the service does

* Provides structured, normalised connectivity metadata
* Is operator-agnostic wherever that is technically possible
* Avoids payload inspection entirely

### What the service does not do

* Expose packet payloads
* Guarantee that every operator provides every field
* Provide raw network protocol parity across all networks
* Perform deep application-layer inspection

### Reading these limits

Two of these are worth expanding, because they shape how you model the data.

**Field availability varies by operator:** Some fields, serving network context being the common example, depend on what the operator supplies. Build your pipeline to tolerate absent fields rather than treating them as errors, and expect coverage to differ between networks and countries.

**Protocol parity is not guaranteed:** Networks differ in what they expose and how. Normalisation gets you consistent structure across operators, and it does not manufacture data that a given network never provided in the first place.

Neither limit undermines estate-level analysis. Both are worth knowing before you write queries that assume a field is always populated.

### Related

*
* [Traffic Flow (NetFlow) Metrics](https://claude.ai/cowork/datasets/netflow-metrics.md)
