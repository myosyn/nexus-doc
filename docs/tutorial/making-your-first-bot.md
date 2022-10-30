---
sidebar_position: 0
---

# Making your first bot
In order to make your first bot, please make sure that the Nexus package is in your dependency list. 
If it isn't, everything won't work. 

To do this, locate your Maven or Gradle package. Gradle is highly recommended for larger projects. 
**Make sure you have Kotlin equivalent to the most recent Kord release or else your bot will fail to 
compile, as Kord does some wonky stuff with Kotlin versions, which results in errors.**

The most recent Kord snapshot supports 1.7.10.

```kotlin
plugins {
    kotlin("jvm") version "1.7.10"
    kotlin("plugin.serialization") version "1.7.10"
}

repositories {
    mavenCentral()
    // For Kord releases
    maven("https://oss.sonatype.org/content/repositories/snapshots")
    // For those who want the bleeding edge
    maven("https://maven.shuuyu.live/repositories/snapshots")
    // For those who want stable releases
    maven("https://maven.shuuyu.live/repositories/releases")
}

dependencies {
    // This will bundle both Kord and Nexus, so no need to fret.
    implementation("live.shuuyu.nexus:core:0.0.1-SNAPSHOT")
}
```

