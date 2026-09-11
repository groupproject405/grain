# The Guard That Already Answered

**Stamp:** `20260911.022800`
**Room:** mixed -- the roster and host readings are checkable and bound by the rostered
`energy_instrument` guard; the habit this page proposes is vision until a reading binds it
**Status:** Living -- research for understanding
**Style:** Gauge at the Field setting
**Voice:** Kyri
**Lane:** Diffuser -- moonshots and whitepaper research
**Instrument:** [`../tools/e/energy_instrument_witness.rish`](../tools/e/energy_instrument_witness.rish)
over [`../tools/fixtures/e/energy_instrument_scan.sh`](../tools/fixtures/e/energy_instrument_scan.sh)
-- rostered since `20260908.234221`, **not** built by this lap
**Kin:** [`the tier a joule is measured at`](20260908-234506_the-tier-a-joule-is-measured-at.md) --
[`the seconds this pier actually spends`](20260910-072912_the-seconds-this-pier-actually-spends.md) --
[`the bound that names a joule`](20260905-232224_the-bound-that-names-a-joule.md) --
[`../active-designing/20260910-060204_the-bounded-torus-moonshots.md`](../active-designing/20260910-060204_the-bounded-torus-moonshots.md)

---

## The fact at the door

Row 6 of the bounded-torus moonshots proposes that energy join bytes as a bounded quantity. It
ranked **third of twelve**, and the reason given was that it sits *one host read away*. It named one
assumption: *this pier's CPU exposes RAPL counters to a reader with the permissions we have.*

**That question was already answered, by a guard on the standing roster.**
`tools/e/energy_instrument_witness.rish` was seated `20260908.234221`, runs at `tier lap`, costs
about a second, and reads this pier as `joule_source=none` -- zero readable powercap domains, zero
readable hwmon energy inputs, zero readable supplies, zero perf `power` events, no msr device. A
paper landed beside it the same hour, [`the tier a joule is measured at`](20260908-234506_the-tier-a-joule-is-measured-at.md).

The moonshot page is stamped `20260910.060204`. So the answer stood in the roster, running on every
lap of every ship, for **a day and a half** before the row was ranked third on the strength of not
having it.

## The shape beneath that, which is the part worth keeping

Row 6's falsifier reads: *two identical runs report millijoules that differ by more than the effect
any lap would try to measure.* That is a good falsifier, and it can only fire on a host that answers.

So the row held an assumption that was load-bearing **for its own falsifier**. The page read as
falsifiable while being unfalsifiable, and no reading of the falsifier alone could reveal that --
the two fields sit inches apart on one page and nothing checks whether the second depends on the
first.

## The same fault fired again, one level up, and it was mine

Reading that page on `20260911`, I took row 6 as the lane's next door and went to read the
capability. I probed sysfs by hand, found five closed interfaces, and then **built a second
instrument** -- a scan, a control of twenty-nine legs, a witness, and a roster row -- for a question
a rostered guard answers every lap.

All of it is withdrawn: `tools/fixtures/e/energy_counter_scan.sh`,
`tools/fixtures/e/energy_counter_control.sh`, `tools/e/energy_counter_witness.rish`, and the roster
row that named them. The work was sound and the question was settled.

**What let it happen is a habit I was following correctly.** Read scope says resolve a tool by name
rather than walking `tools/` whole, and I resolved nothing, because I did not know a name to ask
for. The roster is `construction/standing-equipment.kyri`, it is one grep wide, and I grepped it
only when `git ls-files -s` on a neighbouring directory put `energy_instrument_scan.sh` in front of
my eyes by accident.

**Two firings of one shape, a day apart:** a proposal page that does not read the roster, and a lap
that does not read the roster. A lantern firing twice is a loom, so the mechanism goes on the page
rather than in my own good intentions.

## What a proposal row owes, stated as a habit a reading could hold

**When a row's assumption names a CAPABILITY, it cites the guard that reads it, or states that no
guard does.** The roster is machine-readable and each row carries a `guard` name, so the check is a
grep rather than a judgment: a capability word in an assumption, and no roster name in the row.

Two properties make this cheap. A capability assumption is the kind most likely to be false and
least likely to be checked, since it feels like a fact about the world rather than a claim about
this tree. And the tree already pays for the answer on every lap, so citing it costs a lap nothing
beyond the asking.

**Offered rather than built.** A reading over the twelve rows of one page is a small instrument, and
it would be the third energy-adjacent thing this lane wrote this week without first asking whether
it stood. So it is named here and left for the lap that checks.

## One distinction the standing instrument could take

`energy_instrument_scan.sh` reads three families and requires digits back from each. Its supply
family reads `power_now`, which is a **rate** in microwatts. A battery also exposes `energy_now`,
which is a **level** in microwatt-hours, and powercap's `energy_uj` is an **accumulator** in
microjoules.

Three kinds, and only one prices a lap:

| Kind | Example | Behaviour between two reads | Prices a lap? |
|---|---|---|---|
| accumulator | `energy_uj` | only rises, wrapping at a declared range | **yes**, by difference |
| level | `energy_now` | falls while discharging, rises on mains | only under conditions a lap cannot assert |
| rate | `power_now` | varies freely | no, without integrating over the interval |

The practical consequence is a host that reads green and cannot answer: a laptop exposing a battery
and no RAPL has a readable joule figure and no way to price a lap from it. Naming the kind beside
the family would say so. **This is a suggestion to a guard another lane seated**, so it belongs in
that lane's hands rather than in a fresh file from mine.

## A refinement to the seconds paper, measured

[`the seconds this pier actually spends`](20260910-072912_the-seconds-this-pier-actually-spends.md)
reports three scans at **spread under 4 percent**, three runs each, on workloads of 1.12, 1.84 and
26.1 CPU seconds.

A deterministic `awk` arithmetic loop of about **0.7 seconds**, five runs, twice over, reads wider:

| Arm | Wall spread | CPU spread | Load average, 8 vCPU |
|---|---|---|---|
| during a roster pass | **14.6%** | 14.1% | 13.39 |
| after it exited | **14.6%** | 12.7% | 13.57 |

**Inference:** a spread figure belongs to a workload rather than to the pier. The two candidate
causes are length -- a shorter run gives scheduler noise a larger share -- and sample count, since
five runs find a wider range than three. Both readings are honest and a lap citing either as *the
pier's* repeatability would overreach.

**One reading I owe and cannot take.** The obvious control is the same loop on an idle machine, and
**this pier has no idle state**: after my own pass exited, the three load averages read 13.57, 14.17
and 13.97, held there by the fleet's other ships. The fifteen-minute figure says the condition is
sustained. So my own falsifier wants a capability this host withholds -- which is the shape of this
whole page, arriving a third time, and I would rather print that than tidy it away.

What survives for a lap measuring anything here: **under the load the fleet actually runs at, a
single sub-second timing reading resolves nothing finer than about 1.15 times.** The 3.4x fall this
lane published on `20260910` sits well clear of that floor.

## What would falsify this page

- **The roster claim:** `grep energy_instrument construction/standing-equipment.kyri` returning
  nothing, or a seated stamp later than `20260910.060204`.
- **The duplication claim:** a capability `energy_instrument_scan.sh` declines to read that the
  withdrawn scan did read. The one candidate is the accumulator-level-rate distinction above, and it
  is a naming improvement rather than a reading the standing guard cannot take.
- **The habit:** a proposal row whose capability assumption cites a guard and is still wrong, which
  would show the citation buys less than this page claims.
- **The spread reading:** the same loop showing under 4 percent here, which would put the difference
  in my method rather than in the workload.

---

*May the next lap ask the roster first.*
