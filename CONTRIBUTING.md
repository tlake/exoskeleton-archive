# Contributing

## Quickstart

### Local dev setup (speedrun, macos edition)

- `brew install hugo`
- Clone/fork the repo, `cd` to repo root
- `git submodule init`
- `git submodule update`

### Create an Exo post

```zsh
HUGO_PARAMS_zone="1" \
HUGO_PARAMS_gear="1" \
HUGO_PARAMS_gear_theme="I'm a Starbucks Tall" \
HUGO_PARAMS_question="1" \
HUGO_PARAMS_clue="Kirb your enthusiasm" \
HUGO_PARAMS_hints="Don’t overthink it, He’s in a better place.|Inhale, exorcise" \
HUGO_PARAMS_solution="Ghost Kirby" \
HUGO_PARAMS_author="Minion #00143" \
HUGO_PARAMS_date="2024-08-30" \
hugo new -k exopost content/events/2024-pax-west/111.md
```

Alternatively, copypasta some other exo post and edit it yourself.

### Preview changes

- `hugo serve --source src/`
- Point your web browser to `localhost:1313`

### Commit

- Make a pull request targeting the `main` branch!


## File structure

Each event is given its own date-prefixed directory under `src/content/events/`, and all the question files for an event are contained within that event's directory.
For example: `src/content/events/2024-pax-west/{file}.md`

### Kinds of Exo content files

All content file kinds have an archetype (found in `src/archetypes/`) that can be used to generate those content files from the terminal using the `hugo new` command.
Each instance of `.Site.Params.{field}` within an archetype signifies a value that can be passed on the command line using a `HUGO_PARAMS_{field}=""` environment variable.
Defaults exist for any such variable, and so they may safely be omitted from the command.

Sample `hugo new` command:

```zsh
HUGO_PARAMS_name="TITLE_HERE" hugo new -k exolist src/content/EVENT_NAME_HERE/_index.md
```

Most of the content for an exo file can be defined in the file's front matter: the keys and values at the start of the file, contained between the `---` lines.
Consult the relevant archetype or a already-existing file for reference.
The main body of these files can often be left blank, but content placed in the body will still be displayed so it's still useful for cases where the key/value configuration isn't flexible enough.

Archetype `exolist`:
  - Example file: `src/content/events/{event_name}/_index.md`
  - Event listing page for exo files.
  - Must be named `_index.md`.
  - Cascades `type` and `exoevent` params to the rest of the event's content files.

Archetype `exopost`:
  - Example file: `src/content/events/{event_name}/111.md`
  - Most common kind of content file, consisting of a zone number, a gear number (and theme), and a question number.
    - "Zone 1, Gear 2, Question 5" for example.
  - Weighting strategy:
    - `{zone}{gear}{question}0`.
    - For example, the `111.md` file should have `weight: 1110`.

Archetype `exosidequest`:
  - Example file: `src/content/events/{event_name}/sq01.md`
  - This archetype is technically just a subset of the `expost` archetype; it's a shortcut template with certain `exopost` fields removed.
  - Weighting strategy recommendation:
    -`{zone}{zone's highest gear + 1}{sidequest number}`
    -`{zone}{zone's highest gear + 3}{sidequest number}` if this sidequest needs to follow a mini boss

Archetype `exoboss`:
  - Example file: `src/content/events/{event_name}/mb101.md`
    - For mini bosses, the filename is `mb{mini boss number}{two-digit question number}.md`
  - Example file: `src/content/events/{event_name}/fb01.md`
    - For final bosses, the filename is `fb{two-digit question number}.md`
  - This archetype is technically just a subset of the `expost` archetype; it's a shortcut template with certain `exopost` fields removed.
  - Weighting strategy recommendation:
    -`{zone}{zone's highest gear + 2}{sidequest number}`

Other files:
  - Sometimes we have a use case for a file that doesn't fit the above templates; for example, the `gate.md` file.
    In such cases, we can just set a `title` and `weight` in the front matter and put whatever markdown content we need in the file's body.
  - Weighting strategy recommendation:
    - Whatever works to get it in the right place xD

### Images

Images should be kept in an event-spaced directory within the static folder.
I like to keep the image filename the same as the content filename.

For example, an image clue for Zone 1, Gear 3, Question 2 in the 2024 PAX West event should be found at `src/static/images/2024-pax-west/132.png`.

