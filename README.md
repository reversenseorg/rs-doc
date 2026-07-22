# Reversense documentation

This repository holds the documentation for **Reversense platform**.

The documentation is written in **Markdown** inside the `docs/` folder and is
published automatically to GitHub Pages on every push to `main`.

📖 **Online documentation:** [https://reversenseorg.github.io/rs-doc/](https://reversenseorg.github.io/rs-doc/)

---

## A. Install and preview the docs locally

You need **Python 3.8+** installed on your machine.

### A.1. Clone the repository

```bash
git clone https://github.com/reversenseorg/rs-doc.git
cd rs-doc
```

### A.2. (Recommended) Create a virtual environment

This avoids installing the dependencies globally on your system.

```bash
python -m venv .venv

# Activate the environment:
source .venv/bin/activate      # macOS / Linux
.venv\Scripts\activate         # Windows
```

### A.3. Install the dependencies

```bash
pip install -r requirements.txt
```

### A.4. Start the local server

```bash
mkdocs serve
```

Then open **http://127.0.0.1:8000** in your browser. The site reloads
automatically whenever you change a `.md` file, so you see your edits in real
time.

To build the static site without serving it (rarely needed, since deployment
is automatic):

```bash
mkdocs build
```

---

## B. Contributing

Contributions are welcome, whether it's fixing a typo, clarifying an
explanation, or adding a page.

### B.1. Workflow

1. **Fork** the repository (the _Fork_ button at the top right on GitHub), or
   create a branch if you have write access.
2. **Create a branch** for your change:
   ```bash
   git checkout -b docs/my-change
   ```
3. **Edit or add** Markdown files in `docs/`.
4. **Check the result locally** with `mkdocs serve` before proposing your
   changes.
5. **Commit and push:**
   ```bash
   git add .
   git commit -m "docs: briefly describe your change"
   git push origin docs/my-change
   ```
6. **Open a Pull Request** against the `main` branch.

### B.2. Adding a new page

1. Create the file, for example `docs/installation.md`.
2. Declare it in the `nav:` section of `mkdocs.yml` so it appears in the menu:
   ```yaml
   nav:
     - Home: index.md
     - Getting started: guide.md
     - Installation: installation.md   # ← new page
   ```

### B.3. A few conventions

- One page = one clear, focused `.md` file.
- Use `##` / `###` headings to add structure (the table of contents is
  generated automatically from them).
- Links between pages are **relative**: `[see the guide](guide.md)`.
- The deployment build uses the `--strict` option: a broken link or a page
  missing from the navigation will **fail** the publication. Test locally to
  avoid surprises.

---

## C. Repository structure

```
rs-doc/
├── mkdocs.yml                      # MkDocs configuration (theme, menu, options)
├── requirements.txt                # Python dependencies (mkdocs-material)
├── README.md                       # This file
│
├── .github/
│   └── workflows/
│       └── deploy.yml              # Automatic deployment to GitHub Pages
│
└── docs/                           # ← All the documentation content lives here
    ├── index.md                    # Home page
    ├── guide.md                    # Any page
    └── assets/
        └── images/                 # Documentation images
```


## D. Images

Put all images in **`docs/assets/images/`**. That way they are bundled into
the site at build time.

### D.1. Inserting an image in a page

Use a **relative path** from the Markdown file to the image.

From a page at the root of `docs/` (like `index.md` or `guide.md`):

```markdown
![Alt text describing the image](assets/images/my-diagram.png)
```

From a page stored in a **subfolder** of `docs/`, go up one level with `../`:

```markdown
![Alt text](../assets/images/my-diagram.png)
```

### D.2. Best practices

- Use **descriptive file names** in lowercase, with no spaces or accents:
  `global-architecture.png` rather than `Diagram 1.png`.
- Always provide **alt text** (inside the square brackets): it matters for
  accessibility and search-engine indexing.
- Prefer **lightweight** (compressed) images so the site stays fast. Use
  `.png` for screenshots and diagrams, `.jpg` for photos, and `.svg` for
  vector diagrams.
- You can create **subfolders** if you have many images, for example
  `docs/assets/images/tutorials/` — just remember to adjust the path.