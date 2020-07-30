# AESTD tag library

A collection of data pack tags for use in other data packs.

## What is this?

[AESTD](https://github.com/Aeldrion/AESTD) is a utility data pack I made for Minecraft 1.14+ for other data pack makers to use.
An important feature of AESTD is its **tag library**, a collection of 200+ item/block/entity type tags with many different use cases.
I have decided to move it to its own repository, for easy access and to include multiple versions of the library (default, expanded, minified).
Tags in this library have a description header, to further explain the criteria when the name itself is ambiguous.

A complete list of tags in this pack can be found on [Pastebin](https://pastebin.com/1TfhsM2p).

## How can use it?

Here are a few examples of things you can do easily thanks to this library:

- [x] Clearing items with an NBT tag:
```mcfunction
clear @a #aestd1:all{example: 1b}
```

- [x] Replacing every non air block with another:
```mcfunction
fill ~ ~ ~ ~15 ~15 ~15 minecraft:obsidian replace #aestd1:all_but_air
```
(or cloning everything but air)

- [x] Testing for an active light source:
```mcfunction
execute if block ~ ~ ~ #aestd1:can_emit_light unless block ~ ~ ~ #aestd1:can_emit_light[lit=false] run ...
```

- [x] Damaging a mob, regardless of type:
```mcfunction
effect give @e[type=#aestd1:undead] minecraft:instant_health
effect give @e[type=#aestd1:mobs, type=!#aestd1:undead] minecraft:instant_damage
```

- [x] Giving a tool that can mine every block in adventure mode:
```mcfunction
give @a minecraft:axe{CanDestroy: ["#aestd1:all_but_air"]}
```

- [x] Detecting when a player eats cooked food:
```json
{
  "criteria": {
    "eat": {
      "trigger": "minecraft:consume_item",
      "conditions": {
        "item": {
          "tag": "#aestd1:cooked_food"
        }
      }
    }
  }
}
```

## Which version should I pick?

The **default** version is the one used in AESTD.

The **expanded** version does not use tag references in tags, making it much heavier but meaning that any tag can be safely removed without invalidating other tags.

The **minified** version removes every occurrence of whitespace in the library's files, making it more lightweight but less readable.

The **expanded, minified** version does not use tag references in tags but removes every occurrence of whitespace in the library's files, making it much heavier than the default version but slightly more lighter than the expanded version.
Like the expanded version, tags can be safely removed without invalidating other tags.
