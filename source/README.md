# Source documents

The privacy policies and terms in Markdown — easier to read and to diff than the HTML. The published
copy is the HTML in the app folders; this is the working copy.

- `privacy-policy.md`, `terms.md` — After Dark: Street War, published at `../afterdark/`.

The next app adds its own pair here, named for the app.

## Keep the two copies in step

Neither copy is generated from the other. **Change both in the same commit, and change the
"Last updated" date in both.** A privacy policy that no longer matches what an app does is worse than
none — it is a statement to players and to Google that is then broken.

## What After Dark's policy says, and why

It was written from that game's code, not from a template. Three things were checked first:

- no analytics package is actually used (the Unity module is in the manifest but nothing calls it);
- the game requests no special Android or iOS permissions;
- the only personal data is an optional email address and a username the player chooses.

The policy states all three plainly rather than hedging. **If any of them stops being true, the policy
is wrong until it is updated.**

## When a policy has to change

- A new SDK, or a change of advert provider or backend.
- Collecting anything new — a new field, a new identifier, a new permission.
- Turning on in-app purchases.
- Reaching a country whose law adds a requirement.
