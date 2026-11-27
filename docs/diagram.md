# The integration diagram

The README's "How the tools work together" image is `docs/assets/tools.png`. Its source is `docs/assets/tools.html`.

## When to update it

Update it when an extension is added or removed, or when the way two tools connect changes.

## How to update it

1. Install the `diagram-viz` skill: `npx skills@latest add zazencodes/skills --skill diagram-viz`. Its `SKILL.md` lists the requirements and the layout rules.
2. Edit `docs/assets/tools.html`. Boxes and arrows are absolutely positioned, so moving one usually means moving its arrows and captions too.
3. Render it with the skill's script and fix every fault the layout check reports:

   ```sh
   <diagram-viz>/scripts/render.sh docs/assets/tools.html docs/assets/tools.png
   ```

4. Look at the PNG and confirm it still explains the setup at a glance.
5. Commit the HTML and PNG together.

## Colours

Box outlines show which parts belong together. Everything else stays grey.

- Purple (`a1`): the agent session, which every tool connects to.
- Orange (`a2`): Swipe List and its parts.
- Pink (`a3`): Agent Plane.

The style allows only these three accents. A tool without one keeps the neutral outline.
