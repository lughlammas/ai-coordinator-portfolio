# GitHub & Project Estate Consolidation — Self-Directed Case Study

> **Self-directed / internal case study. Not paid client work.**
> Subject: my own GitHub account ([@lughlammas](https://github.com/lughlammas)) and local project workspace, consolidated under ARBOCK LABS on 7 October 2026. All times are BRT (UTC−3). Every number below comes from the GitHub API, the repositories themselves or recorded tool output from that day. No revenue, leads, client outcomes or time savings are claimed.

**Author:** Guilherme Cavalcanti · **Method:** human-directed AI-assisted development (see [HUMAN_DIRECTED_AI_WORKFLOW.md](../docs/HUMAN_DIRECTED_AI_WORKFLOW.md))

## Summary

The work started with a mix of public course exercises, product repositories and unversioned local projects. Over one working day it became a curated public portfolio, with private work kept separate, every import secret-scanned and every irreversible decision left to the owner. The method is the same one used for an inherited codebase: inventory, verify sources against builds, classify, then publish only what is ready, documenting what was deliberately left alone.

## 1. Initial condition

Verified in a read-only audit at about 11:50, before any change:

- **Fragmented public presence.** There were 39 public repositories. Most were 2025 course exercises with no description or README, and 14 public repositories use an exercise branch as their default instead of `main`, which is still the case at closure. The profile showed a short display name, an empty bio and no pinned repositories.
- **Mixed presentation.** Repository descriptions mixed Portuguese and English. The portfolio site misspelled the surname and carried dated "this week" availability text.
- **Engine without public source.** The C++ chess engine (Lughnasadh) appeared only as compiled `.so` files inside two app repositories, plus symlinks pointing to a machine-local build path that is broken for anyone who clones.
- **No CI anywhere.** None of the 39 public repositories had a GitHub Actions workflow. Only three had releases.
- **Version drift.** The engine source implemented 0.4.0, according to its UCI identity string and NEWS file, while its README, CMake file and ChangeLog still said 0.3.0.
- **Duplicated artifacts in the workspace:**
  - archives byte-identical to working folders;
  - release bundles and binaries split into parts;
  - older engine clones whose content was already in Git history.
- **Overlapping public repositories.** Of the 79 files in `tron-o-legado`, 54 are identical in path and content to files in `sherlock`.
- **Sensitive material next to source:**
  - Android signing keys and keystore property files;
  - a personal photograph and a third-party image in an asset folder;
  - tooling reports quoting unpublished manuscripts.
- **Uneven documentation.** Flagship READMEs answered basic reviewer questions inconsistently. A 10-question matrix was used to score them: what it is, problem, my role, technologies, what works, how to test, what is experimental, build/release, role of AI, validation.

## 2. Constraints and approval gates

These rules were set before any work and held throughout:

- **Owner approval only:**
  - deleting repositories, branches or releases;
  - changing visibility;
  - rewriting history or force-pushing;
  - changing licences;
  - touching secrets, billing or DNS;
  - renaming the account.
- **No invented licences.** Private projects without a licence received only "All rights reserved — licensing under review."
- **Ambiguity handling.** If a project's identity was ambiguous, work stopped on that project only, and the ambiguity was documented instead of guessed.
- **What never gets published:** secrets, signing material, personal data, private manuscripts or `local.properties`. Synthetic fixtures replace private data where tests need it.
- **Protected repositories.** Some public repositories were explicitly out of scope and were not modified.

## 3. Process

1. **Inventory and read-only audit.**
   - Used the GitHub API plus a shallow clone of every public repository, with links tested by `curl`.
   - Read the profile and pin state through GraphQL.
   - Scored each candidate flagship README against the 10-question matrix.
   - Classified every recommendation as SAFE, REVIEW or APPROVAL REQUIRED.
2. **Source verification and canonical-project identification.** For each local project the audit recorded:
   - the canonical source folder, version, stack and licence found;
   - whether source actually existed.

   Versions were taken from code and changelogs, not from READMEs. For the engine, the README, CMake version and ChangeLog were corrected to match the 0.4.0 code.
3. **Duplicate detection.**
   - Archives were compared with the folders they claimed to contain.
   - Public repositories were compared blob by blob, which found the 54-file overlap above.
   - Older engine snapshots were confirmed to be already present as commits, so nothing was lost by not importing them again.
4. **Source vs. build.** Excluded from version control:
   - third-party engine binaries (over 100 MB each);
   - APK/AAB outputs, build directories and generated asset copies.

   The only binary kept was a small WebAssembly engine build that one project's build step needs, and the import report records why.
5. **Public/private and IP classification.**
   - Five previously unversioned projects were imported into new **private** repositories, with sanitised docs (machine-local paths replaced by generic instructions), `.gitignore` rules for keys and local properties, and the placeholder licence above.
   - Manuscript-derived reports, the personal photograph and the third-party image were excluded.
   - One verification package kept machine-local paths byte-for-byte, because those files are covered by published SHA-256 manifests. That exception is documented in its README rather than silently "cleaned".
   - The engine repository was made public during the consolidation under its existing MIT licence.
6. **Ambiguous projects.**
   - **Divergent derivations.** One small static prototype existed as an original package and two later derivations, and none of the three was a superset of the others. Work stopped and the ambiguity was reported. After the owner decided, all three went into one private repository as separate commits: original, then derivation 1, then derivation 2. Neither derivation is presented as a "clean" version of the other.
   - **Incomplete source.** A game prototype lacked its canonical engine project file and assets. It was marked **SOURCE INCOMPLETE — WAITING FOR CANONICAL PROJECT**, and nothing was imported.
7. **Secret hygiene.**
   - `gitleaks` 8.21.2 ran in directory mode before each push, and over the full history of all 40 public repositories plus one private repository: **0 findings**. A filename search for `.jks`, `.keystore`, `.p12`, `.pem`, `.env`, `local.properties` and `google-services.json` across history found only a harmless example file.
   - A debug-keystore password was removed from a public Android README ([sherlock@8543997](https://github.com/lughlammas/sherlock/commit/8543997)). The keystore file itself was never committed. The old value remains in earlier history; rewriting it would need owner approval and was judged unnecessary for a debug-only key that is never used for release.
   - The production signing key was neither moved nor committed. Its need for an offline backup was recorded as an owner action.
8. **Licensing flags.** These were raised without changing any licence:
   - A private project bundles a third-party GPL-3.0 chess engine in its desktop and Android builds. The audit listed the obligations that would apply to any future distribution; a separate licence audit is pending.
   - A public web project is MIT-licensed but depends on a GPL-3.0-or-later board library. Distributed bundles are therefore combined works under the GPL, so it was flagged before any commercial use.
   - Public repositories without a `LICENSE` were flagged as owner decisions, not filled in.
9. **Identity and metadata cleanup.**
   - Fixed the surname spelling and removed the dated wording on the portfolio site ([lughlammas.github.io@d310509](https://github.com/lughlammas/lughlammas.github.io/commit/d310509)).
   - Rewrote the profile README in English around the selected projects ([lughlammas@2caf8f3](https://github.com/lughlammas/lughlammas/commit/2caf8f3)).
   - Gave the five flagships English descriptions and topics.
   - Changed the current brand to ARBOCK LABS while preserving the historical "Lugh Labs" origin in `AUTHORS` ([lughnasadh@eff2238](https://github.com/lughlammas/lughnasadh/commit/eff2238)).
   - One historical commit author with the old surname spelling was left as is; fixing it would require rewriting history.
10. **Flagship selection.** Five public projects were selected by technical depth, completeness, reproducibility and engineering evidence, not by recency: [SHERLOCK](https://github.com/lughlammas/sherlock), [Lughnasadh](https://github.com/lughlammas/lughnasadh), [comercial-template](https://github.com/lughlammas/comercial-template), [Êxodus](https://github.com/lughlammas/exodus) and this repository.
11. **CI and technical validation.**
    - The engine gained a GitHub Actions workflow that builds the C++20 source and asserts the UCI identity and `perft 5 = 4,865,609` from the start position. It passed on [fd7dc48](https://github.com/lughlammas/lughnasadh/commit/fd7dc48), [eff2238](https://github.com/lughlammas/lughnasadh/commit/eff2238) and [b2956a0](https://github.com/lughlammas/lughnasadh/commit/b2956a0).
    - Locally, the 0.4.0 build was also checked against Kiwipete `perft 4 = 4,085,603`, the corrected promotion output (`a7a8q`), `go infinite` followed by `stop`, and `go nodes`.
    - Where imported private projects had test suites, the suites were re-run from clean copies of exactly what was pushed.
12. **Branch and conflict review.**
    - A release branch prepared in one session conflicted with a newer `main` that a parallel agent session had pushed minutes earlier, in four files.
    - The merge was aborted, no tag was created, nothing was force-merged and no visibility was changed. The conflict was reported with options: redo the change on top of the new `main`, or resolve it by hand.
    - The newer `main` was itself verified read-only: secret scan, build and perft.
13. **Commercial positioning.** The profile README gained a short, factual "Available for project work" section ([lughlammas@cbe7c1f](https://github.com/lughlammas/lughlammas/commit/cbe7c1f)). It describes engagement types without prices, client names or results.
14. **Handoff and closure reporting.** Each phase ended with a written report that was not published:
    - **Audit:** current state, proposed pins, corrections, a broken-link list, and a SAFE/REVIEW/APPROVAL REQUIRED plan.
    - **Import report:** for every project, the path, version, stack, whether source was found, excluded files, licence found, problems, build/test commands, and the commit SHA or the reason for stopping.
    - **Decision log:** the owner's per-project decisions.
    - **Status report:** the public page and two product lines, closing with explicit "could not verify" items.

## 4. Human-directed multi-agent setup

I set the goals, constraints and approval gates, and made every decision on visibility, licensing, branding and ambiguous projects. AI coding agents did the inventory, comparisons, scans, edits, builds and report drafting, under the rules in section 2.

Two agent sessions worked on the same repositories concurrently. That is how the branch conflict in step 12 arose, and why the rule "fetch, inspect, never overwrite newer work, stop on conflict" matters. No agent ran unattended against production systems, and every push was a normal, non-forced commit.

## 5. Results (verifiable)

| Outcome | Evidence |
|---|---|
| Five curated public flagship projects, each with an English description and topics | [Profile README](https://github.com/lughlammas/lughlammas), repository pages |
| Private work separated from public evidence | 7 private and 40 public repositories (GitHub API, 7 Oct 2026); a text search of the ten main public repositories found no private project names |
| Engine source public with reproducible CI validation | [lughnasadh Actions](https://github.com/lughlammas/lughnasadh/actions) |
| Coherent, English-first profile | [lughlammas/lughlammas](https://github.com/lughlammas/lughlammas) |
| Secret scan over all public history: 0 findings | gitleaks 8.21.2, as described in step 7 |
| Credential text removed from a public README | [sherlock@8543997](https://github.com/lughlammas/sherlock/commit/8543997) |
| Historical and course repositories preserved, not deleted | 28 public repositories with a last push in 2025 remain |
| Follow-up: one flagship made easier to verify | [comercial-template product walkthrough](https://github.com/lughlammas/comercial-template/blob/main/docs/PRODUCT_WALKTHROUGH.md): 24 unit tests, a browser smoke test and real local screenshots |

## 6. Deliberately not done

- No repository was deleted or archived. The only visibility change was publishing the engine repository, and no private project was made public.
- No history was rewritten and nothing was force-pushed.
- No licence terms were changed, and no licence was added to a public repository that lacked one. The only licence-file edit was a copyright-holder line updated for the brand.
- The account was not renamed. The audit found that the change would take the user Pages site offline, because GitHub does not redirect user Pages.
- Private projects were not prepared for commercial distribution.

## 7. Open items at closure

- Profile bio and pinned repositories can only be changed through the GitHub web UI with the current token, so they remain manual owner actions.
- The stale release branch on the engine repository is still there, since deleting it needs approval, and there is no `v0.4.0` tag yet.
- Two app repositories still contain a symlink to a machine-local build path.
- Several public projects have no `LICENSE`, including `sherlock`, `comercial-template` and `tron-o-legado`; adding one is an owner decision.
- `tron-o-legado` still overlaps heavily with `sherlock`.
- Whether to archive the course-exercise repositories is pending owner review.

## 8. What this demonstrates

- Reading an unfamiliar estate quickly and stating its condition with counts that can be checked.
- Separating source from build output and public evidence from private IP before anything is published.
- Treating ambiguity and conflicts as stop conditions, not things to guess around.
- Leaving a written trail (reports, commit SHAs, open items) that another person can pick up without the original context.
