# Claude Computer · CC3

> This book is the documentation of Claude Computer, and it is also the reference Claude reads before it works on your desktop. Every code block marked **runnable** has a button that puts it on your desktop.

Claude Computer is a computer you and Claude share, one for each conversation. Its desktop is a canvas you both use: you work on it with your hands, Claude works on it with words, and you both see the same files. Claude answers here rather than in a long chat reply: it builds a small app or opens a file, and the two of you work in it. When Claude writes, you watch it happen: each file appears where it will land and fills in as Claude types.

Four things live on a desktop.

1. **Files** hold content: notes, docs, lists, tables, data, links and small web pages. Every file has an author and a history in the log.
2. **Apps** hold behaviour. An app is a short program in **Tanke**, a small JavaScript language for desktops, and renders in a frame. It shows and changes files by name, sorts notes into zones and responds to buttons.
3. **Programs** do work. A program is plain JavaScript that runs when someone presses **Run**: it loops, waits, computes, reads and writes files, and asks Claude. Its console is shared, so everyone sees the same output.
4. **The log** holds what happened: every capture, edit, run and chat line, with who did it.

Four ideas hold it together.

- **Two hands on one desktop.** Whatever you do with the mouse and whatever Claude does with words end up in the same store. Either side can pick up where the other left off.
- **Answers are things you use.** Claude replies with apps and files, not walls of text. An app can hand the turn back to Claude with a button, so a click can be your answer.
- **Watch it happen.** Claude's work is never a wall of text that arrives at the end. Drafts appear on the canvas as they are written and become real files when they close.
- **Files are content, apps and programs are behaviour.** Apps and programs never copy content into their code. They refer to files by name, so the same files can be seen and changed through many apps.
- **Most of the interface is hidden.** The desktop is the page. There is a menu corner, a view corner and a bar at the bottom; everything else appears when you ask for it.

# 1 · The desktop

The whole screen is the desktop. Scroll or drag open space to move around; pinch or Ctrl/⌘ + scroll to zoom; **Fit** shows everything.

| Gesture | Effect |
|---|---|
| Type in the bar at the bottom, then Enter | capture a note into the Inbox |
| Type in the bar, then ⌘/Ctrl + Enter or **Ask** | ask Claude (the canvas agent); watch it write |
| Double-click open space | write a note right there |
| Right-click open space | make a new file, app or program there |
| Drag a file by its title bar · drag the corner | move it · resize it |
| Double-click a title | rename the file |
| Drag a note into an app's zone | assign the zone's kind or tag |
| Drag a note's round handle onto another note | link them |
| Click a file, then use the bar above it | change kind, edit, tuck away, delete, **Send to Claude** |
| `/` or ⌘/Ctrl + K | jump to the bar |

The **menu corner** (top left) holds the desktops, new files, the drawer (Files, Log, Book), export and settings. The **view corner** (top right) shows where files are kept (red dot: shared with Claude; green: this browser only), the zoom, and **N new for Claude** when things changed that your Claude in the chat has not read yet. When others have the computer open, their faces sit in that corner too (chapter 14).

While Claude writes, a chip at the top says who is writing what. Click it to go there. Anything Claude made or changed has a red outline and **New from Claude** until you touch it. Every change Claude makes can be undone from the **Log**.

**Tucked away** files keep existing but leave the desktop. Find them in **Files** and open them again; apps can still use them.

# 2 · Files

Every file has a `type`, a `name` and `content`. Content depends on the type:

| Type | Content | On the desktop |
|---|---|---|
| `note` | text | a card with a kind (note, idea, question, decision, task, quote, source) |
| `doc` | text | a page you type into |
| `list` | `[{ text, done }]` | a checklist |
| `table` | `{ cols: [...], rows: [[...]] }` | an editable grid |
| `data` | any JSON | a JSON view you can edit |
| `link` | `{ url, title }` | a link card |
| `page` | HTML | a small web page in a sandbox; **Source** shows its HTML |
| `program` | JavaScript | code, a **Run** button and a console (chapter 6) |
| `app` | a Tanke program | a frame running it |

Everything you type saves on its own and lands in the log. Two people editing the same field at the same moment: the last save wins.

**Notes** are the small change of thinking. Capture them in the bar; a prefix chooses the kind and `#words` become tags:

| You type | You get |
|---|---|
| `Plain text` | a note (ending in `?` makes it a question) |
| `? How do we price it` | a question |
| `! A free tier` | an idea |
| `= We start with two plans` | a decision |
| `[] Draft the page` · `[x] Done already` | a task |
| `> A quote` · `@ A source https://…` | a quote, a source (any link becomes its url) |

A note you write by double-clicking stays where you wrote it. A note captured in the bar goes to the **Inbox**, or into an app that claims it (chapter 7).

**Pages** run in a sandbox: their scripts work, but they cannot reach the desktop, its files or Claude. Use a page for a small visual, a mock-up or a calculator to look at; use an app or a program when it should work on files.

# 3 · Built-in apps

Most of what you and Claude make together is one of a few kinds of thing: a document, a spreadsheet, a presentation, a canvas of boxes and arrows, a small website, or an app that asks you something and hands the answer back. These come built in. Claude writes their **content** in a few plain lines, the page turns that into a working app, and nobody sees code: you change any of them in place, like a desktop app.

Each built-in app keeps its content in a data file called *Name · data* and saves what you do in it (answers, picks, values, moves), so Claude sees the result on its next turn, written as what you did: *Capitals: answered question 2: Lisbon, right*, *Flow: connected “Build” to “Ship it”*. Most end in a **Send to Claude** button that hands the turn back with what you chose.

**Real tools.** Four kinds of file are full apps, like the ones on any computer:

- **Documents** are a word processor: a toolbar (text style, bold, italic, strikethrough, code, link, lists, checklist, quote, divider, table, undo), an outline when the window is wide, and a word count. Markdown shortcuts work while you type: `#`, `##`, `###` for headings, `-` for bullets, `1.` for numbers, `[]` for a checklist, `>` for a quote, `---` then Enter for a divider. It saves as markdown, which is what Claude reads.
- **Spreadsheets** have a formula bar, a cell you move with the arrows, Tab and Enter, typing that fills a cell, Enter or F2 or a double-click to edit, Shift for ranges, Delete to clear, ⌘C and ⌘V for blocks (from other spreadsheets too), insert and delete rows and columns, sort, Σ to sum what is above, number formats (money, percent, whole), and a status bar that adds up what you select. Empty rows wait below the data.
- **Presentations** have slides down the side (drag to reorder), the slide you are on in the middle, edited right on the slide, a layout (title, points, two columns, section, quote, big number), a theme (Paper, Ink, Clay), speaker notes, and **Present**, which fills the screen; arrows and clicks move on, Esc ends.
- **Canvases** are a whiteboard (below).

**The launcher and focus.** Press `/` (or the search button beside the orb) to open the launcher: make anything new from its tiles, open a recent file, find any file, run a command (fit, theme, settings, files, log, another desktop), or ask Claude. Enter opens what you pick in **focus**: the app fills the screen with its own title bar, like an app opened full screen. ⇧Enter shows it on the desktop instead. **F** focuses the selected window, **Esc** returns to the desktop. These keys work only when nobody is typing, and the computer leaves Claude's own shortcuts (⌘K and the like) alone.

**The cube** in the corner is Claude: it turns to look at your pointer and blinks. While Claude works on the desktop it flies to what Claude is writing and rides along; working from the chat, it turns over in place. Click it for the menu.

**Changing an app yourself.** Every window has a title bar like a desktop app: **Edit** turns a quiz, poll, form, chart, board, timeline, cards, slides or website into its own editor (add, reword, reorder, remove, mark the right answer, switch a chart to lines, write speaker notes), and **Done** turns it back. The canvas and records are always editable. The selection bar above a selected window has the same as icons (hover for their names): Edit, Focus, Rename, Duplicate, Export, Tuck away, Delete, and Send to Claude. The **⋯** menu (or a right-click on the window) has Focus, Edit, **Edit as text** (the same few lines Claude writes, to change in one go), Rename, Duplicate, New, Export (CSV, Markdown, HTML, SVG), Tuck away, Send to Claude and Delete. ⌘Z undoes your own last change, ⌘⇧Z redoes it.

**The canvas** works like a whiteboard: pick Box, Pill, Circle, Decision or Note in its toolbar (or press B, P, O, D, N) and click to place one, then type its name; double-click empty space for a box; drag the dot on a shape's edge to another shape to connect them, or into empty space for a new connected box; double-click a shape or an arrow to label it; pick a colour or a different shape for the selected one; Delete removes, arrows nudge, ⌘D duplicates, − + and ⤢ zoom and fit.

**When Claude rewrites an app, what you did stays**: answers to the questions that are still there, picks that still exist, filled-in values, where you put shapes on a canvas, record ids. A variant Claude leaves out stays as it was (a poll stays multi-pick).

| Block | Writes | You get |
|---|---|---|
| `@@quiz Name` | `? question`, then `- option` lines, `* the right one`, `> why` | questions you answer, a score, Send results to Claude |
| `@@poll Name · multi` | the question, then `- options` (`· multi` allows several) | a pick, Send to Claude |
| `@@form Name` | an intro line, then `- Label: text`, `long`, `number`, `date`, `email`, `yes` or `choice (a, b)`; `= value` sets a default | a form that saves as you type, Send to Claude |
| `@@chart Name · line` | a pipe table: the labels, then columns of numbers | a bar chart (`· line` for lines) with the latest value and the change |
| `@@board Name` | `## Column` headings, then `- cards` | columns you drag cards between, add to and clear |
| `@@timeline Name` | `- when: what` lines; `- [x] when: what` is done | steps you tick off |
| `@@cards Name · pick` | `## Title`, `Key: value` facts, body lines | cards side by side; `· pick` adds Choose, which tells Claude |
| `@@slides Name` | markdown slides separated by a line `---`; a first line `layout: title`, `section`, `two`, `quote` or `big` picks a layout, a line `||` starts the second column, a line `???` starts speaker notes | a presentation app: slides down the side, editing on the slide, layouts, themes, notes and Present |
| `@@canvas Name · tb` | `[Box]`, `(Round)`, `((Circle))`, `<Decision?>`, `note: text #yellow`, `A -> B: label`, `A --> B` (dashed) | boxes and arrows laid out for you, left to right (`· tb` top to bottom); drag to rearrange |
| `@@site Name` | markdown: `# headline`, an intro, a line of `[Button](https://…)` links, `## sections` | a small website: a hero, buttons, sections, lists as feature rows |
| `@@records Name` | a pipe table: field names, then one row per record | a small database: search, sort by any column, edit in place, add and delete; apps and programs read and write it by name |

```
@@poll Lunch
Where should we eat?
- Thai
- Pizza
- Salad bar
```

A block with the name of an existing built-in app rewrites its content; `@@append Name` adds questions, options, rows, cards, slides or shapes to it. Sticky colours are yellow, pink, blue, green, grey, purple and orange.

**Documents** (`@@doc`) are markdown and read as formatted text: headings, lists, `- [ ]` tasks, tables, quotes, links. Click a document to edit the markdown underneath.

**Spreadsheets** (`@@sheet` or `@@table`) are tables whose cells compute when they start with `=`. Columns are lettered and rows numbered under the header, so `A1` is the first column of the first row: `=SUM(B1:B4)`, `=B2*C2`, `=AVG(B1:B4)`, `=ROUND(B5 / 3, 2)`, `=IF(B1 > 100, "high", "ok")`. Also `MIN`, `MAX`, `COUNT` and `ABS`. Click a computed cell to see its formula.

**Records** are how the desktop stores structured data. A `@@records` app shows them; anything can use them by name. In an app: `c.records("Contacts", { Stage: "Lead" })` lists (filtered by equal fields), and inside an action `c.add("Contacts", { Name: "Ada" })`, `c.update("Contacts", id, { Stage: "Customer" })` and `c.remove("Contacts", id)` change them. Programs have the same four as `await records(…)`, `await add(…)`, `await update(…)` and `await remove(…)`. Adding to a name that does not exist yet starts a new store.

**In your own apps** each built-in app is also a part: `quiz(file)`, `poll(file)`, `form(file)`, `chart(file)`, `board(file)`, `timeline(file)`, `cards(file)`, `slides(file)`, `canvas(file)`, `site(file)`. Three small parts help an app talk: `choices(question, options)` shows buttons and a click hands the turn to Claude with the pick, `progress(label, value, max)` draws a bar, and `md(text)` shows formatted text. For structure: `tabs({ Overview: part, Data: part })` switches between named panes, `divider()` draws a rule, and `badge(text)` is a small label (with `.tone(…)`).

**Making apps that make things.** Inside an action, `c.make("a quiz about this chapter")` asks the Claude built into the page to build it on the desktop, and a program can do the same with `await make(…)` (it returns what was made) and bring anything into view with `await open(name)`. A program can also write an app directly: `await write("Tracker", code, "app")`.

**Shared components.** A library is an app whose program has no `app()` and ends with `return { … }`; its window lists what it shares. Any app uses it with `include`:

```
// the app "UI kit"
const Stat = (label, v) => value(label, v).tone("accent")
const Section = (title, ...parts) => zone(title, ...parts)
return { Stat, Section }
```

```
const { Stat, Section } = include("UI kit")
app("Sales").add(Section("This week", Stat("Orders", live(c => c.records("Orders").length))))
```

**Tokens everywhere.** Apps take the desktop's look automatically; tones are `ink`, `muted`, `accent`, `positive` and `danger`, and `sketch()` paints with the same names. Pages (`@@page`) get the tokens as CSS variables (`var(--ink)`, `var(--accent)`, `var(--accent-ink)` for orange text, `var(--surface)`, `var(--line)`, `var(--r)`, `var(--font)`, …; the brand's data colors are `var(--clay)`, `var(--sky)`, `var(--olive)` and `var(--kraft)`) and a few opt-in classes: `cc-btn` (with `ghost` or `accent`), `cc-card`, `cc-stat`, `cc-label`, `cc-tag`, `cc-grid`, `cc-input` and `cc-rule`, so a page Claude writes matches the desktop without its own design work.

```tanke
app("Next step")
  .add(
    md("**Three ways forward.** Pick one and Claude takes it from there."),
    choices("Which should we do first?", ["Write the brief", "Sketch the site", "Plan the budget"]),
    progress("Ready", 2, 5),
  )
```

# 4 · Apps are Tanke programs

An app starts with `app(name)` and `.add(...)` places parts in it. It renders in a frame on the desktop. With **Show code** on in Settings (for developers), **⋯ → Show the program** opens it to read and edit; it rebuilds as you type. Without it, people only see the app, and **Fix with Claude** appears if it breaks.

```tanke
app("Hello")
  .add(
    heading("What are we thinking about?"),
    row(
      question("What problem are we solving?"),
      idea("Write it down before it scrolls away"),
      note("Everything here is code you can edit"),
    ),
  )
```

**Cards** show one thought: `note`, `idea`, `question`, `decision`, `task(text, done?)`, `quote(text, cite?)`, `source(title, url?)`. **Leaves**: `heading(text)`, `value(label, v)` for a key number, `sketch(...)` for drawing.

**Layouts** hold other parts:

| Layout | Arranges |
|---|---|
| `zone(title, ...parts)` | a titled area; a drop target when it holds a stream |
| `stack(...)` · `row(...)` · `grid(cols, ...)` | top to bottom · left to right · in columns |
| `tree(root, ...children)` | a hierarchy, left to right; children can be trees |
| `orbit(center, ...parts)` | around a center; `.turn(angle)` rotates |
| `cluster(...)` | a force field, simulated every frame |

Strings in a layout become notes: `zone("Risks", "Churn", "Cost")`.

**Modifiers** chain: `.key("name")` names a part for links, `.tone("accent" | "muted" | "positive" | "danger" | "ink")`, `.tag("risk")`, `.w(px)`, `.h(px)`, `.gap(px)`, `.dim(true)`, `.at(x, y)` places a top-level part freely inside the frame.

A part sits in one place; placing it twice is an error (`T-REUSED`). Plain JavaScript functions are the component system: `const Risk = t => note(t).tone("danger")`.

Double-click a part of a running app to jump to the line that made it.

# 5 · Apps that work on files

Apps find files by name. `file(name, { type, seed })` declares one; the seed is what the app shows until the file exists. The file is created the first time someone changes it, and it appears in **Files**.

**Editors** show a file and let anyone change it: `textedit(docFile)`, `checklist(listFile)`, `sheet(tableFile)`, `inspect(anyFile)`. **Actions** change files when someone uses the app: `button(label, act(c => …))` and `input(placeholder, act((text, c) => …))`. Inside an action, `c.write(name, value)` replaces a file's content and `c.write(name, old => new)` updates it.

```tanke
const items = file("Groceries", { type: "list", seed: [{ text: "Oat milk", done: false }] })

app("Groceries")
  .add(
    heading(live(c => `${c.file("Groceries").filter(x => !x.done).length} to buy`)),
    checklist(items),
    row(
      button("Clear bought", act(c => c.write("Groceries", xs => xs.filter(x => !x.done)))),
      button("Uncheck all", act(c => c.write("Groceries", xs => xs.map(x => ({ ...x, done: false }))))),
    ),
  )
```

The checklist edits the same file the desktop shows if you open it from **Files**: there is only one Groceries.

`files(filter)` lists files as tiles you click to open, which makes folders a one-liner: `files({ type: "doc" })`, `files({ name: "draft" })`, `files({ tag: "client" })`. Filters: `type` (one or a list), `name` (contains), `tag`, `placed`.

```tanke
const log = file("Reading log", { type: "table", seed: { cols: ["Title", "Pages"], rows: [] } })

app("Reading")
  .add(
    heading("What we are reading"),
    input("Add a title and press Enter", act((text, c) =>
      c.write("Reading log", t => ({ ...t, rows: t.rows.concat([[text, 0]]) })))),
    sheet(log),
    value("Pages so far", live(c => c.file("Reading log").rows.reduce((a, r) => a + (Number(r[1]) || 0), 0))),
    files({ type: "doc" }),
  )
```

`c.write` only works inside `act()`. Writing from `live()` would change a file every frame, so it fails with a clear error instead.

**Apps hand the turn to Claude.** `c.claude(say, data)` inside an action sends what someone said and picked to their own Claude in the chat; their click becomes that Claude's next message, and Claude answers on the desktop. This is how an app asks a question and gets an answer without anyone typing in the chat.

```tanke
const options = file("Options", { type: "list", seed: [{ text: "Lisbon", done: false }, { text: "Porto", done: false }] })

app("Pick a city")
  .add(
    heading("Where should we go?"),
    checklist(options),
    button("Plan it", act(c => c.claude("Plan a weekend in the ones I ticked", { picked: c.file("Options").filter(x => x.done).map(x => x.text) }))),
  )
```

The platform shows the person what is about to be sent and asks before it goes. Outside Claude (a saved copy of this file) the button copies the message to paste instead.
**Apps run programs.** `terminal(name)` puts a program's **Run** button and console inside an app, and `c.run(name, input)` starts a program from an action. The program does the work; the app shows what came of it.

```tanke
const rolls = file("Rolls", { type: "list", seed: [] })

app("Dice")
  .add(
    heading(live(c => `${c.file("Rolls").length} rolls`)),
    row(
      button("Roll 10", act(c => c.run("Roll dice", { times: 10 }))),
      button("Clear", act(c => c.write("Rolls", []))),
    ),
    checklist(rolls),
    terminal("Roll dice"),
  )
```

It needs the program **Roll dice** from the next chapter.

# 6 · Programs that run

A program is a file of plain JavaScript that runs when someone presses **Run** (or ⌘/Ctrl + Enter in its code). It is a whole language: variables, loops, functions, recursion, objects, `async`/`await`. It runs for as long as it needs, keeps its own state while it runs, and works on the desktop through a few functions.

```program
// Hello · counts down, then looks at the desktop
print("Hello from a program.")
for (let i = 3; i > 0; i--) { print(i); await sleep(300) }
const all = await files()
print(`This desktop has ${all.length} files.`)
return all.length
```

The code is the body of an async function, so `await` works at the top and `return` gives the result, which the console shows after `→`.

| In a program | Does |
|---|---|
| `print(...values)` | writes a line to the console (`console.log` works too) |
| `await read(name or id)` | a copy of a file's content |
| `await write(name, value)` | replaces a file's content; makes the file if it is new (a string makes a doc, `[{ text, done }]` a list, `{ cols, rows }` a table, anything else data) |
| `await append(name, value)` | adds an item to a list, a row to a table, a line to a doc |
| `await files(filter?)` | `[{ id, name, type, placed, by, kind, tags }]`; filter by fields, e.g. `{ type: "doc" }` |
| `await note(text, kind?)` | captures a note; prefixes and `#tags` work |
| `await sleep(ms)` | waits |
| `await ask(prompt)` | asks Claude and returns its answer as text |
| `await run(name, input)` | runs another program and returns its result |
| `await records(name, query?)` · `add(name, record)` · `update(name, id, patch)` · `remove(name, id)` | the records store (chapter 3) |
| `await open(name)` | brings a file into view |
| `await make(request)` | asks the Claude built into the page to build something on the desktop; returns `{ ok, made }` |
| `clear()` | empties the console |
| `input` | what the program was started with (`null` from the Run button) |

**Run and Stop.** While a program runs, its button says **Stop**, and Stop always works: the program runs in its own thread, so even an endless loop cannot freeze the desktop. (Where the browser allows no threads it runs on the page instead, and a loop that runs 8 seconds without an `await` stops with a message saying where to add `await sleep(0)`.)

**One console for everyone.** The output, the status and who ran it are saved on the program file. Everyone looking at the desktop sees the same console, and so does Claude in the chat. Every write a program makes lands in the store like any other edit, so apps that show those files update while it runs.

**Mistakes** show before you run: the line with a syntax error is marked in the code and named under it. Errors while running print in red with their line.

```program
// Roll dice · adds rolls to the list "Rolls"; input: { times }
const times = (input && input.times) || 5
for (let i = 0; i < times; i++) {
  const n = 1 + Math.floor(Math.random() * 6)
  await append("Rolls", { text: `Rolled a ${n}`, done: n === 6 })
  print(n)
  await sleep(120)
}
return `${times} rolls`
```

```program
// Primes · a sieve; writes every prime up to 500 to the table "Primes"
const N = (input && input.upTo) || 500
const sieve = new Array(N + 1).fill(true); sieve[0] = sieve[1] = false
for (let i = 2; i * i <= N; i++) if (sieve[i]) for (let j = i * i; j <= N; j += i) sieve[j] = false
const primes = sieve.flatMap((p, i) => p ? [i] : [])
await write("Primes", { cols: ["#", "Prime", "Gap"], rows: primes.map((p, i) => [i + 1, p, i ? p - primes[i - 1] : 0]) })
print(`${primes.length} primes up to ${N}.`)
return primes.slice(-5)
```

Programs and apps make each other better: a program does work in time, an app shows its files as they change. **Life** below writes a board every tick; the **Life** app draws it and has the program's Run button in it.

```program
// Life · Conway's Game of Life; writes the board to "Life board" every tick
const W = 40, H = 24, gens = (input && input.generations) || 300
let cells = Array.from({ length: W * H }, () => Math.random() < 0.28 ? 1 : 0)
const at = (x, y) => cells[((y + H) % H) * W + ((x + W) % W)]
for (let gen = 1; gen <= gens; gen++) {
  cells = cells.map((alive, i) => {
    const x = i % W, y = Math.floor(i / W)
    let n = 0
    for (let dy = -1; dy <= 1; dy++) for (let dx = -1; dx <= 1; dx++) if (dx || dy) n += at(x + dx, y + dy)
    return n === 3 || (alive && n === 2) ? 1 : 0
  })
  await write("Life board", { w: W, h: H, gen, alive: cells.reduce((a, b) => a + b, 0), cells })
  await sleep(160)
}
return "Settled after " + gens + " generations"
```

```tanke
const board = file("Life board", { type: "data", seed: { w: 1, h: 1, gen: 0, alive: 0, cells: [0] } })

app("Life")
  .add(
    row(
      value("Generation", live(c => c.file("Life board").gen)),
      value("Alive", live(c => c.file("Life board").alive)).tone("accent"),
    ),
    sketch(live((g, c) => {
      const b = c.file("Life board"), s = Math.min(g.w / b.w, g.h / b.h)
      b.cells.forEach((v, i) => v && g.rect((i % b.w) * s, Math.floor(i / b.w) * s, s - 1, s - 1, "ink"))
    })).w(480).h(288),
    terminal("Life"),
  )
```

**Claude and programs.** The canvas agent can write a program and run it in the same answer (`@@program`, then `@@run`, chapter 12). Claude in the chat cannot press Run in your browser, so it asks: the program shows **Claude asks to run this program** with a **Run it** button.

# 7 · Streams: apps as lenses over notes

`stream(filter)` shows the notes that belong in a place. It is a runtime part: the program does not list notes, it says which ones belong.

```tanke
app("Board")
  .add(
    grid(3,
      zone("Inbox", stream({ unsorted: true })),
      zone("Questions", stream({ kind: "question" })),
      zone("Ideas", stream({ kind: "idea" })),
      zone("Decisions", stream({ kind: "decision" })),
      zone("Tasks", stream({ kind: "task" })),
      zone("Pricing", stream({ tag: "pricing" })),
    ).gap(24),
  )
```

**How notes find their place.** Each note shows up exactly once on a desktop:

1. A note placed by hand stays where you put it.
2. Otherwise the first stream that matches it claims it, apps in the order they were made, streams in program order.
3. `stream({ unsorted: true })` takes everything no other stream claimed.
4. Anything left sits in the desktop's **Inbox**, so nothing captured is hidden.

Filters combine: `{ kind, tag, by, who, text, done, last }`. `by` is `"you"` (a person), `"claude"`, `"agent"` or `"any"`; `who` is `"me"`, `"others"` or a person's id (chapter 14); `last: 5` keeps the five newest. Arrange a stream with `.layout("stack" | "row" | "grid" | "cluster")` or `.cols(n)`; style each note at runtime with `.style(live((t, c) => ({ tone, dim })))`.

**Dragging assigns.** A stream whose filter names one kind or one tag is a drop target. Drop a note in *Questions* and it becomes a question; drop it in *Pricing* and it gains the tag; leave *Pricing* and the tag goes. Drop it on open space and it stays there, placed by hand.

# 8 · Build-time, runtime and event lambdas

Lambdas run at three moments, and Tanke makes each one explicit.

| Where the lambda goes | When it runs | What it gets |
|---|---|---|
| `repeat(n or array, (x, i) => part)` | **build time**, once per element | real values |
| `app().use(a => a.add(…))`, plain functions | **build time** | what you pass |
| `live(c => value)` in a text, tone, dim, value or `.at` slot | **runtime**, every frame | the context `c` |
| `stream().style(live((t, c) => …))` | **runtime**, per note | the note and `c` |
| `orbit().turn(live(c => angle))`, `sketch(live((g, c) => …))` | **runtime**, every frame | `c` (and a painter `g`) |
| `button(label, act(c => …))`, `input(text, act((text, c) => …))` | **event**, when someone uses it | `c` with `write` and `create` |

Build-time lambdas **make structure**: their parts land in the IR. Runtime lambdas **compute values** and must not change anything. Event lambdas **change files**.

```tanke
const days = ["Mon", "Tue", "Wed", "Thu", "Fri"]

app("Week")
  .add(
    heading(live(c => `${c.count({ kind: "task", done: false })} tasks open this week`)),
    row(repeat(days, d => zone(d, stream({ tag: d.toLowerCase() })).w(200))),
  )
```

**A bare function where a value or action goes is an error** (`T-BARE-FN`): `note(c => c.t)` fails with the fix `note(live(c => c.t))`, and `button("Go", c => …)` with `button("Go", act(c => …))`. `repeat()` over a stream fails (`T-REPEAT-RUNTIME`): notes do not exist yet while building.

The context `c` has `t` (seconds), `dt`, `frame`, `now`, `zoom`, `notes` (all notes as `{ id, text, kind, tags, by, at, done, links }`), `count(filter?)`, `file(name)` (a copy of the content, or the seed), `files` (every file's id, name, type and placement), `selected`, `params` and every parameter by name. In actions it also has `write(name, value | fn)` and `create(name, type, content)`.

```tanke
app("Pulse")
  .add(
    row(
      value("Notes", live(c => c.count())),
      value("Open questions", live(c => c.count({ kind: "question" })))
        .tone(live(c => c.count({ kind: "question" }) > 3 ? "accent" : "ink")),
      value("Files", live(c => c.files.length)),
    ),
    orbit(question("What matters most?"), "Speed", "Trust", "Cost", "Focus").turn(live(c => c.t * 0.15)),
  )
```

`sketch(live((g, c) => …))` draws every frame. The painter `g` has `w`, `h`, `rect`, `circle`, `ring`, `line`, `text`, `color(name)` and the raw `ctx`; colors are theme tokens (`"ink"`, `"accent"`, `"muted"`, `"line"`) or any CSS color.

A runtime lambda that throws marks only its own part with a dashed outline and lists the line in the app's code view (`T-RUNTIME`); the rest of the app keeps running.

# 9 · Parameters

`params({ … })` declares knobs. They appear along the bottom of the app's frame, and their values are plain JavaScript while the program builds. Each person's knob settings stay in their own browser.

| Knob | Value |
|---|---|
| `slider(value, min, max, step?)` | number |
| `checkbox(value)` | true / false |
| `choice(value, options)` | text |
| `field(text)` | text |

```tanke
const p = params({
  cols: slider(2, 1, 4),
  focus: choice("all", ["all", "idea", "question", "task"]),
})

app("Focus")
  .add(
    heading(p.focus === "all" ? "Every note" : `Only ${p.focus}s`),
    zone("Focus", stream(p.focus === "all" ? { unsorted: true } : { kind: p.focus }).cols(p.cols)),
  )
```

# 10 · Links

`link(a, b, label?)` draws an arrow between parts of an app. Ends are parts you hold in a `const`, or `"#key"` strings for parts named with `.key()`.

```tanke
const why = question("Why do good ideas get lost?").key("why")

app("Lost ideas")
  .add(
    row(
      tree(why,
        tree("Chat scrolls away", "Nothing pins it"),
        tree("Notes live elsewhere", "No context"),
        "Nobody looks back"),
      decision("Keep one desktop per conversation").key("fix"),
    ).gap(64),
    link(why, "#fix", "answered by"),
  )
```

Notes link by hand: drag the round handle on a note onto another note. Note links are stored with the note, so they show wherever the notes are, on the desktop or inside apps.

# 11 · The IR

Each app's program compiles to an IR, a JSON DAG, before anything renders. `tanke.apps.getIR(id)` returns it.

- `nodes` are the parts, each with `id`, `type`, `cls` (`card`, `heading`, `value`, `sketch`, `layout`, `stream`, `editor`, `files`, `button`, `input`, `link`), `line`, `props`, `kids` and `parent`.
- `edges` are `contains` (layout → part), `link` (arrows), `reads` (from `notes`, `files` or `file:Name` into a part) and `writes` (from an editor to its file).
- `sources` are what the app reads at runtime: the notes, the file list, and each declared file.
- `lambdas` lists every runtime lambda (`when: "runtime"`), every action (`when: "event"`) and every build-time `repeat`, with lines.
- `hash` fingerprints the structure.

The IR never contains file contents. Those live in the store and are read at runtime.

# 12 · Working live

Claude writes onto the desktop in one plain-text format, whether it is the canvas agent behind the bar or Claude in the chat. The page reads the text while it is still being written: every block shows up as a draft where it will land, fills in token by token, and becomes a real file the moment it closes.

A line that starts with `@@` opens a block. The block ends at a line `@@end`, at the next `@@` line, or at the end of the text. Lines outside blocks are what Claude says; they show in the chat.

````
I'll set up the trip: a packing list, a budget and one open question.
@@list Packing @ 80,40
- [ ] Passport
- [x] Charger
@@table Budget @ 420,40
| Item | CHF |
| --- | --- |
| Train | 120 |
| Hotel | 340 |
@@note question Do we need a car? #trip
@@end
````

| Header | Body |
|---|---|
| `@@note <kind> <text>` | the note's text, inline or on the lines below; kind is one of note, idea, question, decision, task, quote, source |
| `@@doc <Name>` | text; markdown is fine |
| `@@list <Name>` | one item per line: `- [ ] item`, `- [x] done` (plain lines work) |
| `@@table <Name>` | a pipe table or CSV lines, header first |
| `@@data <Name>` | JSON |
| `@@link <Name>` | the address, then a title line |
| `@@page <Name>` | one small, complete HTML page; inline CSS and JS only |
| `@@program <Name>` | JavaScript that runs (chapter 6) |
| `@@app <Name>` | one complete Tanke program |
| `@@file <Name> · <type>` | the same as `@@<type> <Name>` |
| `@@append <Name>` | text for a doc, items for a list, rows for a table |
| `@@delete <Name>` | nothing |
| `@@run <Name>` | optional input for the program, as JSON |
| `@@open <Name>` | nothing; puts the file on the desktop if it was tucked away and brings it into view (`@@focus` is the same) |
| `@@tuck <Name>` | nothing; takes the file off the desktop, it stays in **Files** |
| `@@move <Name> @ x,y` | nothing; moves the file |

Any header can end with `#tags` and `@ x,y` to put the file at that spot (`@ x,y 900x600` also sizes its window); without a spot it lands in free space near your view (notes without a spot go to the Inbox or into an app that claims them). A block with the name of an existing file of the same type rewrites that file in place: you see the draft over the file while it is rewritten. Code fences inside a block are ignored, so code wrapped in a fence does no harm.

**Following along.** When a new block starts somewhere off screen, the view glides there (turn this off in Settings). The chip at the top names who is writing what; click it to jump there.

**Programs, too.** `@@run Name` runs a program after the blocks before it have landed, so the canvas agent can write a program, run it and let you watch its console in one answer. From Claude in the chat it asks first: the program shows **Claude asks to run this program** with a **Run it** button.

**Pointing.** `@@open Name` is how Claude says "look at this": the view glides there and the file glows for a moment, with Claude's marker beside it.

# 13 · Claude in the chat: two calls a turn

Many authors can share a desktop, and the log tells them apart: **you**, the other **people** here (by name), **Claude · canvas** (the agent behind the bar, built into the page) and each person's **Claude** in their own conversation ("Ana's Claude").

**One computer per conversation.** Give Claude this file in a conversation and it publishes it from there as a new artifact. A new artifact has its own database, so each conversation gets its own computer. One artifact can still hold several desktops (menu corner); a link that ends in `#d-<desktop id>` opens one directly. Share it from the artifact's Share menu and the people you share it with work on it with you (chapter 14).

**The canvas agent** reads this book, every file on the desktop (written in the block format, newest first, within a budget), who made what, who else is here, what you have selected, where you are looking and the recent log with each request. Its answer streams onto the canvas. A failing app goes back to it once with its errors.

**Models.** The canvas agent prefers Claude built into the page, which needs no setup inside Claude. If that is unavailable it falls back to the Anthropic API, then to any OpenAI-compatible endpoint (Settings). Keys stay in memory for the visit. The bar shows which model answers.

**Claude in the chat** works in turns, and each turn is two calls: it reads one document and writes one document. The page does everything else. Every person's Claude has a **channel of its own**, private to that person (their `data/users/<id>/` space, which only they can read or write):

1. **The view.** Your page keeps `data/users/{you}/claude-{desk}` current for your Claude: what everyone changed since its last turn (by name, Claudes included), those files in full, a one-line index of every file with who made and last changed it, where you are looking, who else is here and what they look at, select and type in, what your Claude's last turn did (with apps that failed to build, by line), consoles of running programs, and the id for its next turn. Claude reads it with one call: `ArtifactData get`, collection `data/users/me`, doc_id `claude-{desk}` (`me` is whoever's Claude asks).
2. **The turn.** Your Claude writes `data/users/me/claude-{desk}/turns/{next}` with `{ text }` in the block format (and, if you run several, `agent: "Research"` to label it). Your page plays it in as your Claude working on the desktop (drafts where things land, its marker where it is, its sentences in a bubble at the top). Everyone else sees it land live, as "Your-name's Claude". Each block becomes a file, each change is logged so anyone can undo it, the outcome is recorded on the turn and the view is refreshed.
3. **The cursor.** When a turn lands, the page marks how far your Claude has read. Until then the view corner shows **N new for Claude**, and the Log marks where it stopped reading.
4. **Hand-offs.** **Send to Claude** (the bar above a selected file) and **N new for Claude** put an attachment in your message box, for *your* Claude. An app's `c.claude()` button sends its message to the Claude of whoever pressed it, right away, after the platform asks. Each one says where that Claude reads and where it answers, so it can answer without looking anything up. Where none of this is available, the same buttons copy the text to paste.
5. **Presence.** The page tells your conversation which desktop and file you are looking at, so "this one" means something.

Your page has to be open for your Claude's turn to land; a turn that arrives while it is closed waits and lands when you open the computer again. Nobody else can write to your channel, so nobody can speak as your Claude.

**The shared channel.** Before people had channels, one Claude per computer read `claude/{desk}` and wrote `claude/{desk}/turns/{next}`. That still works for editors: an editor's page keeps that view current and plays those turns, attributed to "Claude". Only editors can write there.

| Path | Holds |
|---|---|
| `desks/{deskId}` | `{ title, at, by, who, inbox: [x, y] }` |
| `desks/{deskId}/files/{fileId}` | `{ name, type, content, kind, tags, done, links, url, placed, x, y, w, h, by, who, eby, ewho, rev, prev, at, updated, fresh }`; programs also `output: [{ at, kind, text }]`, `status`, `ranBy`, `ranWho`, `ranAt`, `took`, `runRequest: { at, by, who, input }` |
| `desks/{deskId}/events/{id}` | `{ at, by, who, op, text, ref, kind, before? }`; edits to one file by one person within a minute share one entry, and old entries are pruned |
| `data/users/{id}/claude-{deskId}` | that person's Claude's view: `{ asOf, next, how, channel, desk, you, person, people, changes, changed, files, errors, running, last, pending }` |
| `data/users/{id}/claude-{deskId}/turns/{turnId}` | `{ text, agent? }` from their Claude; their page adds `applied: { at, ok, results, errors }` |
| `data/users/{id}/claude-{deskId}-read` | `{ at }`: how far their Claude has read |
| `people/{id}` | `{ at }`: this person has been on this computer |
| `people/{id}/desks/{deskId}` | `{ at, marks: { scope: { j, at } } }`: what this person did in built-in apps and in apps' `c.setMy` (chapter 14); everyone reads it, only they write it |
| `claude/{deskId}`, `claude/{deskId}/turns/{turnId}`, `desks/{deskId}/cursors/claude` | the shared channel: view, turns and cursor for an editor's Claude |

`by` is the kind of author (`you` for a person, `claude`, `agent`) and `who` the person's id (for a Claude, whose Claude it is); `eby`/`ewho` say who changed the file last. Ids are opaque and never shown; the page turns them into names for each viewer, and nothing stores a name. `rev`/`prev` version each content write (chapter 14). Times are milliseconds. `fresh: true` marks a file a Claude touched that nobody has touched since. The page cleans every record as it arrives, so a malformed one can never break the desktop. When the desktop runs outside Claude (a saved copy of this file), the same records live in this browser and the hand-offs are off.

# 14 · Together

Share the computer from the artifact's **Share** menu and everyone you share it with works on it with you, live. Each person who opens it is a person here, with their name and face; each of them can have their own Claude.

**Who can do what** follows the Share menu. *Viewers* and *Commenters* watch: they see everything move but change nothing. *Contributors* do everything on the desktop (notes, files, apps, programs, votes) and have their own Claude. *Editors* also keep the shared channel for older Claudes and publish new versions of the computer. Guests from outside your organization are marked as guests.

**Seeing each other.** The faces in the view corner are the people who have this computer open; a dimmed face is on another desktop. Click one to **go to** where they are or to **follow** them: your view moves with theirs until you pan or press Stop. On the desktop you see their pointers with their names, a colored outline on what each person has selected, "Ana is typing" on what they are writing in, windows moving under their hand while they drag, and their Claude's marker with whose Claude it is. None of this is stored; it is gone when they close the page.

**Writing at the same time.** Two people can type in the same document, tick the same checklist, fill the same sheet or move cards on the same board at once. Each change says which version it was made from, and the page merges: by line in text (and by word inside a line), by item in lists and tables, by key in data, by id in records and on canvases. Where two changes touch the same spot, the later one wins; where both add, both stay. A document you are typing in takes in other people's changes when you pause, around your caret. When the page does merge, it says so once: *Both changes are kept.*

**Each person's answers.** The built-in apps that ask something keep what each person does apart:

| App | Each person keeps | Everyone sees |
|---|---|---|
| Poll | their own pick(s) | a tally with faces on each option |
| Quiz | their own answers and score | everyone's score beside theirs, and who picked what once they have answered |
| Form | their own filled-in copy | a Responses table, one row a person (Export makes it a CSV) |
| Cards · pick | their own choice | faces and counts on each card |

Claude reads all of it by name: *"3 voted: Thai 2 (Ana, Bo), Pizza 1 (Cy)"*. The questions, options and fields themselves stay shared, so anyone can edit them.

**In your own apps.** The context `c` knows who is using the app and who is here:

| | |
|---|---|
| `c.me` | the person using the app: `{ id, name, color, avatar, isMe }` |
| `c.people` | everyone on this desktop now, you first: `{ id, name, color, guest, isMe, view, selected, editing }` |
| `c.person(id)` | one person by id: `{ id, name, color, avatar, guest, isMe }` |
| `c.my(key)` | your value for `key` in this app |
| `c.setMy(key, value)` | in actions: set your value; everyone sees it, only you can change it |
| `c.everyone(key)` | everyone's values for `key`: `[{ id, name, color, value, at, isMe }]` |
| `facepile({ names })` | a part: the faces of who is here now |
| `avatar(id)` | a part: one person's face and name (`avatar(live(c => c.me.id))`) |
| `stream({ who: "me" })` | notes you wrote (`"others"`, or a person's id) |

Programs get `me` and `people` the same way, as they were when someone pressed Run.

```tanke
// Standup · everyone writes their own line; everyone sees all of them
app("Standup").add(
  toolbar(heading("Standup"), spacer(), facepile()),
  input("What are you on today?", act((text, c) => c.setMy("today", text))),
  stack(live(c => c.everyone("today").map(x => `${x.isMe ? "You" : x.name}: ${x.value}`).join("\n") || "Nobody yet")),
  statusbar(live(c => `${c.everyone("today").length} of ${c.people.length} here have written`)),
)
```

**Code you trust.** Apps and programs are code, and code runs with whatever the person running it can see and do. So each page runs only the code its person trusts: the built-in apps, what they or their own Claude wrote, and code they let in. Anyone else's app shows a small panel instead, *Run this app?*, with who changed it last and the code a click away; **Run it** remembers that exact code for that person, on every device. When the code changes, the question comes back. Programs ask the same before **Run**. Built-in apps (polls, boards, forms and the rest) are content, not code, so they work for everyone straight away: prefer them when you build for a group.

**Every Claude.** Each person's Claude works in its own conversation and its own channel (chapter 13), so several Claudes can work on one desktop at once without stepping on each other. Each reads what everyone did since it last looked, names included; each one's work shows as theirs ("Ana's Claude"); and anyone can undo any Claude's change from the Log.

# 15 · The window API

Everything a person can do, a script or agent can do through `window.computer` (also `window.tanke`).

| Call | Does |
|---|---|
| `computer.files.list(filter?)` / `.get(idOrName)` | read files; filter by fields, e.g. `{ type: "doc" }` |
| `computer.files.create({ type, name, content, … })` / `.update(id, patch)` / `.remove(id)` / `.open(id)` | change files |
| `computer.capture(text, { kind, tags, x, y, by })` | capture a note; prefixes and `#tags` work |
| `computer.stream(text, { by })` | apply text in the block format, as Claude would: `{ prose, results }` |
| `computer.parse(text)` | parse the block format without applying it |
| `computer.programs.run(name, input)` / `.stop(name)` / `.check(code)` / `.running()` | programs; `run` resolves `{ ok, value, error, line }` |
| `computer.apps.list()` / `.create(code, name?)` / `.getIR(id)` / `.setParam(id, name, value)` | apps |
| `computer.check(code)` | compile a Tanke app without touching the desktop: `{ ok, errors, warnings, ir }` |
| `computer.desks.list()` / `.current()` / `.create(title)` / `.switch(id)` / `.rename(title)` | desktops |
| `computer.events(n?)` / `.unread()` / `.cursor()` / `.undo(eventId)` | the log, what Claude in the chat has not read, undo |
| `computer.live()` | what each Claude is doing right now |
| `computer.view(kind?)` | the view a Claude reads, as the page would write it now: `"mine"` (your Claude's) or `"shared"` |
| `computer.channel()` | where your Claude reads and writes |
| `computer.me()` / `computer.people()` | who you are; who is on this desktop now |
| `computer.goTo(peer)` / `computer.follow(peer \| null)` | go to where someone is; follow them, or stop |
| `computer.marks(scopeOrDataFileId)` | what each person did in a built-in app: `[{ id, v, at, isMe }]` |
| `computer.turn(text)` | play text in the block format as a turn from Claude in the chat (for testing) |
| `computer.ask(text)` | ask the canvas agent |
| `computer.model()` | the active model and the fallback chain |
| `computer.export()` | save the desktop as JSON |
| `computer.fit()` / `.select(id)` / `.openDrawer("files" \| "log" \| "book")` | the view |
| `computer.examples()` / `computer.docs()` | the examples; this book as markdown |
| `computer.on(event, fn)` | `"files"`, `"param"`, `"message"`, `"people"`; returns an unsubscribe function |

**Extending it.** Everything lives in one HTML file. A new Tanke part is a function in the `DSL` object (section TANKE CORE) and a case in `AppView.make()` (section TANKE DESKTOP). A new file type is an entry in `FILE_TYPES` and `SEEDS`, a case in `editorFor()` and, for the block format, in `decodeBody()`. A new program function is an entry in the runner's `api` and in `PROGRAM_API`. Add it to the reference below and Claude learns it on its next request.

# 16 · Reference

**App shape (Tanke)**

```js
const p = params({ knob: slider(2, 1, 4) })                 // optional, once
const doc = file("Brief", { type: "doc", seed: "" })        // files the app uses
const Card = t => note(t).tone("muted")                     // plain functions are components
app("Name")
  .add(...parts)
  .link(a, b, "label")
  .use(a => a.add(…))
```

**Cards**: `note` · `idea` · `question` · `decision` · `task(text, done?)` · `quote(text, cite?)` · `source(title, url?)`

**Leaves**: `heading(text)` · `value(label, v, { suffix, digits })` · `sketch(live((g, c) => …))`

**Layouts**: `zone(title, ...)` · `stack(...)` · `row(...)` · `grid(cols, ...)` · `tree(root, ...)` · `orbit(center, ...)` · `cluster(...)`

**Notes**: `stream({ kind, tag, by, who, text, done, last } | { unsorted: true })` · `.layout(…)` · `.cols(n)` · `.style(live((t, c) => ({ tone, dim })))`

**Files**: `file(name, { type, seed })` · `textedit(doc)` · `checklist(list)` · `sheet(table)` · `inspect(any)` · `terminal(program)` · `files({ type, name, tag, placed })`

**Actions**: `button(label, act(c => …))` · `input(placeholder, act((text, c) => …))` · in actions: `c.write(name, value | old => new)` · `c.create(name, type, content)` · `c.run(program, input)` · `c.claude(say, data)` hands the turn to Claude

**Links**: `link(a, b, label?)`; ends are parts or `"#key"`

**Modifiers**: `.at(x, y | live)` · `.key(name)` · `.tone(… | live)` · `.tag(...words)` · `.w(px)` · `.h(px)` · `.gap(px)` · `.dim(bool | live)` · `.turn(angle | live)` · `.cols(n)`

**Lambdas**: build time `repeat`, `.use`, plain functions · runtime `live(c => …)` · event `act(c => …)`

**Knobs**: `slider` · `checkbox` · `choice` · `field`

**Context `c`**: `t` `dt` `frame` `now` `zoom` `notes` `count(filter?)` `file(name)` `files` `selected` `params` `records(name, query?)` `me` `people` `person(id)` `my(key)` `everyone(key)` + every knob · in actions also `write` `create` `run` `add` `update` `remove` `make` `claude` `setMy`

**People**: `facepile({ names })` · `avatar(id | live)` (chapter 14)

**Structure**: `tabs({ Title: part })` · `divider()` · `badge(text)` · `include(library)` (a library app returns `{ … }` instead of calling `app()`)

**The app kit**: the parts that make an app look and behave like one, so Claude writes only what the app is about.

| Part | What it is |
|---|---|
| `toolbar(…)` | a row of controls along the top: buttons, inputs, badges, `heading`, `icon`, `spacer()`; strings are plain text |
| `statusbar(…)` | a quiet line along the bottom for counts and state |
| `split(side, main)` | a sidebar and a main area, like mail or notes; `side.w(260)` sets the sidebar's width |
| `panel(title, …)` | a card with a title around a group of parts |
| `list(items, opts)` | a list to pick from. `items` is `live(c => [...])`, a records store's name, or an array. Options: `title`, `subtitle`, `meta`, `icon` (a field's name, or `live((item, c) => …)`), `pick: act((item, c) => …)`, `selected: live(c => id)` |
| `empty(text)` | an empty state |
| `icon(name)` | one of the computer's icons: person, mail, calendar, clock, star, heart, flag, folder, gear, home, image, chat, bolt, tag, pin, lock, money, search, plus, check, doc, sheet, slides, canvas, … |
| `spacer()` | pushes what follows to the far end of a toolbar or row |
| `document(file)` · `spreadsheet(file)` | the word processor and the spreadsheet as parts (the same as `textedit` and `sheet`) |

**Where data lives**, without a backend to write: `c.records(store)`, `c.add`, `c.update`, `c.remove` for shared records; `c.file(name)` and `c.write` for files; `c.state` and `c.set(key, value)` for what this viewer has open (a selected item, a tab, a draft), which resets on reload; `c.mine` and `c.keep(key, value)` for what this device remembers between visits; `c.my(key)`, `c.setMy(key, value)` and `c.everyone(key)` for one value per person that everyone sees; `c.claude(say, data)` to hand the turn to Claude and `c.make(request)` to have the page's Claude build something.

```tanke
// Contacts · a list and a detail, built from the kit
const notes = file("Contact notes", { type: "doc" })
app("Contacts").add(
  toolbar(icon("person"), heading("Contacts"), spacer(), button("Add", act(c => c.set("open", c.add("People", { Name: "New person" }))))),
  split(
    list("People", { title: "Name", subtitle: "Company", pick: act((r, c) => c.set("open", r.id)), selected: live(c => c.state.open) }).w(260),
    stack(heading(live(c => (c.records("People").find(r => r.id === c.state.open) || {}).Name || "Pick someone")), panel("Notes", document(notes))),
  ),
  statusbar(live(c => c.records("People").length + " people")),
)
```

**Programs**: `print` · `await read(name)` · `await write(name, value, type?)` · `await append(name, value)` · `await files(filter?)` · `await note(text, kind?)` · `await sleep(ms)` · `await ask(prompt)` · `await run(name, input)` · `await records/add/update/remove(…)` · `await open(name)` · `await make(request)` · `clear()` · `input` · `me` · `people` · `return value`

**Block format**: `@@note` `@@doc` `@@list` `@@table` `@@sheet` `@@data` `@@link` `@@page` `@@program` `@@app` `@@file Name · type` `@@append` `@@delete` `@@run` `@@open` `@@tuck` `@@move` `@@end` · headers take `#tags` and `@ x,y`

**Built-in apps**: `@@quiz` `@@poll` `@@form` `@@chart` `@@board` `@@timeline` `@@cards` `@@slides` `@@canvas` `@@site` `@@records` (chapter 3) · as parts: `quiz(file)` … `site(file)` · `choices(question, options)` · `progress(label, value, max)` · `md(text)`

**File types**: `note` `doc` `list` `table` `data` `link` `page` `program` `app` · **Note kinds**: `note` `idea` `question` `decision` `task` `quote` `source` · **Authors**: `you` `claude` `agent` (and `who`, the person's id)

**Error codes** (Tanke apps)

| Code | Meaning |
|---|---|
| T-SYNTAX, T-JS | JavaScript itself failed (syntax, unknown name) |
| T-BARE-FN | a function where a value or action goes; wrap it in `live()` or `act()` |
| T-ACT, T-LIVE | `act()` or `live()` without a function |
| T-REPEAT-RUNTIME | `repeat()` over runtime data; use `stream()` |
| T-REUSED | a part placed twice; make a function and call it twice |
| T-NODE-IN-TEXT | a part where text goes |
| T-FILE | a file reference or file type is wrong |
| T-MISSING, T-ARITY, T-TYPE, T-OPTION | wrong arguments |
| T-FILTER | an unknown filter, kind, type or author |
| T-LINK, T-KEY, T-KEY-DUP | link ends and keys |
| T-TONE, T-LAYOUT, T-MODIFIER | an unknown tone or layout, or a modifier on the wrong part |
| T-PARAM | knob declarations |
| T-SPACE, T-SPACE-TWICE, T-NO-SPACE | one `app()` per program |
| T-RUNTIME | a runtime lambda or action threw (only its part is marked) |
| T-LOOSE, T-ZONE-TWO | notes: a part made but never placed; two assignable streams in one zone |

Programs report plain JavaScript errors with their line.

Credits: Claude Computer and Tanke are by Ramon Marc ([moldandyeast.com](https://moldandyeast.com)).
