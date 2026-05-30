# PsychProfile

Official implementation of **PsychProfile: A dual-process retrieval-augmented framework for clinically grounded psychiatric decision support**.

PsychProfile is a retrieval-augmented reasoning framework designed to support psychiatric clinical decision-making by integrating:

* **Evidence-based knowledge** (clinical guidelines, literature, drug instructions)
* **Historical clinical practice** patterns derived from structured psychiatric case representations
* **Confidence-driven multi-turn reasoning** for dynamic coordination between complementary knowledge sources

The framework supports representative psychiatric decision-support tasks including:

* Diagnostic inference
* Medication recommendation
* Similar case retrieval

## Repository Structure
```
PsychProfile/
├── src/
│   ├── HyperGraph.py             # Clinical practice pattern graph construction
│   ├── graphrag.py               # nano-graph rag inteface
│   ├── evaluate.py               # Evaluation utilities of medication recommendation task
│   ├── prompt.py                 # Prompt templates
│   ├── _llm.py                   # LLM interface
│   ├── _utils.py                 # tools of normalizing model output
│   ├── main_PsychProfile.py          # Main pipeline entry
│   ├── main_SimilarCase.py       # Similar case retrieval pipeline
│   └── druginfo/                 # Drug-related reference resources
│
├── example_PsychProfile.py           # Minimal usage example for PsychRAG
├── example_SimilarCase.py        # Minimal usage example for similar case retrieval
└── README.md
```
## Quick Start
### Installation

Clone this repository:

```bash
git clone https://github.com/WuFaye/PsychProfile.git
cd PsychProfile
```

PsychProfile depends on the NanoGraphRAG framework. Please clone the NanoGraphRAG repository into the `src/` directory:
```bash
cd src
git clone https://github.com/gusye1234/nano-graphrag.git
cd ..
```
Install required dependencies:
```bash
pip install -r requirements.txt
```
### Model Configuration

PsychProfile supports multiple LLM backends.

The current implementation includes ready-to-use interfaces for:

* DeepSeek API
* SiliconFlow API (e.g., Qwen models)
* Doubao API
* Local Qwen deployment (Hugging Face Transformers)

Users may also replace the model interface in `src/_llm.py` to integrate other compatible LLM providers.

#### Linux / macOS

Set the required API key depending on the backend you intend to use.

For DeepSeek:

```bash
export DEEPSEEK_API_KEY="your_deepseek_api_key"
```

For SiliconFlow:

```bash
export SILICONFLOW_API_KEY="your_siliconflow_api_key"
```

For Doubao:

```bash
export DOUBAO_API_KEY="your_doubao_api_key"
```


#### Windows (PowerShell)

```powershell
$env:DEEPSEEK_API_KEY="your_deepseek_api_key"
$env:SILICONFLOW_API_KEY="your_siliconflow_api_key"
$env:DOUBAO_API_KEY="your_doubao_api_key"
```

#### Local Model Inference (Optional)

PsychProfile also supports local inference using Hugging Face models.  
For local deployment, no API key is required, but users should ensure:

- model weights are available locally
- CUDA-compatible GPU resources are properly configured
- device settings in `src/_llm.py` match the local hardware environment

### Run PsychProfile
Run PsychProfile

```
python example_PsychProfile.py
```


Run Similar Case Retrieval

```
python example_SimilarCase.py
```

## Data Availability

The clinical case data used in this study are not publicly available due to patient privacy, ethical restrictions, and institutional data governance requirements.

Only the code framework and non-sensitive supporting resources are provided in this repository.
