# Lightning Wand — Fabric mod (Minecraft 1.20.1)

Egy pálca, amivel jobb kattintással villámot idézhetsz oda, ahová éppen nézel.
Saját 16×16-os textúrával, 1 másodperces cooldownnal, és elérhető a Creative
"Combat" fülön (a szigony mellett), illetve `/give` paranccsal is.

## Miért nincs mellékelve kész .jar?

Ezt a projektet egy olyan sandbox-környezetben állítottam össze, aminek nincs
hálózati hozzáférése a Minecraft/Fabric letöltő szerverekhez (Mojang
könyvtárak, Fabric Maven, Gradle disztribúció), ezért itt nem tudtam lefordítani.
A build viszont teljesen standard, és a te gépeden 2-3 perc alatt lefut.

## Fordítás (build)

Szükséges: **Java 17 JDK** (pl. Temurin/Adoptium) és internetkapcsolat
(a Gradle első futáskor letölti a Minecraftot, a mappingeket és a Fabric API-t).

1. Csomagold ki ezt a mappát valahova.
2. Nyiss egy terminált/parancssort a mappában.
3. Futtasd:
   - Windows: `gradlew.bat build`
   - macOS/Linux: `./gradlew build`
4. Az első futás letölti a szükséges könyvtárakat (ez eltarthat egy darabig),
   utána lefordítja a modot.
5. A kész jar itt lesz: `build/libs/lightningwand-1.0.0.jar`

## Telepítés

1. Telepítsd a **Fabric Loadert** Minecraft 1.20.1-hez
   (https://fabricmc.net/use/installer/).
2. Töltsd le a **Fabric API**-t 1.20.1-hez (Modrinth/CurseForge), és tedd a
   `.minecraft/mods` mappába.
3. Másold a `build/libs/lightningwand-1.0.0.jar` fájlt is a `.minecraft/mods`
   mappába.
4. Indítsd el a Fabric profillal a játékot.

## Használat

- Nyisd meg a Creative inventoryt, keresd meg a "Villámpálca" / "Lightning
  Wand" itemet a Combat fülön, vagy írd be: `/give @s lightningwand:lightning_wand`
- Jobb klikk: villám csap le oda, ahová nézel (max ~50 blokk távolság).
- 1 másodperc cooldown lövések között.

## Projekt felépítés

```
src/main/java/com/lightningwand/LightningWandMod.java   -> item regisztráció, creative tab
src/main/java/com/lightningwand/item/LightningWandItem.java -> a villám-logika
src/main/resources/fabric.mod.json                      -> mod metaadatok
src/main/resources/assets/lightningwand/textures/item/lightning_wand.png -> saját textúra
src/main/resources/assets/lightningwand/models/item/lightning_wand.json  -> item model
src/main/resources/assets/lightningwand/lang/en_us.json, hu_hu.json      -> fordítások
```

Szabadon módosítható: pl. a `RANGE` és `COOLDOWN_TICKS` értékek a
`LightningWandItem.java`-ban állíthatók.
