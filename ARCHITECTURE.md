# The Open Commons Observatory: how the pieces fit

The observatory reflects every project of the open commons in one living picture. Its rule: **the
state of a project lives in the project, as data, and rises into the picture by itself.** Nothing is
wired in by hand, and nothing important lives only in a person's - or an agent's - memory.

## The pieces

**Projects** keep their own state as tad data in their own repository: a board (tasks and their
state), a backlog, a session log (what was done, considered, rejected), and what they measure (test
runs, support status). Their pages render from that data, as every tad project's do.

**The mark** makes a repository a piece of the picture: a small `oco.toml` at its root - which
project it is, what kind (conveyor, device lab, tool, research), its parent, and which of its tad
tables it exports, under which schema version - plus the GitHub topic `oco-project`, so it can be
found. Projects made from a template carry the mark from their first commit.

**The harvest** runs in this repository's CI on a schedule: it finds marked repositories by their
topic, reads their exported tables at their published paths, checks them against the schema their
mark names, and merges them into the observatory's own tad database - every row tagged with the
project it came from. A project that breaks the schema is shown as such; it does not break the
picture.

**The faces** show it all:
- **the website** (this repository's GitHub Pages): the grand views - every project's progress,
  boards and backlogs rolled up, device support as matrices, test history as charts, the landscape
  of other projects we build on - rendered by tad from the harvested data; and each project's own
  site for its detail;
- **the conveyor's command line and board** (devlab, lab-agent): for the people and agents working;
  including the half-manual tests below.

## The linux-phone conveyor

A template repository (linux-phone-oco) holding everything a human or an agent needs to bring
Linux to a phone - tools (devlab and the rest of lab-tools, in Rust), procedures, safety rules,
principles - so that anyone can fork it, point their own agent at it, and work with no setup. Device
labs are made from it, carry the mark, and contribute tools and findings back. Surya is the first
device; the template is the product.

## Half-manual tests

Some checks need a person: does it vibrate, does the sound come out of the right speaker. They are
data like the automatic checks - what to prepare, what to run, what to ask, which answer passes -
and a runner takes them in order: it asks the person to get ready (a dialog that comes up whatever
the desktop, or the board when it is open), runs the test and keeps it running, and asks for the
result while it runs. Results are the same versioned JSON lines as the automatic checks, and the
person is one *observer* among others: a rig - a camera, a microphone, servos pressing buttons -
can take the observer's place later, with nothing else changing.

## Principles for agents and people

- **State in the repository, not in memory**: plans, progress and decisions are committed data.
- **Safety first on the device**: the test phone stays in a known-working state; experiments are
  one-off tries that fall back by themselves (see the conveyor's AGENTS.md).
- **Interoperability research, never code taken**: to learn how hardware works, read what is open
  first - vendor kernel sources published under the GPL, Android's configuration (mixer paths,
  audio routing, device trees) - and observe behaviour (register traces, logs). Studying binary
  blobs is the last resort and only for interoperability, as EU law allows: document behaviour in
  your own words, copy no code, keep notes and implementation apart.
- **Build on what exists**: before building, read the landscape (postmarketOS's hardware CI and
  deviceinfo, Mobian, CI-tron, upstream projects) and fit in rather than beside.

## The order of work

1. The mark and its schema (`oco.toml`, the exported tables); marks on the existing projects.
2. The harvest, and a first grand view on this site from the harvested data.
3. tad's website renderer: charts, matrices, timelines from the data's shape.
4. The conveyor as a template repository, surya's lab made from it.
5. The half-manual test runner and its dialog face; the first test: vibration.
