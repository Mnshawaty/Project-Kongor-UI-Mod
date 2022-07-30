# Project Kongor UI Mod

HoN Mod to enable the custom Project Kongor UI: homepage, ladder, etc

## Details

### Ladder

The ladder URLs are constructed in `ui/scripts/web_panel.lua`. For the two main ladders (player -- i.e. MMR -- and mastery), there are functions
that return the URLs. Instead of returning a fixed value, these methods already check for the existence of cvars and prefer to use that.

The mod sets the cvars with a `SetSave(...)` inside of corresponding functions, rather than just hijacking the `url` local variable.

- Player (MMR) Ladder - `function HoN_Web_Panel:ShowLadder(widget)`

  Sets the cvar `ui_url_playerLadder`.

- Mastery Ladder - `function HoN_Web_Panel:ShowMasteryAllLadder(widget)`

  Sets the cvar `'ui_url_playerMasteryAllLadder'`.

### MoTD (Message of the Day)

There are two modifications done (one for the new UI and one for the old UI). Essentially there is Lua code to construct the URL and the
mod overrides that return value to return a hardcoded string.

- ui/scripts/newui/homepage_v2.lu

  Return value for the new UI is returned from `function Homepage_V2:GetMotdURL()`.

- ui/scripts/news.lua

  Return value for the old UI is returned from `local function getMOTDURL()`.
