# Prompt (English)

Create a 2D roguelike browser game as a single self-contained HTML file (pure JavaScript + Canvas, no external libraries or images). All pixel-art graphics are drawn in code. Dark fantasy, mouse-only controls.

**Run:** a tower of 20 floors with 2-3 rooms each; no free movement, the player picks rooms by clicking. Room types: combat, trap, chest, event, rest camp (floors 12, 14, 17, 19). After each floor: reward (skill upgrade / HP / gold), then a merchant. Mini-bosses on floors 10 (Necromancer) and 15 (Captain of the Cursed Guard); final boss on floor 20 (Lich King, with a short backstory: the Necromancer was his court mage). Death ends the run; no progression between runs.

**Zones:** Dungeons (1-3), Catacombs (4-6), Frozen Depths (7-9), Necromancer's Lair (10), then the Cursed Kingdom: castle halls, library, castle dungeons, barracks, royal chambers, throne room (11-20). Each zone has its own pixel-art background.

**Combat:** turn-based Slay the Spire-style cards with energy (3) and a hand of 5. Fights have 1-3 enemies, target chosen by click; area-attack cards hit everyone. Statuses: poison and frost (on the player), burn and bleed (on enemies, damage over time that ignores block). New cards only from the merchant and chests; after floor 10 the merchant sells stronger, pricier cards and artifacts.

**Classes:** Dark Knight (sword and shield, vampirism, bleed, weakening enemies) and Mage (staff and hat: burn, magic shields with healing, heal spell, expensive ice spells). Each class draws from its own card pool.

**Enemies:** rats, skeletons, giant bats, spiders, zombies, worms (floors 1-15); cursed knights, spectral servants, vampire bats, mimic chests, black priests (curses, heal allies), gargoyles, royal guards (floors 11-19). Enemy HP and damage scale with the floor and shrink in groups. Lich King: summons royal guards, drains life, adds curse cards to the player's deck, two phases (new attacks and more damage at 50% HP).

**Artifacts:** each has a plus and a minus, sold by the merchant (2 per visit) and found in chests; some are mage-only and some appear only after floor 10.

See `features.md` for the final numbers and `data/tower-of-shadows-data.xlsx` for tables.
