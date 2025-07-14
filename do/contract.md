<!-- DO-ROOT -->

# Command Map
| token    | meaning                                                                           |
|----------|-----------------------------------------------------------------------------------|
| `!run:`  | Open **do/contract.md** and execute the **Workflow Contract** below (algorithmic) |

---

# Workflow Contract (pure English)

1. **Save user prompt**  
   * Strip `!run:` + whitespace.  
   * Overwrite `do/indexInstruction.md` with the prompt.  
   * Backup previous version to `do/history_do/indexInstruction-YYYYMMDD-HHMM.md`.

2. **Generate tasks**  
   * Read `do/taskGenerator.md`.  
   * Replace `{{y}}` with the full content of `do/indexInstruction.md`.  
   * Execute the substituted file as a prompt.  
   * Overwrite `do/taskDefinition.md` with the result (backup first).

3. **Refine without regression**  
   * Read `do/implementWithoutRegression.md`.  
   * Replace `{{y}}` with the full content of `do/taskDefinition.md`.  
   * Execute the substituted file as a prompt.  
   * Overwrite `do/RefinedUserPrompt.md` with the result (backup first).

4. **Authorised output**  
   * Execute the content of `do/RefinedUserPrompt.md`.  

5. **Back-ups**  
   * Before every overwrite, copy the previous version to `do/history_do/{filename}-YYYYMMDD-HHMM.md`.

6. 📂 **Directory map** *(All paths are relative to repo root.)*

/                             (all other existing project files)
└─ do/                        (doc-chain workspace — NEW)
   ├─ contract.md             ← root contract (opened first, always)
   ├─ indexInstruction.md     ← user prompt (over-written)
   ├─ taskGenerator.md        ← constant x + variable y
   ├─ taskDefinition.md       ← generated
   ├─ implementWithoutRegression.md  ← constant x + variable y
   ├─ RefinedUserPrompt.md    ← final authorised prompt
   └─ history_do/             ← automatic backups