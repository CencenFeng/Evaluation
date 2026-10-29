# COMP8410 Assignment 1. 

Compare two AI systems for a university student platform: **System A** and **System B**, tested in 4 pairs, for different purpose.

- `pair1_...` to `pair4_...` notebooks: each one runs both models on the same inputs and measures them.
- `final_evaluation.ipynb`: pulls everything together (cost, my ratings, governance) and picks a winner per pair.
- `data/`: the inputs. `outputs/`: what the models made. `results/`: the numbers.
- `user_test/`: the blind rating packs I filled in (see `user_test/README.md`).

All outputs and results are already included, so you can just read the notebooks without running anything.

## How to re-run

1. **Install what you need.** The basics, for every notebook:
   ```
   pip install jupyterlab pandas matplotlib pillow imageio scikit-learn
   ```
   Then only the extras for the pairs you want to re-run:
   - Pair 1: `pip install ctgan ForestDiffusion ucimlrepo`
   - Pair 2: `pip install openai`
   - Pair 3: `pip install gradio_client trimesh`
   - Pair 4: `pip install torch diffusers transformers accelerate sentencepiece protobuf ftfy imageio-ffmpeg`
2. **Run the pair notebooks top to bottom.** A few need something extra:
   - **Pair 2** needs a free Groq API key saved in a file called `groq_key.txt` (mine isn't included). Heads up: the LLM's replies can come out a bit different each time, even with temperature set to 0, so your numbers may not match mine exactly. The decisions (what the question is about, whether to escalate) were stable in my runs, mostly the wording changes.
   - **Pair 3** needs TripoSR downloaded into its own folder, step 1 of the notebook shows how. TRELLIS runs on a free Hugging Face page, so log in first with `hf auth login`.
   - **Pair 4** needs a proper NVIDIA GPU (I used a lab RTX 4090). The first run downloads about 18 GB of models.
3. **Run `final_evaluation.ipynb` last.** It reads the results and my ratings and prints the final scores.

Pairs 1–3 run fine on a laptop. Only Pair 4 needs the GPU.
