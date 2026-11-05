# Selling in France / the EU: what it takes

Status: overview, 2026-11-05, from general knowledge. Not legal advice. Check
each point with an official source (or a consultant) before we sell the first unit.

## Who we'd be

When we build and sell under our own name, we are the **manufacturer** in the
EU's eyes, even though the design is Alpenglow's. All the obligations below are
ours. Alpenglow's US sales give us nothing to lean on.

## What applies to the SkeinTwister

| Rule | Why it applies | What we do | Rough cost |
|---|---|---|---|
| **Machinery Regulation (EU) 2023/1230**, replaces the Machinery Directive from **20 Jan 2027** | Motor-driven device with moving parts (pinch/twist hazard) | Risk assessment, technical file, EU Declaration of Conformity, CE mark. Self-assessed: not on the high-risk list, so no notified body | Our time |
| **EMC Directive 2014/30/EU** | PWM motor + microcontroller emit electrical noise | Self-declared, but an emissions/immunity test at a lab is the only real proof | ~1 000 to 3 000 € once per design (to verify) |
| **Low Voltage Directive** | The device runs on 12 V DC: **below the threshold, does not apply to it** | Buy a CE-marked, EU-sourced power supply with its declaration | Part price |
| **RoHS** (no lead etc.) | Electronics | Keep RoHS declarations from JLCPCB and part suppliers | Free |
| **REACH** | Materials | Supplier declarations (SVHC substances) | Free |
| **GPSR (EU) 2023/988**, general product safety, in force since Dec 2024 | Sold to consumers (hobby dyers) | Traceability (batch/serial number), our name + address on the product, safety info on the online listing, incident reporting | Our time |
| **WEEE + packaging EPR (France)** | Electronics and packaging put on the French market | Register as producer with an eco-organism (e.g. ecosystem for electronics, Citeo for packaging), pay a small fee per unit, Triman logo | Small yearly fee (to verify) |
| **Product liability** | A twisting motor can hurt someone | Product liability insurance ("RC produit") | Yearly premium (to verify) |

## The paperwork in practice

1. **Risk assessment**: list hazards (fingers caught, hook flying off, motor overheating, clamp failure) and how the design reduces them.
2. **Technical file**: drawings, schematic, BOM, risk assessment, test reports, standards applied. Kept 10 years.
3. **EU Declaration of Conformity**: one page, signed by us.
4. **CE mark + our name/address + serial number** on the device (UV printer or laser does this).
5. **Instructions in French** (and in the language of each country we sell to), with the safety warnings. The Captain's Guide is a good base.

## Impact on design choices

1. **The finger risk drives everything**: a current-sensing auto-stop (upgrade candidate 3 in ASSESSMENT.md) would make the risk assessment much stronger.
2. **Adding wireless (Bluetooth/Wi-Fi) brings the Radio Equipment Directive** and its cybersecurity rules: much heavier. Rules it out unless it's worth it.
3. **Every design change can mean a new EMC test**: freeze the electronics before testing.
4. **12 V external supply is a gift**: keeps mains voltage out of our box.

## Open questions

1. Did Alpenglow ever CE-test the design? Ask Carrie in the free 30 min call: an existing EMC report would tell us where the risks are.
2. Selling as a company or a micro-entrepreneur: changes insurance and registration, not the CE work.
