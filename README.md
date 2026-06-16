# Name Tag++

Name Tag++ is a Minecraft Bedrock add-on built as a portfolio project around one familiar vanilla item: the Name Tag. Players rename special Name Tags to discover 35 unique names across five tiers, then use them to transform compatible mobs into companions, stronger enemies, and boss encounters.

I built this project to practice Marketplace style Bedrock systems work: readable Script API gameplay logic, data driven content configuration, custom entity replacement, in game onboarding, combat mechanics, recipes, loot progression, and playtest tooling.

## Portfolio Focus

This project shows my work in:

- Minecraft Bedrock Script API gameplay systems using TypeScript.
- Event driven entity, combat, loot, explosion, and item interaction logic with `@minecraft/server`.
- Custom UI and guidebook flows with `@minecraft/server-ui`.
- A tiered Name Tag transformation system with 35 configured names.
- 42 behavior pack custom entity definitions for companions, enemies, mounts, and bosses.
- State preserving entity replacement for variants, rotation, selected equipment, and companion taming.
- Combat effect systems for regeneration, speed, bonus damage, lifesteal, double hit, triple hit, lightning hits, wither, poison, blindness, taunt, shockwaves, and boss phases.
- Dev commands, playtest kits, and debug overlays for faster in game balancing.
- rgl and esbuild based pack compilation for a cleaner Bedrock add-on workflow.

## Gameplay Systems

### Name Tag Transformation Pipeline

The core system reads a renamed Name Tag, normalizes the name, checks the matching tier, validates the target mob, and applies the correct transformation. Some names modify the original mob directly, while others replace it with a custom entity and then restore important state such as location, rotation, variant, mark variant, and selected equipment.

Companion transformations can tame the result to the player. Enemy transformations create stronger hostile variants with custom behavior, loot, and combat pressure.

### Tiered Progression

Name Tag++ uses five tiers: common, rare, epic, legendary, and mythic. The pack includes custom tier materials, recipes, and loot tables so players can progress from simple companion upgrades into high value encounters. Higher tier tags can use lower tier names, while lower tier tags cannot unlock higher tier transformations.

### Combat and Companion Mechanics

The Script API layer tracks transformed entity effects in memory and refreshes them on schedule. Effects include health boosts, speed changes, regeneration, fire immunity, resistance, bonus damage, lifesteal, multi hit attacks, lightning strikes, wither, poison, blindness, and improved drops.

The combat handlers also manage friendly companion hits, restored melee damage, gilded enemy enrage behavior, golem shockwaves, support effects, and custom boss phase transitions.

### Boss Encounters

The Doom Warden and Chaos Wither use scripted phase behavior instead of only static entity JSON. Doom can run ground slam and sonic boom pressure, with phase two adding a delayed second sonic attack. Chaos applies aura pressure, summons support enemies, and uses explosive attacks after phase changes.

### Guidebook and Onboarding

The project includes a guidebook item, guidebook pages, onboarding prompts, and a starter tutorial. The tutorial gives the player a starter kit and teaches the first transformation by guiding them through renaming a Name Tag to Brave and applying it to a wolf.

### Playtest and Debug Tools

The add-on includes `/scriptevent` driven dev commands gated behind a debug tag. These commands can generate tier specific companion and enemy playtest kits, including matching spawn eggs and correctly named tier Name Tags. A debug action bar can show live combat and cooldown information while testing.

## Tech Stack

- Minecraft Bedrock Behavior Pack and Resource Pack.
- TypeScript source in `data/scripts`.
- `@minecraft/server` for world, entity, event, combat, item, and component logic.
- `@minecraft/server-ui` for guidebook and onboarding UI.
- Custom Bedrock JSON for items, recipes, loot tables, entities, and resource pack client definitions.
- `rgl` with the esbuild filter for compiling TypeScript into the behavior pack.

## Repository Layout

- `data/scripts`: TypeScript source for Script API gameplay logic.
- `packs/BP`: Behavior pack files, custom entities, items, recipes, loot tables, texts, and generated script output.
- `packs/RP`: Resource pack files, entity client definitions, textures, and texts.
- `config.json`: rgl project configuration.
- `package.json`: Script API package dependencies.

## Current Status

This is a prototype and portfolio build. The gameplay scripting, transformation architecture, guidebook flow, custom entities, and playtest tooling are the main focus. Current visual, audio, and icon assets are placeholder assets for prototype review and may be replaced in a future version.

## Links

- [Game Design Document](https://www.notion.so/Name-Tag-GDD-35e4dedd24de81c59437ee4f43213e03)
- YouTube Video: [Watch on YouTube](https://youtu.be/Eipn8S22Qt4)

  [![YouTube Video thumbnail](https://img.youtube.com/vi/Eipn8S22Qt4/hqdefault.jpg)](https://youtu.be/Eipn8S22Qt4)
- [rgl](https://github.com/ink0rr/rgl)

## Download

Download the latest `.mcaddon` from the [Releases page](https://github.com/AdonisZK-Portfolio/NameTagPlusPlus/releases).

1. Open the latest release.
2. Download `NameTagPlusPlus-*.mcaddon` from Assets.
3. Open the downloaded file with Minecraft Bedrock.
4. Enable both the Behavior Pack and Resource Pack in your world settings.

## Development

Install dependencies:

```bash
npm install
```

Install rgl by following the official setup guide on the [rgl project page](https://github.com/ink0rr/rgl).

Start development watch mode:

```bash
rgl watch
```

rgl handles TypeScript compilation and pack output. Source scripts stay in `data/scripts`.
