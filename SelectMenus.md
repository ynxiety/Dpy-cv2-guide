# Select Menus (discord.py)

Select menus go inside a `ui.ActionRow` and use decorator syntax to assign callbacks. One select menu per row.

> Requires **discord.py 2.7+**

---

## Types of Select Menus

| Class | What It Does |
|-------|-------------|
| `ui.Select` | Custom list of options you define |
| `ui.UserSelect` | Pick a user from the server |
| `ui.RoleSelect` | Pick a role |
| `ui.ChannelSelect` | Pick a channel |
| `ui.MentionableSelect` | Pick a user or role |

---

## String Select Menu

```python
import discord
from discord import ui

class MyLayout(discord.ui.LayoutView):
    container = discord.ui.Container(
        discord.ui.TextDisplay("Select a support category below.")
    )
    row: discord.ui.ActionRow["MyLayout"] = discord.ui.ActionRow()

    @row.select(
        placeholder="Choose a category...",
        options=[
            discord.SelectOption(label="General",   value="general",   description="General support"),
            discord.SelectOption(label="Billing",   value="billing",   description="Payment issues"),
            discord.SelectOption(label="Technical", value="technical", description="Technical help"),
        ]
    )
    async def category_select(self, interaction: discord.Interaction, select: discord.ui.Select):
