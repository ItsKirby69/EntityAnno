# `EntityAnno`
Utility tools for generating [`Mindustry`](https://github.com/Anuken/Mindustry)
custom entity component classes. Updated for v151.

This is a temporary fork of [`GglLfr's repository`](https://github.com/GglLfr/EntityAnno) to try and fix issues related to mods unable to be updated beyond v149. THIS REPOSITORY IS NOW REDUNDANT!

## Using this EntityAnno fork
This only concerns mods that use GglLfr's mod template!
Changes you'd need to make (at least from my testings) are as follows:

### `settings.gradle.kts`

```diff
- maven("https://raw.githubusercontent.com/GglLfr/EntityAnnoMaven/main")
+ maven("https://jitpack.io")
///
- id("com.github.GglLfr.EntityAnno") version(entVersion)
+ id("com.github.ItsKirby69.EntityAnno") version(entVersion)
```
### `build.gradle.kts`

We are essentially changing from maven repository to jitpack to make this work. Also replacing all references to the old repository.

```diff
- val useJitpack = property("mindustryBE").toString().toBooleanStrict()
+ val useJitpack = true
///
- id("com.github.GglLfr.EntityAnno") apply false
+ val entVersion: String by project
+ id("com.github.ItsKirby69.EntityAnno") version (entVersion) apply false
///
- val useJitpack = property("mindustryBE").toString().toBooleanStrict()
+ val useJitpack = true
///
- return "com.github.GglLfr.EntityAnno$module:$entVersion"
+ return "com.github.ItsKirby69.EntityAnno$module:$entVersion"
///
if(useJitpack && requested.group == "com.github.Anuken.Mindustry"){
-  useTarget("com.github.Anuken.MindustryJitpack:${requested.module.name}:$mindustryBEVersion")
- }else if(requested.group == "com.github.Anuken.Arc"){
  useVersion(arcVersion)
}
///
- maven("https://raw.githubusercontent.com/GglLfr/EntityAnnoMaven/main")
+ maven("https://raw.githubusercontent.com/ItsKirby69/EntityAnnoMaven/main")
///
- apply(plugin = "com.github.GglLfr.EntityAnno")
+ apply(plugin = "com.github.ItsKirby69.EntityAnno")
///
- mindustryVersion = project.properties[if(useJitpack) "mindustryBEVersion" else "mindustryVersion"].toString()
+ mindustryVersion = project.properties["mindustryVersion"].toString()
```


## Contributing
This project is licensed under [GNU GPL v3](/LICENSE).

## Version Compatibility
| `Mindustry`/`Arc` | `EntityAnno`  | `Use this fork?` |
|-------------------|---------------|------------------|
| `v150`-`v15X`     | `v151.0.2`    |   Should work            |
| `v147`-`v149`     | `v149.0.0`    |   Prefer original            |
| `v146`            | `v146.0.11`   |   Prefer original            |
| `v145`            | `1.1.2`       |   Prefer original            |
| `v144.3`          | `1.0.0`       |   Prefer original            |
