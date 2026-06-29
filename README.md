# Example Wiki: The Role of Gamma Synchrony in Early Visual Cortex

This is an example project-level wiki derived from the **[NeuroWiki-Project](https://github.com/ccnmaastricht/NeuroWiki-Project.git)** template. It is intended to illustrate how NeuroWiki can be used to build a literature-grounded wiki for a specific research project.

---

## Repo layout

```
project-root/
├── README.md             ← this file
├── CLAUDE.md             ← Claude Code context (auto-read on launch)
├── AGENTS.md             ← OpenAI Codex context
├── CURSOR.md             ← Cursor context
├── GEMINI.md             ← Gemini CLI context
├── project.md            ← project identity (source of truth; synced by setup.sh)
├── agent/                ← agent instruction files
│   ├── TEMPLATES.md      ← page templates, index structure, conflict resolution, citation rules
│   ├── INGESTION.md      ← workflow: processing new PDFs
│   ├── REVIEW.md         ← workflow: agent-assisted flag resolution
│   ├── REFINE_A.md       ← workflow: structural harmonization
│   ├── REFINE_B.md       ← workflow: depth audit
│   └── REFINE_C.md       ← workflow: cross-link audit
├── docs/                 ← human-facing documentation
│   ├── QUICKSTART.md     ← session invocation prompts
│   ├── VERIFICATION.md   ← human verification protocol
│   └── CONTRIBUTING.md   ← lab wiki submission guide
├── scripts/              ← tools
│   ├── validate.py       ← pre-submission structural validator
│   └── setup.sh          ← one-command project initialization
├── raw/                  ← source PDFs (git-ignored; never modified by agent)
└── wiki/
    ├── primary.bib       ← BibTeX: papers with PDFs in raw/
    ├── secondary.bib     ← BibTeX: papers cited within PDFs but not in raw/
    ├── log.md            ← human verification log
    ├── index.md          ← wiki root index; agent navigation entry point
    └── pages/
        └── <TYPE>_<slug>.md
```

## Using this wiki as a NeuroWiki example

This repo demonstrates the NeuroWiki conventions in practice:

- **Two-tier citation system** — `(@Key)` for PDFs verified in `raw/`, `(@Key†)` for secondary citations reconstructed from within those PDFs
- **Typed concept pages** — `PHE_`, `MOD_`, `THE_`, `REG_`, `CEL_`, `NET_`, `PAR_`, `TECH_`, `ANA_`, `DAT_` prefixes cover phenomena, models, theories, regions, cell types, circuits, paradigms, techniques, analysis methods, and datasets
- **Confidence tracking** — every `PHE_`, `MOD_`, `REG_`, `CEL_`, `NET_`, `TECH_`, and `ANA_` page carries an `established` / `debated` / `speculative` rating
- **Conflict surfacing** — papers that disagree are represented with both positions; irreconcilable conflicts are flagged for human review rather than silently resolved

See **[docs/QUICKSTART.md](docs/QUICKSTART.md)** for session invocation prompts.
See the **[NeuroWiki template](https://github.com/ccnmaastricht/NeuroWiki.git)** for setup instructions if starting a new project.

## Legal notice

NeuroWiki produces scholarly synthesis from papers users have legitimately accessed. This is standard academic practice equivalent to writing a literature review or review article.

**PDFs and the `raw/` folder:**
- `raw/` is excluded from git tracking by default (via `.gitignore`, set by `setup.sh`). PDFs are never committed to any repository.
- Users are responsible for ensuring they have legitimate access to any PDF placed in `raw/` through institutional site licenses, open access, or author-provided copies.
- PDFs must never be committed to shared or public repositories, and are explicitly excluded from lab wiki submissions.

**Wiki pages:**
- The synthesized wiki pages are the user's own scholarly work. They paraphrase and cite sources; they do not reproduce substantial portions of copyrighted text.
- Users should ensure wiki pages do not quote excessively from any single source.

NeuroWiki does not endorse or facilitate copyright infringement. When in doubt, use open access sources (PubMed Central, bioRxiv, papers published under CC licenses).

## License

NeuroWiki uses a dual license reflecting the two distinct layers of the project:

| Layer | License |
|-------|---------|
| Infrastructure files (CLAUDE.md, AGENTS.md, agent/*.md, scripts/*, validate.py, etc.) | Apache 2.0 with template exception |
| Wiki content (wiki/pages/, wiki/index.md, wiki/log.md, .bib files) | CC BY 4.0 |

**The template exception** means that using NeuroWiki to build a project wiki does not make your wiki a Derivative Work of NeuroWiki. Your wiki content is entirely your own — you may license it however you choose. The Apache 2.0 terms only apply if you distribute modified versions of the infrastructure files themselves.

**CC BY 4.0** on wiki content means anyone can reuse and build on the knowledge in the wiki as long as they credit the contributing lab(s). This is the standard license for open access scientific content.

See `LICENSE` (infrastructure) and `wiki/LICENSE` (content) for full terms.
