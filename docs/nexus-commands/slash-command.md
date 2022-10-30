---
sidebar_position: 6
---

# Slash Commands
Slash commands are commands that are executed via Discord's application command feature. 
In order to use these commands, please enable application commands in Nexus' core. 

## Implementation of slash commands
```kotlin
class testCommand: ApplicationSlashCommand() {

}
```
This will enable the given function of slash command for the given function. Your IDE should throw
an error, stating that you do not have an execute function. **THIS IS INTENDED**. This is because
your command will need to be added to an executor in order for functionality to be concluded. 
Otherwise, your command will cease to work. 

If you want to try fixing this error, you need to add the execute function, which your IDE should do
for you if you look into the function.

```kotlin
import live.shuuyu.commands.

class testCommand: ApplicationSlashCommand() {
    override fun execute(ctx: ApplicationCommandContext, args: ApplicationCommandArguments) {
        // TODO: Add later
    }
}
```

## Execution of Slash Commands

To execute the command, add a companion object, and do the following. 

```kotlin
import live.shuuyu.nexus.commands.application.ApplicationCommandArguments
import live.shuuyu.nexus.commands.application.ApplicationCommandContext
import live.shuuyu.nexus.commands.slash.AbstractSlashCommand

class testCommand: ApplicationSlashCommand {
    override fun execute(ctx: ApplicationCommandContext, args: ApplicationCommandArguments) {
        ctx.respond {
            text = "Hello World!"
        }
    }
}

object testExecutor: ApplicationCommandExecutor {
    override fun command = SlashCommand {
        execute(testCommand)
    }
}
```