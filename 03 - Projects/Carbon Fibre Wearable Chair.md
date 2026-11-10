---
date: 2026-11-10
tags: [project, concept, mobility, design, carbon-fibre, accessibility]
---

# Carbon Fibre Wearable Chair

Concept idea, noted 10 Nov 2026. Design-led project, not a purchase. Related to the
powerchair transport problem: every chair rated for Joel weighs 25–28 kg folded and needs
a hoist or two people to get into a car, so the goal is mobility support that goes on the
body instead of in the boot.

## The concept

- A pair of **trousers** that lock into a seating position, so the wearer can rest in a
  half-sit anywhere.
- Motorised wheels that **clip onto** the trousers.
- The wheels and battery **live in a backpack**.
- Combined, those form a **backwards tripod / chair configuration**.

## Why it's a real gap

A survey of the consumer market (read Oct 2026, third-party research report) found powered
exoskeletons with no seat (Hypershell, Dnsys, Ascentiz, Arc'teryx MO/GO) and wearable seats
with no motor (Noonee Chairless Chair, Archelis), and no product that combines powered
assist with a lockable seat. Joel's version adds the motorised tripod base on top of that.

Closest existing products, for reference, not as suggestions:

- Noonee Chairless Chair 2.0 — passive, 2.95 kg, 130 kg load, ~€2,190 / $2,890.
- Archelis / ArchelisFX — passive, 2.3–2.7 kg, rated around 80–115 kg depending on source.
- Powered hiking exos (Hypershell X, Dnsys X1) — about $999–$1,999, ~2.5 kg, hip assist only.

## Known hard problems

- **Load path.** At 181 kg body mass, the lock joints at hip and knee would carry close to
  full body weight plus dynamic load. The weight has to transfer through a seat and back
  panel into a rigid frame, not through fabric.
- **Tripod stability.** A rearward tripod is statically stable, but braking creates the
  tipping moment that drives the design. Needs checking under dynamic load, not just static.
- **The backpack is the weak point.** A battery big enough for useful range is heavy, and
  putting that mass on the shoulders and spine is the wrong place for a chronically ill
  181 kg user. Worth designing the pack to sit on the base, not the back.
- **Component rating.** Donor parts from bariatric powerchairs are rated around 180–185 kg
  complete. Individual castors and drive wheels built for lighter chairs are not.
- **Regulatory.** A wearable robot intended to support a disabled user is a medical device
  (MHRA / UKCA). ISO 13482 covers safety for personal care robots. Check before building
  anything intended to be worn under load.

## To do

- [ ] Sketch the load path end to end: body → seat panel → trouser frame → wheel base.
- [ ] Fix the design mass and safety factor: 181 kg user, size for dynamic rather than static load.
- [ ] Model the tripod in Blender and find the tipping angle under hard braking.
- [ ] Spec the running gear: castors and drive wheels rated above 181 kg, sourced from bariatric powerchair parts.
- [ ] Design the battery location: base-mounted or axle-mounted, not on the shoulders.
- [ ] Study the closest existing products to see which sub-problems are already solved.
- [ ] Read ISO 13482 and the MHRA route before prototyping anything weight-bearing.
- [ ] Rough a first prototype: 3D print the joint locks at 1:2 scale and test the geometry.
