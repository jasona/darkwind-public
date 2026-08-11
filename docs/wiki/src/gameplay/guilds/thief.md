# Thief

Thieves turn information, access, and timing into power. Their loop is to
study a mark, create Opportunity through meaningful setup, and spend that
Opportunity on unfair control or a prepared finish. The guild works in PvE,
parties, and dual-guild builds; Bleeding and Exposed are the same common
conditions used by every guild.

## Advancement

Thief uses Guild XP (GXP), not gold. Battle contribution awards normal shared
GXP. Successful jobs award small amounts of Thief GXP and use the kill
tracker's target-reward percentage. Repeating the same action against the
same target blueprint in the same area within thirty minutes pays 100%, 50%,
25%, then 0% job GXP.

Ranks are uncapped. Ranks 1–20 open the command kit; later ranks improve
utility and reliability through Knacks and mastery without repeatedly
multiplying direct damage. Each rank grants one Knack point.

| Rank | Important unlocks |
| --- | --- |
| 1 | `case`, `roll`, `quickstrike`, `dirtyfight`, `tstatus`, `knacks` |
| 2 | coin theft and `palm` |
| 3 | `scout`, `detect`, `extract`, `prepare` |
| 4 | `slip`, `trip`, shadowstep |
| 5 | `hide`, `shadow`, contacts |
| 6 | `peek`, `pick`, `plant` |
| 7 | `envenom`/`poison`, `envenomstrike` |
| 8 | `conceal`, `reveal`, `circle` |
| 9 | `tripwire`; existing traps can be disarmed |
| 10 | `disguise`; discipline Methods after 10 trained Knack ranks |
| 11–13 | `breakin`, `fasttalk`, `forge` |
| 14–16 | `covertracks`, room traps, `frame`, `lace` |
| 17–20 | `disembowel`, `hamstring`, `backstab` |

`tstatus` shows Rank and GXP, Knacks, Opportunity, the Studied target,
incident state, poisoncraft inventory, and selected Methods. `knacks` shows
and trains the three discipline trees.

## Knacks, mastery, and Methods

Each discipline has six five-rank Knacks. A Knack cannot exceed the preceding
Knack in its branch. Completing all six opens that discipline's mastery
track. Mastery has diminishing returns: ranks 1–10 give the largest
improvement, 11–20 give half as much, and 21–30 give one quarter as much.
Later mastery remains prestige and reliability progression.

| Discipline | Theme | Methods |
| --- | --- | --- |
| Ghost | stealth, scouting, locks, escape | Shade, Cat, Runner |
| Grifter | theft, disguise, contacts, schemes | Face, Fence, Agitator |
| Knife | openings, control, poison, finishers | Bleeder, Viper, Opportunist |

After training 10 Knack ranks, choose one active Method in that discipline with
`method <discipline> <method>`. Method swaps are free inside a Thieves Guild
hall. `knacks reset confirm` performs a paid full retrain there.

## Studied and Opportunity

`case <target>` makes one target Studied for two minutes, generates one
Opportunity, and reports visible inventory. A Thief can study only one target
at a time. Switching targets normally retains at most two Opportunity; Ghost
mastery raises that carry limit to three, four, and five.

Opportunity is a living resource with a maximum of five. It expires five
minutes after the last gain or spend; merely remaining in combat does not
refresh it.

- `quickstrike` generates Opportunity when it lands on the Studied target and
  applies canonical Bleeding.
- `dirtyfight` spends one to expose, strike, or blind.
- `trip` spends one to control movement and apply Exposed.
- `circle` spends two and gains bonus damage against any Exposed target
  without consuming the condition.
- `envenomstrike` spends one and forces a landed delivery attempt from the
  current weapon coating while trading away direct damage.
- `disembowel` requires any Bleeding, including Bleeding supplied by a party
  member or another guild. It spends three, benefits from the wound, and never
  consumes it.
- `hamstring` spends two and controls movement for longer against Bleeding
  targets.
- `backstab` requires hiding, a Studied or Exposed target, and at least three
  Opportunity. It spends the full current pool. `astrike` remains a
  compatibility alias.

Thief abilities are meant to chain. Using one applies a two-second recovery to
its broad category, such as damage, stealth, or trickery, and a separate reuse
time to that exact skill. Changing techniques is therefore much faster than
repeating one. Backstab, for example, recovers its damage category after two
seconds but cannot itself be used again for twenty-four seconds.

Thief attacks require a wielded weapon where appropriate but do not impose a
dagger, slashing, or piercing restriction. Equipment eligibility remains
owned by the normal GUILD_D allow/restrict rules.

## Stealth, access, and incidents

`hide` is bounded runtime stealth. Combat or expiry clears it. `slip` breaks
from the current fight and finds cover. `detect` reports trap signs and hidden
exits; `reveal` points out a found exit to everyone present.

There is no separate persistent Heat meter. Thief work records a runtime
incident state: Clear, Suspected, or Pursued. `covertracks` lowers it one
step. The existing reputation and guard systems remain authoritative.
`disguise [laborer|courier|pilgrim|merchant]` gives temporary guard-aware
concealment but never changes the player's security identity or actual
reputation; combat or a new incident breaks it. `contacts` reports local guard
warnings, passes, corruption, and the current bribe estimate. Existing corrupt
guards still own the normal `bribe guard` interaction; Silver Tongue and the
Fence Method can lower its price.

## NPC schemes

`case` works broadly. Plant, Lace, Forge, Frame, and Fast Talk work on visible
intelligent humanoid NPCs in the room. Bosses, pets, mindless creatures,
protected rooms, and unsuitable combatants are rejected automatically; NPC
blueprints do not require Thief-specific hooks.

`forge <npc>` creates one short-lived evidence record bound to the Studied
NPC. `frame <npc>` consumes that evidence and throws your voice, making the
mark appear to insult a randomly selected suitable companion in the room.
Agitators and Thieves with Mastermind rank 5 can work without evidence and may
use `frame <npc> against <npc>` to select the companion. Success starts
immediate NPC-versus-NPC combat. Failure may be ignored or reveal the Thief.
The resulting combat gives the Thief no killer attribution. Frame never loads
other rooms, moves NPCs, or creates a remote grudge.

## Poisoncraft

`extract <corpse>` harvests one bounded reagent and marks the corpse used.
Recipes open every two ranks from ranks 3 through 19. `prepare <poison>
[count]` turns matching reagents into persistent soul-held doses. Reagents
are capped at 100 total; doses at 50 total and 20 per recipe.

`envenom <weapon> with <poison>` and the compatible `poison <poison> on
<weapon>` syntax apply a runtime-only coating. It lasts for three landed
delivery attempts or fifteen minutes, consumes a charge even when resisted,
and never enters equipment save data. Damage and effects are attributed to
the weapon's current wielder. A target can carry at most two distinct Thief
poison effects. Reapplying one refreshes the stronger effect; applying a third
distinct poison expires the oldest.

| Poison | Tactical identity |
| --- | --- |
| Greenbite | basic direct poison damage |
| Widow's Kiss | sustained poison damage |
| Grave Milk | heavy direct dose |
| Nerve Lace | movement disruption |
| Black Lotus Sap | concentration disruption and SP drain |
| Throatdust | short Silence |
| Glassblood | applies or deepens canonical Bleeding |
| Dreamrot | Dexterity/Wisdom impairment |
| Nightshade Reserve | adaptive control |

Legacy poison packets are intentionally discarded rather than migrated.
