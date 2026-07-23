# Charlatan

The Charlatans are live on their modern command path. Their many-pocketed
cloak keeps their road training and Rank notes, while their tricks cover
control, volatile ash brews, poison leverage, and temporary loaded weapons.

Charlatans are Wayfarian tricksters who make lies useful. They win by creating
the wrong certainty at the right moment, carrying a pocket for every bad idea,
and ensuring that even their successes have suspicious fine print.

## Progression

Charlatans earn guild XP from level-appropriate combat and bosses. GXP raises
Charlatan Rank; ranks fund road selections rather than a second copy of
classic guild level. `gscore charlatan` shows current rank, XP, roads,
profession gates, and unspent points. Each rank after the first grants one
road point through a total of thirty; use `croads train <road>`. Roads cap at
ten, so Rank 31 provides enough points to complete all three. Later Ranks open
horizontal schemes rather than additional road points. Every new
Charlatan begins with `confuse` and `suckerpunch`; Misdirection improves both
rather than gating the guild's first direct attack.

| Road | Play pattern | Candidate skills |
| --- | --- | --- |
| Misdirection | Control, escape, illusion, social pressure | Improves `confuse` and `suckerpunch`; `distract` at road 2; `avoid` at road 3 |
| Volatility | Dangerous mixtures and bottled weather | `brewacid` and `cookash` at road 1; `brewelement` and `concoct` at road 2 |
| Contraband | Poisons, weapon tricks, rigged objects | `loadweapon` at roads 1-4; `stretchpoison` and `pocketsand` at 2 |

## Advanced Schemes

Beginning at Rank 35, every fifth Rank through 100 opens one scheme in Drina's
ledger. Learning permanently records the scheme in the Charlatan cloak and
costs 1,000 gold per required Rank. A learned scheme can fill an empty active
slot for free; replacing an occupied slot costs half the incoming scheme's
Rank in thousands of gold, with a 25,000 minimum. Drina must be present for
learning and loadout changes.

Charlatans have one active scheme slot initially, two at Rank 50, three at
Rank 100, and another every fifty Ranks thereafter. All fourteen schemes can
be learned by Rank 100, but only three can be active then. `schemes` shows the
catalogue, permanent cloak notes, active loadout, effects, and prices.

Learned schemes and the active loadout remain scribbled in the cloak. Older
cloaks begin with blank scheme pages, while their existing roads and road
points remain intact.

| Rank | Scheme | Road | Sidegrade |
| ---: | --- | --- | --- |
| 35 | Hair Trigger | Contraband | A successful weapon load immediately throws a carried elemental or acid flask at the current foe |
| 40 | Unstable Mixture | Volatility | Elemental throws lose 20% direct damage and apply Burning, Chilled, or lost concentration |
| 45 | Bad Batch | Volatility | Cookash gains two potency, loses 25% duration, and has a 25% chance to become another colour when quaffed |
| 50 | Hot Merchandise | Contraband | Weapon loads last 50% longer and double their fitting side effect |
| 55 | Cut Product | Contraband | Stretch Poison leaves a second weaker owner-bound dose preserving the source poison's special nastiness |
| 60 | Loaded Question | Misdirection | Confuse trades paralysis for a concentration block lasting three seconds longer |
| 65 | Second Story | Misdirection | A resisted Confuse can still create a two-second concentration opening |
| 70 | Improvised Exit | Misdirection | Avoid ends the current fight but its buff lasts half as long |
| 75 | Fine Print | Volatility | Red salt and blue mixer halve immediate recovery and double regeneration duration |
| 80 | Plausible Deniability | Volatility | Volatile throws lose 30% direct damage and no longer splash the thrower |
| 85 | Marked Cards | Contraband | Pocket Sand used on an existing opening applies Exposed instead of Blind |
| 90 | False Bottom | Volatility | Carry two acid and two elemental flasks, each brewed at one lower potency |
| 95 | Double Bluff | Misdirection | Distract applies Exposed instead of attempting to end the fight |
| 100 | The Long Con | Misdirection | Opening-powered Sucker Punch trades half its bonus burst for eight seconds of Exposed |

## Profession Gates

Road investment determines which kind of Charlatan the character is;
profession skill determines whether they can execute the technical parts.
The cloak soul's `extra_gscore()` output shows the three relevant profession
values through `gscore charlatan`.

| Trick | Profession requirement | What practice improves |
| --- | --- | --- |
| `brewacid`; `brewelement`; grey / red-blue / mixed `cookash` | Alchemy 25; 75; 25 / 75 / 150 | Stronger batches; aim for 100 ash when cooking a proper rush |
| Red salt and blue mixer | Alchemy 75 | Lingering recovery, up to 30 each pulse |
| Cutting bitters | Herbalism 50 | Unlock only |
| Dazzling / oiled weapon load | Alchemy 50 / 70 | Treatment strength and duration |
| Poisoned / flaming / frozen load | Alchemy 100 | Treatment strength and duration |
| Silvered load | Alchemy 125 and Smithing 50 | Uses the lower effective discipline and one Silver Bar |
| Shocking load | Alchemy 150 | Treatment strength and duration |
| `stretchpoison` | Alchemy 100 | Dose strength and duration |

Guild actions do not award profession skill directly. Players advance the
professions through their owning systems, preserving profession rooms,
materials, recipes, and advancement loops.

## Potions Without Replacing Professions

Alchemy owns dependable recipes, healing, stat support, work orders, and a
repeatable market. Charlatan mixtures are encounter tools:

- narrow and short-lived;
- frequently thrown, smeared, or planted rather than consumed;
- made from stolen, substituted, or profession-sourced ingredients;
- guaranteed to carry a side effect, tell, delayed crash, or backfire chance;
- poor merchandise unless the buyer enjoys waivers.

Elemental bottles return as volatile surprises. Healing and clean stat potions
do not return as core Charlatan products. A Charlatan may adulterate a
profession potion later, but does not replace the profession recipe.

`brewacid` requires guild rank 2, Volatility 1, and Alchemy 25. It makes one
owner-bound base flask, which may be thrown as a modest acid surprise or used by
`cookash <grey|red|blue|mixed>` (legacy alias `ccook`). Cook Ash uses every
available ash of the selected colour; mixed uses every colour. A single batch
needs at least 10 relevant ash, while mixed needs at least 10 of each. Grey
requires Alchemy 25, red/blue 75, and mixed 150.

`brewelement <fire|ice|lightning>` (alias `elementpotion`) requires guild rank
3, Volatility 2, and Alchemy 75. It creates one owner-bound, two-hour
elemental flask. `throw <element> flask at <target>` deals the corresponding
elemental harm, consumes the flask, starts combat, and kicks some of the blast
back onto the thrower. In combat the explicit target may be omitted. The usual
rules for reaching, seeing, and attacking a target still apply.

Quaffing the result creates a buff-visible Cookash Rush: grey favors accuracy
and defense, red favors damage, blue favors accuracy and an extra swing,
and mixed blends the offensive benefits at lower strength. Aim for 100 ash for
a proper batch. More still stretches the rush, but the difference soon becomes
difficult to notice; no rush lasts longer than thirty minutes. Only one rush
may run at once. The vial belongs to its maker, cannot be sold, and goes flat
after two hours. Throwing it deals elemental harm and always splashes the
thrower. The cloak needs only a few seconds before it can cook another.

### Food And Drink Additives

`concoct <red salt|blue mixer|cutting bitters>` (alias `cmix`) requires guild
rank 2 and Volatility 2. It creates a transferable, no-save additive that
expires after thirty minutes. `mix <additive> into <carried food or drink>`
uses one packet on the entire carried serving; each item accepts only one.
An additive cannot improve fare meant for someone more experienced than its
maker, and even the finest packet tops out at Epic fare.

| Additive | Ash | Benefit | Fine print |
| --- | ---: | --- | --- |
| Red restorative salt | Alchemy 75; 4 red | Better health recovery and a restorative aftertaste, up to 30 each pulse | Immediate SP drain |
| Effervescent blue mixer | Alchemy 75; 4 blue | Better spirit recovery and a refreshing aftertaste, up to 30 each pulse | Small acid bite |
| Cutting bitters | Herbalism 50; 3 grey | Better recovery and a meal that is easier to stomach | Brief concentration block |

The additives work on profession fish, wildcrafted meals, pub food, and
ordinary drinks. One packet treats every use of a meal, snack, keg, or jug;
refillable containers lose the treatment when emptied. A fresh helping of the
same seasoning refreshes its aftertaste rather than stacking it. Inspection
and consumption messages reveal the strength and duration of the lingering
recovery.

## Poisons And Modifications

Charlatans should consume existing poison items or profession reagents and
improve delivery: conceal a dose, stretch its duration at reduced strength,
mix two weak toxins, or trigger a secondary distraction. They do not need a
parallel poison catalog.

The caravan shops still sell ordinary throwing darts, whose item-owned
`throw <target>` action remains live. The old poison-dart coating skill,
pegasus-wing potion recipe, smoke packets, and special potion bottles belonged
to the retired Alchemy/Illusion focus tree and are no longer shop stock.

Every loaded weapon has a drawback: noise, brittleness, self-exposure, a
delayed crash, or a chance to mark the user. Unique gear remains off limits.
The cloak is good at temporary, questionable improvements—not reputable
craftsmanship.

`loadweapon` gives a carried, unwielded, non-unique weapon a temporary razzled,
oiled, silvered, flaming, frozen, poisoned, or shocking treatment.
Dazzling opens at Contraband 1/Alchemy 50; oiled and poisoned at Contraband 2
with Alchemy 70/100; flaming and frozen at Contraband 3/Alchemy 100; silvered
at Contraband 4, Alchemy 125, Smithing 50, and one Silver Bar; shocking at
Contraband 4/Alchemy 150. Each has installer-side fine print. `flash`, `oil`,
and `quicksilver` remain parsing aliases. Serration was removed.

Flaming strikes can leave a foe Burning, frozen strikes can leave one Chilled,
and dazzling weapons have a very rare chance to steal a foe's train of thought.
Sharpened gear can very rarely leave a foe Bleeding. Oiled weapons become
markedly easier to place as soon as they are ready again.

`stretchpoison` opens at guild rank 3, Contraband 2, and Alchemy 100. It
consumes an existing poison, smears a weaker but longer-lasting version onto a
compatible weapon, preserves the poison's special nastiness, and poisons the
installer. Fair is fair.

## Sucker Punch

`suckerpunch [foe]` (alias `spunch`) is a baseline guild-rank-1 attack. It
turns the Charlatan's weapon, physical talent, and Misdirection into one unfair
melee hit. A foe already paralyzed or unable to concentrate leaves room for a
much harder blow, making `confuse` and `distract` natural setup tools. At
Misdirection 4, a second wielded weapon joins the pitch. This is still a
close-range trick; confidence cannot punch across a room.

## Distract

At guild rank 3 and Misdirection 2, `distract` throws the Charlatan's voice
somewhere inconvenient and disrupts a foe's concentration. With deeper
Misdirection, the mark may briefly forget whom they were fighting at all.

## Live Commands

| Command | Gate | Purpose |
| --- | --- | --- |
| `charlhelp` / `chelp` | Member | Modern guild topics and live command help |
| `chskills [available]` / `cskills` | Member | Ability syntax, costs, cooldowns, unlock requirements, and current availability |
| `charlatan` / `cchat` | Member | Primary guild chat; `echarlatan`/`ecchat` manually emotes |
| `chist [lines]` | Member | Recent Charlatan line history |
| `cwho` / `charlatans` | Member | Themed visible-member roll with credentials, dominant-road calling, and status |
| `gscore charlatan` | Member | Rank XP plus soul-provided roads, unspent points, and profession gates |
| `croads train <road>` | Rank-earned point | Invest in Misdirection, Volatility, or Contraband |
| `schemes` / `cons` | Rank 35+ | Inspect, learn, activate, and swap cloak-recorded schemes; changes require Drina |
| `confuse` | Rank 1 | Brief charm-based daze |
| `suckerpunch` / `spunch` | Rank 1 | Melee payoff for a controlled opening; Misdirection improves it |
| `brewacid` | Rank 2, Volatility 1, Alchemy 25 | Makes the base flask for Cook Ash |
| `brewelement` / `elementpotion` | Rank 3, Volatility 2, Alchemy 75 | Bottles fire, ice, or lightning for throwing |
| `cookash` | Rank 2, Volatility 1, Alchemy 25+ | Converts all relevant ash into a timed combat rush |
| `concoct` / `cmix` | Rank 2, Volatility 2, profession 50+ | Expiring food/drink additive |
| `loadweapon` | Rank 2, Contraband 1+, profession 50+ | Temporary loaded treatment |
| `distract` | Rank 3, Misdirection 2 | Concentration control/disengage chance |
| `stretchpoison` | Rank 3, Contraband 2, Alchemy 100 | Dilute an existing poison onto a weapon |
| `avoid` | Rank 4, Misdirection 3 | Short buff-visible defensive footwork |
| `pocketsand` | Rank 4, Contraband 2 | Attempt to blind a foe |
