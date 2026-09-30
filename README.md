# Run a local LLM in VS Code Copilot Chat with OpenVINO Model Server

Use **[Qwen3.8-27B INT4 (OpenVINO)](https://huggingface.co/Morteza89/qwen3.8-27b-int4-ov)** as a **local model in the VS Code Copilot Chat model picker**, running on your **Intel AI PC GPU**. No cloud, no per-token cost, and your code stays on your machine.

```
VS Code Copilot Chat ──(OpenAI Chat Completions API)──► OVMS on 127.0.0.1:8000 ──► OpenVINO ──► Intel Arc GPU
```

## What's inside

**[`Qwen3.8-27B_OVMS_VSCode_Local_Setup.ipynb`](Qwen3.8-27B_OVMS_VSCode_Local_Setup.ipynb)** is a step-by-step notebook that:

1. Creates a Python environment and installs OpenVINO
2. Downloads the model from Hugging Face
3. Checks that it runs on your GPU (with speed metrics)
4. Installs **OpenVINO Model Server (OVMS)** with SHA-256 verification
5. Serves the model with an OpenAI-compatible API, including **tool calling** (for Copilot **Agent** mode) and reasoning
6. Registers it in VS Code as a **Custom Endpoint** model
7. Makes sure it answers in English, and shows how to stop and restart the server
8. Includes a **troubleshooting table** covering every problem we ran into

## Requirements

- Windows 11, Intel Core Ultra with an Intel Arc iGPU (or an Intel Arc dGPU)
- 32 GB RAM minimum (64 GB recommended), about 25 GB free disk space
- Python 3.12, VS Code with GitHub Copilot Chat and the Jupyter extension
- On Copilot Business/Enterprise plans, your admin must allow bring-your-own models

## Quick start

```powershell
py -3.12 -m venv C:\ov_local_llm\.venv
C:\ov_local_llm\.venv\Scripts\python.exe -m pip install --upgrade pip ipykernel
```

Open the notebook in VS Code, select the `C:\ov_local_llm\.venv` kernel, and run the cells from top to bottom.

## Tested with

| Component | Version |
|---|---|
| Hardware | Intel Core Ultra X7 358H, Intel Arc B390 iGPU, 64 GB RAM |
| GPU driver | 32.0.101.8860 |
| OpenVINO / GenAI | 2026.4.0rc1 / 2026.4.0.0rc1 |
| OpenVINO Model Server | 2026.4.0 |
| VS Code | 1.140.0 |
| Date | September 2026 |

Performance on Arc B390: about **7.4 tokens/s** generation. Ask mode is faster than Agent mode, because Agent mode sends much longer prompts.

## Notes

- The model is an unofficial community conversion of [Qwen/Qwen3.8-27B](https://huggingface.co/Qwen/Qwen3.8-27B) (Apache-2.0).
- The VS Code model-management UI changes often. If a step looks different, please open an issue.
