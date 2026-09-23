# Risk-Oriented Quality

## Principle

Quality Engineering effort should be directed by relevant risk rather than test volume, uniform coverage, or habit.

Not every part of a system has the same impact, likelihood of failure, required test depth, justification for automation cost, or need for confidence.

## Meaning

**Risk guides prioritization.** Quality work should prioritize areas where failures may have relevant business or user impact, affect data integrity or security, cause financial loss or operational disruption, influence legal or contractual outcomes, harm reputation, or reduce delivery confidence. These are examples, not a mandatory taxonomy.

**Risk is contextual.** The same functionality or technology can present different risks in different products. QAOS provides principles and supporting tools; concrete assessment belongs to the project context and should not rely on a universal scoring model.

**Risk includes uncertainty.** Risk includes more than known defects. Limited observability or knowledge, frequent change, complex integration, failure history, external dependencies, and difficult-to-reproduce behavior can justify additional investigation. These signals are not a fixed formula.

**Coverage should follow risk.** Coverage should not be pursued only as a percentage or count. Useful coverage relates to the risks that need to be controlled or understood. High test count does not necessarily mean high confidence.

**Risk changes over time.** Product evolution, architecture changes, usage patterns, incidents, new integrations, team knowledge, and operational experience can alter risk. Prioritization should not be treated as permanent.

**Risk does not eliminate exploration.** A risk-oriented approach does not limit work to already known risks. Exploration remains necessary to discover unknown risks and reduce uncertainty.

```text
known risks
+
unknown risks
+
uncertainty
```

## Why it matters

Quality resources are finite, and testing everything with equal depth is impractical. Automation has implementation and maintenance cost, while higher test volume can add cost without increasing confidence. Explicit prioritization improves decisions and connects Quality Engineering to real product impact without reducing quality work to a purely financial calculation.

## Implications

**Prioritization.** Quality activities should favor areas of higher relevant risk.

**Test depth.** Test depth may vary with risk. A critical flow can justify multiple forms of validation, while lower-impact behavior may need less coverage. This principle does not prescribe test levels.

**Automation investment.** Automation should consider the risk it protects in addition to execution frequency or technical convenience.

**Regression.** Regression strategy should consider potential change impact, dependencies, and historically problematic areas. This principle does not define a global regression strategy.

**Unknowns.** When uncertainty is high, investigation, exploration, or discovery may provide more value than simply adding automated tests.

**Context-specific assessment.** Each project should define its own way to assess and represent risk. It may consider impact, likelihood, exposure, criticality, or uncertainty, but QAOS does not define a universal risk scoring formula.

```text
QAOS principle
      ↓
guides
      ↓
project-specific risk assessment
```

Concrete risk modeling belongs in the client workspace, potentially under `work/context/`, `work/strategy/`, or `work/analysis/` as needed by the project.

## Related

- [[Quality Philosophy]]
- [[Principles]]
- [[Standards]]
- [[Quality Gates]]
- [[Metrics]]
