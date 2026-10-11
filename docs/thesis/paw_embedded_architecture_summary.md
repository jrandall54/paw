# PAW Master's Thesis: Embedded AI Architecture

## 1. The Vision: Embedded Local Inference
Instead of relying on large, generalized cloud models or bulky external local servers (like LM Studio), the PAW application will utilize **embedded local inference**. The application will compile a lightweight C++ inference engine (such as `llama.cpp` or ONNX Runtime) directly into its binary. This allows the app to load quantized model weights into system RAM/VRAM and execute the neural network entirely offline, as an internal background thread.

## 2. Hyper-Focused, Small-Parameter Models
Massive 30B+ parameter cloud models are overkill for the specific, deterministic tasks within the PAW framework. Instead, the application will use a suite of small, specialized models (1B to 7B parameters, such as quantized versions of Llama-3 or Qwen-2.5-Coder) tailored for specific pedagogical jobs:
*   **The Evaluator (Stage 2 & 6):** A 1B–3B parameter model fine-tuned specifically for strict classification and semantic grading (e.g., verifying if a user's answer matches the target concept).
*   **The Predictor (Stage 3):** A 3B–7B parameter code-oriented model specialized in structural code comparison.
*   **The Socratic Debugger (Stage 4b):** A 3B–7B parameter model fine-tuned on compiler error logs to parse stack traces and generate targeted learning clues without providing direct answers.

## 3. The AI Engineering Lifecycle (Thesis Roadmap)
Building this system requires executing the end-to-end AI engineering pipeline locally:
1.  **Data Generation:** Curating synthetic datasets of strict pedagogical interactions (e.g., bad code, common student misconceptions, and non-sycophantic Socratic critiques).
2.  **Training & Fine-Tuning:** Using techniques like LoRA (Low-Rank Adaptation) on a dedicated home server to fine-tune open-weights base models, specializing them purely as PAW tutors.
3.  **Quantization:** Compressing the fine-tuned models into 4-bit or 8-bit precision (such as `.gguf` formats) so they run blazingly fast with minimal compute footprint.
4.  **Embedding:** Linking the frontend application (CLI or IDE plugin wrapper) directly against the local inference engine, bundling the custom "PAW Specialist" models natively inside the software architecture.

This architecture bridges the pedagogical state machine with edge-computing AI, turning PAW into a self-contained, offline educational runtime.
