# tnote

Tiny terminal note CLI for quickly saving ideas, reminders, and scratch notes from the shell.

`tnote` is made for those moments when you want to quickly write something down without opening an editor, notes app, or polluting your shell history with random comments.

## Features

* Save notes directly from the terminal
* Store notes locally in SQLite
* Add optional categories
* Add optional tags
* List recent notes
* Search saved notes
* Delete notes by ID
* No server, account, or sync required

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/tnote.git
cd tnote
```

Make the script executable:

```bash
chmod +x tnote
```

Move it into your local bin directory:

```bash
mkdir -p ~/.local/bin
mv tnote ~/.local/bin/tnote
```

Make sure `~/.local/bin` is in your `PATH`:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

For zsh users:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

## Usage

Save a note:

```bash
tnote "fix printer config later"
```

Save a note with a category:

```bash
tnote "look into SQLite FTS" -c dev
```

Save a note with tags:

```bash
tnote "buy oat milk" -c errands --tag shopping
```

List recent notes:

```bash
tnote list
```

Short alias:

```bash
tnote ls
```

Search notes:

```bash
tnote search sqlite
```

Short alias:

```bash
tnote s sqlite
```

Delete a note:

```bash
tnote delete 3
```

Short alias:

```bash
tnote rm 3
```

Show the database path:

```bash
tnote path
```

Show help:

```bash
tnote -h
```

## Import notes from a text file

Create a text file with one note per line:

```txt
# fix ssh config later
# file ticket because of printer failure
# idea: tiny CLI bookmark tool
```

Import the file:

```bash
sed 's/^#[[:space:]]*//' ./notes-to-import.txt \
| while IFS= read -r note; do
    [ -n "$note" ] && tnote "$note"
  done
```

Import with a category:

```bash
sed 's/^#[[:space:]]*//' ./notes-to-import.txt \
| while IFS= read -r note; do
    [ -n "$note" ] && tnote "$note" -c history
  done
```

## Storage

Notes are stored locally in:

```bash
~/.local/share/tnote/notes.sqlite3
```

Nothing leaves your machine.

## Why?

Sometimes you just want to write:

```bash
tnote "remember to check this later"
```

and move on.

`tnote` is a tiny alternative to leaving random `# comments` in your shell history.

## License

MIT

