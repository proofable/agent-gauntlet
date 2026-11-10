# Proofable's entry in the NVIDIA Agent Gauntlet

**Proofable won the NVIDIA Developer Live Agent Gauntlet on 5 November 2026.** It took the final in round four with the top score of the tournament, 98.00, across 20 teams and 11 heats.

Each agent was dropped into an MCP server it had never seen, with hidden tools, encrypted data and no documentation, and had to solve it live with the clock running. Every call this agent made was decided before it ran, by a permission it carried, and left a receipt.

This repository is the exact submission NVIDIA ran.

## Check it is the same file

```bash
sha256sum -c proofable-submission.tar.gz.sha256
```

The expected hash is `7b00e595ac4dbe4ff81bdb972af6f0d5b2473c966a126a587f5c4d79c3d5f601`.

## What is inside

```bash
tar -xzf proofable-submission.tar.gz && cd gauntlet-submission
```

| File | What it does |
|---|---|
| `proofable_gate.py` | Decides every tool call before it runs, and writes each decision and result into a hash-chained receipt |
| `proofable_authority.py` | Proofable's permission engine, ported to Python, that the gate asks about each call |
| `proofable_authority_contract.json` | The public contract those rules follow, pinned by hash |
| `proofable_agent.py` | The agent: explores the server, solves the challenge, submits |
| `agent_tools.py` | Turns the server's tools, resources and prompts into calls the model can make |
| `my_strategy.py` | Model choice, prompts and time budgets |
| `arena_clients/`, `base_strategy.py`, `model_selector.py` | NVIDIA's starter kit, unchanged |

Reading a clue, sending an answer and running code were allowed. Anything destructive was refused before it ran. The tools the challenge needed were granted as one named group, so the agent could not widen its own reach mid-run.

## More

- How it went, in our words: [Proofable won NVIDIA's Live Agent Gauntlet](https://proofable.me/proof/0x622cce0f83068f32e570fab1f3eb5a4ad9a554bc3157bab5bddf41454260a487)
- Every benchmark, beside the tools teams use today: [proofable.me/benchmarks](https://proofable.me/benchmarks)
- Put the same limits on your own agent: [github.com/proofable/agent](https://github.com/proofable/agent)
