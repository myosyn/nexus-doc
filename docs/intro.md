---
sidebar_position: 1
---

# Nexus
Nexus is a modular library designed to be both advanced as well as containing features that aren't
in other Kord frameworks. This was originally created because of a few main reasons:

* They are designed for a specific audience
* They do not offer some of the features that I want

At first, this wasn't supposed to exist, as I was going to use JDA. However, because of the fact that
JDA doesn't contain some of the features I need, I had to look for alternatives. 

Due to that, I chose Kord. However, Kord is still in beta, meaning that you shouldn't rely on it for
the most part, and there will be bugs. The same goes for this library. 

## Project Structure

Nexus has most of its functionality split between the core, the commands, and the utilities. This will
explain why we did most of the decisions we did.

### Nexus Commands
Nexus commands were meant to be simplistic, but also incredibly easy to work with. I wanted to combine
the worlds of Discord InteraKTions and Kord Extensions together when making commands. This makes
development of commands a lot easier, as it's a lot more clean and developer friendly. 

Here's an example of that:

```kotlin
class BanCommand: AbstractApplicationCommand() {
    inner class Arguments: ApplicationCommandArguments() {
        val user = user("user", "The user you want to ban.")
        val reason = defaultingString("reason", "The user why the user is going to be banned") {
            defaultingValue = "No reason provided."
        }
    }

    override val arguments: Arguments()

    override suspend fun execute(ctx: ApplicationCommandContext, args: ApplicationCommandArguments) {
        val msg = ctx.respond {
            text = "Well, you done messed up here cowboy!"
        }
        val user = arguments.user
        val reason = arguments.reason

        ctx.guild?.ban(user, reason)
        
        msg
    }
}
```

Maybe this was an excuse to provide more boilerplate, but you'll never know!