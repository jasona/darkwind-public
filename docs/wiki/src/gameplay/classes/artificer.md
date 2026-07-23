# Artificer

The Artificer implementation is in development but is not player-selectable.
The Brass Crucible is deliberately inaccessible from the Esper shrine and its
attunement rite has a second internal release latch. The class registry remains
live for wizard testing. Once released, class membership, GXP, disciplines,
essence, invention history, and prepared prototypes persist through leveling,
logout, death, and future remorts.

Artificers solve problems by finding the hidden seam between body and soul and
hammering it into useful shapes. Their power is transformation, not ownership
of ordinary crafting: Smiths make excellent equipment; Artificers make an
ordinary thing become impossible for a little while.

## In Play

An Artificer enters danger with a plan, a kit, and a bag full of parts.

- Strike with blacksmith force and furnace heat
- Harvest cinder or cyan ichor from elite and boss enemies
- Temporarily elevate non-unique equipment with those essences
- Prepare persistent one-use inventions rather than mass-producing gear
- Sustain a portable wall and animate a real weapon as an ash construct
- Fabricate a class-gated shoulder projector that consumes SP and blue ash
- Temporarily fold two same-slot unique armours into one chimera working
- Eventually fold a named boss property into one treasured object

Unique equipment is excluded from ordinary tempering. Mature Artificers can
instead perform a costly, reversible chimera artifice: the primary remains
worn while a matching donor unique is reserved inside the temporary working.
This is intentionally stranger and narrower than a conventional item upgrade.

## Body, Soul, And Confluence

| Discipline | Material | Identity |
| --- | --- | --- |
| Body | Cinder, slag, bone, shell | Fire, impact, armor, endurance, Bellows Blow |
| Soul | Cyan ichor, memory, resonance | Lightning, strange light, intent, spectral properties |
| Confluence | Both | Risky hybrid inventions and permanent signature work |

Bosses biased toward strength and constitution yield cinder. Bosses biased
toward intellect and wisdom yield ichor. This is deterministic enough to hunt
for while still making different enemies matter.

Use `artificer study body` or `artificer study soul` to spend five matching
essence on a discipline rank. Once both have a rank, `artificer study
confluence` spends three of each. Discipline ranks currently strengthen
Bellows Blow and matching tempers, and are capped at five.

The disciplines are the finite build. Permanent mastery is the long tail.

## Permanent GXP And Mastery

Artificer GXP belongs to the class soul, not the current body or guild. The
legacy `miInsight` save field remains the storage location so existing class
saves migrate without losing progress. A
remort resets level, stats, and guilds but leaves Artificer progress intact.
Every successful mutation saves immediately, and login repairs a missing class
soul from its canonical path.

The mastery curve is:

```text
mastery = GXP / (GXP + 3,500)
```

Mastery is displayed to one decimal place. It approaches 100% but never uses a
hard rank cap as its power model.

| GXP | Mastery | Standing |
| ---: | ---: | --- |
| 0 | 0.0% | Crucible-marked |
| 1,000 | 22.2% | Tinker |
| 5,000 | 58.8% | Maker |
| 15,000 | 81.0% | Animator |
| 30,000 | 89.5% | Aetherist |
| 60,000 | 94.4% | Heretic |
| 150,000 | 97.7% | Master Artificer |
| 350,000 | 99.0% | Grand Artificer |

The class is therefore practically built after dozens of hours, while a player
with hundreds of hours still gets measurable—very small—improvements. Mastery
scales bounded bonuses such as temper duration, prototype output, and a
percentage of Bellows Blow. It never adds an uncapped flat combat statistic.

GXP sources are intentionally tied to class play:

- Boss harvest: `100 * boss tier`, plus 25 for the killing blow, adjusted by
  the shared kill tracker's repetition percentage
- Build a prototype: 20
- Deploy a prototype: 10
- Single essence temper: 8
- Confluence temper: 15
- Chimera armour: 75
- Portable bulwark: 30
- Awakened weapon: 100
- Aether mount fabrication: 75

Bosses remain the main source. Repeated ordinary attacks do not award GXP,
and repeatedly farming one boss loses GXP through the canonical kill
tracker rather than a new Artificer-only history. Essence still drops so a
player cannot be locked out of their class materials.

## Progression

Artificers advance through boss harvests, prototypes, discipline choices, and
Crucible milestones. This class progression is separate from character level,
guild level, guild XP, and profession skill.

| Threshold | Opens |
| --- | --- |
| Crucible-marked | Resonance, Bellows Blow, boss harvest, basic tempering |
| Body 1 | Cinder ward prototypes and stronger physical/fire work |
| Soul 1 | Ichor coil prototypes and stronger cyan/lightning work |
| Confluence 1 | Dual tempers and starburst prototypes |
| Confluence 2 and 50% mastery | Chimera armour using two matching uniques |
| Confluence 3 | Chimera resistance echo and one additional prototype slot |
| Permanent GXP ranks | Increasing Load for concurrent sustained workings |
| GXP rank 3 and Body 2 | Portable Bulwark |
| GXP rank 4, Body 2, Soul 2 | Awaken Weapon |
| GXP rank 5 and Soul 3 | Aether Mount fabrication and installation |

## Live Abilities

| Ability | Use |
| --- | --- |
| `artificer` / `crucible` | GXP, rank, mastery, Load, ash, essence, disciplines, prototypes, workings, and history |
| `artificer study ...` | Spend essence on Body, Soul, or Confluence ranks |
| `resonate` | Inspect equipment seams or predict a boss's essence affinity |
| Boss extraction | Qualified boss participation automatically harvests essence and GXP |
| `bellowsblow` | Heavy blunt/fire strike; level handles the new body, mastery adds bounded scaling |
| `temper` | Temporarily elevate ordinary weapons or armour with one or both essences |
| `bulwark` | Sustain a folding wall using grey ash, reserves, and one Load |
| `awaken` | Put a real non-unique weapon inside a temporary combat follower |
| `fabricate aether mount` | Build a persistent class-gated shoulder implant |
| `artifice` | Temporarily echo part of one unique armour through another |
| `prototype` | Prepare a persistent invention outside combat |
| `deploy` | Consume a prepared invention; preparation replaces an SP cost |
| `unmake` | List or safely collapse sustained workings, returning reserves and donors |

### Sustained Ashpunk Workings

`bulwark` opens at GXP rank 3 and Body 2. Eight grey ash sustains an armour
bonus for ten to twenty minutes, reserves 4% maximum HP and SP, and consumes
one Load. `unmake` collapses it early.

`awaken <weapon>` opens at rank 4 with Body 2 and Soul 2. Five cinder and five
ichor bind a carried, unwielded, non-unique weapon into a follower for ten to
twenty minutes. The construct physically wields the original weapon, follows
and assists the Artificer, reserves 8% HP and 10% SP, and consumes two Load.
The actual weapon is returned on expiry, dismissal, construct death, logout,
soul teardown, or `unmake`. Unique weapons remain excluded to preserve their
authored identities and Morpher's weapon niche.

At rank 5 and Soul 3, `fabricate aether mount` spends 15 blue ash and five
ichor to create a persistent prototype implant. The standard cyberware system
owns shoulder-slot conflicts, installation, extraction, strain, persistence,
and combat proc dispatch. When installed, the projector has a 25% chance on a
qualifying combat hit, with a six-second proc cooldown, to spend 12 SP and one
blue ash on a bounded magic/lightning shot. It does not fire when the Engine
lacks fuel.

### Temper Results

| Target | Cinder | Ichor | Confluence |
| --- | --- | --- | --- |
| Weapon | Flaming | Shocking | Flaming and shocking |
| Armour | Reinforced | Enchanted | Reinforced and enchanted |

Unique equipment and equipment that rejects the existing modifier contract are
excluded. Tempering uses the established modifier duration and compatibility
rules; it does not rewrite item quality or manufacture a replacement item.

### Chimera Armour

`artifice <primary unique> with <carried unique>` opens at Confluence 2 and
50% mastery. It costs 10 cinder, 10 ichor, 75 immediate SP, 2 Load, and
reserves 5% maximum HP plus 8% maximum SP.
Both pieces must be unique armour with exactly the same slot mask. Rings,
amulets, shields, auras, and all weapons are excluded.

The primary may be worn or carried during creation and remains a real usable
item. The donor is physically reserved by a no-save temporary effect,
continues to count its full carried weight, and is returned when the effect
expires or the player quits. Benefits apply only while the primary is worn;
removing it suspends rather than destroys the seam. Higher permanent GXP
provides enough Load for multiple seams, with a hard cap of three. Duration
scales toward a bounded twenty-five-minute maximum through Confluence and mastery.

The first-generation seam echoes 20–34% of the donor's armour class across
its actual unlock-to-cap progression.
Confluence 3 also echoes the donor's single strongest positive resistance,
capped at 15. It does not clone, consume, rename, rewrite, or manufacture
either unique, and it never invokes the donor's arbitrary wear hooks, combat
callbacks, set bonuses, spells, or bespoke scripts. That limitation is the
point: generic numbers are safe to echo; authored identity is not.

A later extension can let individual unique armours opt into a reviewed
`query_artificer_echo()` mapping. There should be no reflective copying of
callbacks. This gives builders explicit control over unusual synergies and
keeps Morpher's weapon/body identity distinct from Artificer's armour work.

### Prepared Prototypes

| Prototype | Requirement and cost | Deployment |
| --- | --- | --- |
| Coil | Soul 1, two ichor | Focused magic/lightning attack |
| Ward | Body 1, two cinder | General shield scaled to the current body |
| Starburst | Confluence 1, two of each | Bounded eight-target fire/lightning burst |

An Artificer begins with two prototype slots. Permanent mastery gradually opens
three more; Confluence 3 opens a sixth. Prepared counts are primitive persisted
state, so they survive remort without keeping unsafe object references alive.

## Why This Is A Class, Not Another Guild

A guild supplies a combat culture, social identity, restrictions, channels,
and a progression loop for the current life. Artificer sits across those
choices:

- It survives when remort removes all guilds.
- It has no guild level, guild XP, channel, guild hall, or equipment doctrine.
- Its primary rewards come from reading bosses and changing equipment, not
  repeating a guild rotation.
- Prepared inventions work as a loadout. The player decides what future
  problems to pack for instead of receiving another bar of cooldowns.
- Its combat values scale from the current body and then receive bounded
  permanent mastery. A level-1 remort keeps expertise without carrying
  level-250 damage into the new life.
- It makes every guild notice different loot. A Fighter may value a cinder
  hammer, a Mage an ichor focus, and a Thief a compact coil, but none requires
  a guild-specific Artificer branch.

## System Integration

| System | Artificer relationship |
| --- | --- |
| Remort | Membership and class-soul state persist; body stats and guilds reset normally |
| Bosses | Existing `query_boss_tier()` determines harvest strength; no area-specific table |
| Equipment | Existing weapon/armour modifier contracts own compatibility and duration |
| Unique items | Ordinary tempering excludes them; constrained same-slot armour fusion reserves both originals |
| Professions | Own repeatable crafting, quality, repairs, recipes, work orders, and material economy |
| Guilds | Continue to own combat identity; Artificer uses the current body's stats and equipment |
| GMCP | Existing class name remains in `Char.Status`; detailed class state is currently textual |
| Persistence | Primitive class-soul fields plus a nosave runtime working ledger; no persisted object references or callbacks |

Professions can later supply housings, catalysts, lenses, and blanks, but
profession mastery will not gate the class. That creates trade without turning
Artificer into “Smithing, but mandatory.”

## Ability Buildout

The next abilities should deepen transformations rather than add a conventional
spell list.

| Discipline | Candidate ability | Intended niche |
| --- | --- | --- |
| Body | Quench | Convert part of an active cinder temper into immediate defense |
| Body | Magma Ram | Movement/impact strike whose output follows weapon weight |
| Body | Adamant Moment | Briefly keep ordinary armour functional through a breaking hit |
| Soul | Ghostlight Lens | Read concealed magical structure without replacing identify magic |
| Soul | Phase Rivet | Pin a target's position with cyan light rather than a generic stun |
| Soul | Resonant Recall | Recover part of a failed prototype pattern, not its full materials |
| Confluence | Refold | Move a weakened temper between two eligible ordinary items |
| Confluence | Impossible Geometry | Broaden reviewed chimera echoes or prototype slot composition |
| Confluence | Impossible Geometry | Expand only explicitly reviewed unique echoes |

The Cinis Engine replaces the proposed signature ring. It is a class-soul
facade and corpse-burner replacement rather than equipped gear.

## Workbenches And Field Kits

The Cinis Engine is the field kit, ash store, persistent prototype store, and
class soul. It shares the ordinary corpse burner's implementation, retains
`burn`, `check burner`, and `cinis`, and absorbs an existing standard burner
without duplicating its ash or logout event. The Brass Crucible currently
handles class entry; Ashad becomes the canonical class home when available.
