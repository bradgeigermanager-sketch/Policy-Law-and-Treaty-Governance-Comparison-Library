# Governance DAG Visual Specification

This document defines the structure, semantics, and visualization rules for the Governance‑OS Version‑Aware Governance DAG.

The DAG represents the flow of governance authority and impact:

**Instrument → Version → Scope → Participant → Impact**

---

## 1. Node Types

### 1.1 Instrument Node
Represents a treaty, law, or policy.

- Shape: Rectangle  
- Color: `#4A90E2` (blue)  
- Label: `treaty.*`, `law.*`, `policy.org.*`

### 1.2 Instrument Version Node
Represents a time‑bounded version of an instrument.

- Shape: Rounded rectangle  
- Color: `#50E3C2` (teal)  
- Label: `treaty_version.*`, `law_version.*`, `policy_version.*`

### 1.3 Scope Node
Represents jurisdictional or party applicability.

- Shape: Hexagon  
- Color: `#F5A623` (orange)  
- Label: `jurisdiction.*`, `party.*`

### 1.4 Participant Node
Represents an entity subject to governance.

- Shape: Ellipse  
- Color: `#9013FE` (purple)  
- Label: `entity.*`

### 1.5 Impact Node
Represents a time‑sliced unified impact report.

- Shape: Diamond  
- Color: `#D0021B` (red)  
- Label: `report.unified_participant_impact_timeslice.*`

---

## 2. Edge Types

### 2.1 Instrument → Version
Indicates version lineage.

- Style: Solid  
- Color: `#4A90E2`  
- Label: `has_version`

### 2.2 Version → Scope
Indicates applicability.

- Style: Dashed  
- Color: `#50E3C2`  
- Label: `applies_to`

### 2.3 Scope → Participant
Indicates that a participant falls under the scope.

- Style: Solid  
- Color: `#F5A623`  
- Label: `covers`

### 2.4 Participant → Impact
Indicates that an impact report was generated for the participant.

- Style: Bold  
- Color: `#D0021B`  
- Label: `produces`

---

## 3. Layout Rules

- Rank direction: **Left → Right**  
- Instruments appear on the far left  
- Impacts appear on the far right  
- Versions always appear between instruments and scopes  
- Scopes always appear between versions and participants  
- Participants always appear before impacts  

---

## 4. DOT Template

```dot
digraph GovernanceDAG {
  rankdir=LR;

  node [fontname="Arial"];

  // Node styles
  node [shape=rectangle, style=filled, fillcolor="#4A90E2"] instrument;
  node [shape=rect, style="rounded,filled", fillcolor="#50E3C2"] version;
  node [shape=hexagon, style=filled, fillcolor="#F5A623"] scope;
  node [shape=ellipse, style=filled, fillcolor="#9013FE"] participant;
  node [shape=diamond, style=filled, fillcolor="#D0021B"] impact;

  // Example edges
  instrument -> version [label="has_version"];
  version -> scope [label="applies_to"];
  scope -> participant [label="covers"];
  participant -> impact [label="produces"];
}
