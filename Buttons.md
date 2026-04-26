# Buttons (discord.py)

Buttons go inside a `ui.ActionRow` and use decorator syntax to assign callbacks — similar to how `@ui.button` works in a regular `ui.View`.

> Requires **discord.py 2.7+**

---

## Button Styles

```python
import discord

discord.ButtonStyle.primary    # blurple
discord.ButtonStyle.secondary  # grey
discord.ButtonStyle.success    # green
discord.ButtonStyle.danger     # red
discord.ButtonStyle.link       # grey with external link icon
```

> `ButtonStyle.link` opens a URL — it does **not** fire a callback. No `custom_id` needed, use `url=` instead.

---

## Basic Button in a CV2 Message

```python
import discord
from discord import ui

class MyLayout(discord.ui.LayoutView):
    row: discord.ui.ActionRow["MyLayout"] = discord.ui.ActionRow()

    @row.button(label="Click Me", style=discord.ButtonStyle.primary)
    async def my_button(self, interaction: discord.Interaction, button: discord.ui.Button):
        await interaction.response.send_message("You clicked it!", ephemeral=True)

@bot.tree.command()
async def hello(interaction: discord.Interaction):
    await interaction.response.send_message(view=MyLayout())
```

---

## Multiple Buttons in One Row

```python
class ConfirmLayout(discord.ui.LayoutView):
    row: discord.ui.ActionRow["ConfirmLayout"] = discord.ui.ActionRow()
