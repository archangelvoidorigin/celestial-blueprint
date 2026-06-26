---
title: "Stage 4 — The Nerves — Verification Checklist"
tags: [verify, stage-4, mcp]
status: "Not Started"
date_created: 2026-06-25
---

# Stage 4 — The Nerves — Verification Checklist

All commands run from `Celestial_Blueprint/` (project root) with the backend venv python available:

```bash
cd /home/void-yggdrasil/CHAOS_DAO_FORGE/00_CORTEX/01_CREATION_REALM/Celestial_Blueprint
PYTHON=backend/.venv/bin/python3
```

---

## Phase 4.1 — Scaffold

### T4.1.01 — mcp/ package

- [ ] `mcp/__init__.py` exists
- [ ] `mcp/requirements.txt` contains `httpx`
- [ ] Backend venv has httpx

```bash
test -f mcp/__init__.py && echo "__init__ ok"
grep -q httpx mcp/requirements.txt && echo "requirements ok"
$PYTHON -c "import httpx; print('httpx ok')"
```

Expected: three `ok` lines.

---

## Phase 4.2 — MCP Server

### T4.2.01 — server.py

- [ ] `mcp/server.py` exists and is executable
- [ ] `--test` flag prints 14 tool names
- [ ] `tools/list` returns 14 tools
- [ ] `initialize` returns `serverInfo.name == "celestial-blueprint"`

```bash
test -x mcp/server.py && echo "executable ok"
$PYTHON mcp/server.py --test | head -1

echo '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}' \
  | $PYTHON mcp/server.py \
  | $PYTHON -c "import json,sys; d=json.load(sys.stdin); n=len(d['result']['tools']); assert n==14,n; print(f'{n} tools ok')"

echo '{"jsonrpc":"2.0","id":2,"method":"initialize","params":{}}' \
  | $PYTHON mcp/server.py \
  | $PYTHON -c "import json,sys; d=json.load(sys.stdin); assert d['result']['serverInfo']['name']=='celestial-blueprint'; print('initialize ok')"
```

Expected: `executable ok`, `Tools available: 14`, `14 tools ok`, `initialize ok`.

---

## Phase 4.3 — Registration

### T4.3.01 — mcp-lazy entry

- [ ] `mcp-lazy-servers.json` contains `"celestial-blueprint"` key
- [ ] File is valid JSON
- [ ] All existing server entries still present

```bash
FILE=/home/void-yggdrasil/CHAOS_DAO_FORGE/03_TOOLBOX/tools/mcp-lazy/mcp-lazy-servers.json
python3 -c "import json; d=json.load(open('$FILE')); assert 'celestial-blueprint' in d['servers']; print('entry ok')"
python3 -c "import json; d=json.load(open('$FILE')); print('servers:', sorted(d['servers'].keys()))"
```

Expected: `entry ok` then a sorted list including `celestial-blueprint` plus all previously existing entries.

---

## Phase 4.4 — Skill Wiring

### T4.4.01 — SKILL.md MCP tools

- [ ] `skill/celestial-blueprint/SKILL.md` exists
- [ ] Contains `## MCP Tools` section
- [ ] All 14 tool names present

```bash
grep -q "## MCP Tools" skill/celestial-blueprint/SKILL.md && echo "section ok"
for t in blueprint_list blueprint_get blueprint_create blueprint_patch blueprint_archive node_add edge_add \
          assumption_add decision_add risk_add chronicle_add blueprint_export blueprint_import blueprint_rebuild; do
  grep -q "$t" skill/celestial-blueprint/SKILL.md || echo "MISSING: $t"
done
echo "all tools checked"
```

Expected: `section ok`, no `MISSING` lines, `all tools checked`.

---

## Live MCP checks [LIVE]

These require the backend running: `uvicorn app.main:app --port 8787` (from `backend/` with venv active).

- [ ] `blueprint_list` returns a JSON array
- [ ] `blueprint_create` creates a blueprint and returns its ID
- [ ] `node_add` adds a node and returns the updated blueprint
- [ ] `blueprint_export` returns markdown starting with `---`

```bash
# blueprint_list
echo '{"jsonrpc":"2.0","id":10,"method":"tools/call","params":{"name":"blueprint_list","arguments":{}}}' \
  | $PYTHON mcp/server.py

# blueprint_create
echo '{"jsonrpc":"2.0","id":11,"method":"tools/call","params":{"name":"blueprint_create","arguments":{"name":"MCP Test","tier":"small"}}}' \
  | $PYTHON mcp/server.py
```

---

## Stage 4 done when

`mcp/server.py --test` prints 14 tools; `tools/list` returns 14; `mcp-lazy-servers.json` has the entry; SKILL.md lists all tools; `[LIVE]` checks pass with backend running.
