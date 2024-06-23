# Novus ActionRow for Nextcord
A while ago, we decided to port our bot Unifier from Novus to Nextcord.

The problem was, the bot had a LOT of MessageComponents, and these were completely 
different from how Nextcord Views worked. So we decided to save some time porting 
things over by implementing Novus' ActionRows to Nextcord by extending its View class.

## Examples
To add a MessageComponent with an ActionRow in Nextcord:
```py
import nextcord
import ui

...

view = ui.MessageComponents() # or ui.View()
row = ui.ActionRow(
    nextcord.ui.Button(
        style=nextcord.ButtonStyle.blurple,
        label='Button 1'
    ),
    nextcord.ui.Button(
        style=nextcord.ButtonStyle.green,
        label='Button 2'
    )
)
view.add_row(row)
await ctx.send(view=view)
```

Or to add multiple ActionRows:
```py
view = ui.MessageComponents() # or ui.View()
row = ui.ActionRow(
    nextcord.ui.Button(
        style=nextcord.ButtonStyle.blurple,
        label='Button 1'
    ),
    nextcord.ui.Button(
        style=nextcord.ButtonStyle.green,
        label='Button 2'
    )
)
row2 = ui.ActionRow(
    nextcord.ui.Button(
        style=nextcord.ButtonStyle.gray,
        label='Button 3'
    ),
    nextcord.ui.Button(
        style=nextcord.ButtonStyle.red,
        label='Button 4'
    )
)
view.add_rows(row,row2)
await ctx.send(view=view)
```

## Limitations
- This is NOT a full re-implementation of discord.ui.ActionRow (from Novus). We
  only reimplemented the functionality that was necessary for us to port Unifier
  to Nextcord.
- Although **theoretically** this should work when using this as a subclass, we
  have not tested this, so proceed with caution.
- Also, auto_defer has been set to False by default, but you may always override
  this.
