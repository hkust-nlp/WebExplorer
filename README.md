# WebExplorer: Explore and Evolve for Training Long-Horizon Web Agents

<!-- [![Paper](https://img.shields.io/badge/Paper-arXiv-red.svg)](https://arxiv.org/abs/2025.xxx) -->
[![Model](https://img.shields.io/badge/🤗%20Model-WebExplorer--8B-blue)](https://huggingface.co/hkust-nlp/WebExplorer-8B)
[![Dataset](https://img.shields.io/badge/🤗%20Dataset-WebExplorer--QA-green)](https://huggingface.co/datasets/hkust-nlp/WebExplorer-QA)
[![License](https://img.shields.io/badge/License-Apache--2.0-green.svg)](LICENSE)

## Abstract

WebExplorer introduces a systematic approach for training long-horizon web agents through model-based exploration and iterative query evolution. Our method generates challenging query-answer pairs requiring multi-step reasoning and complex web navigation, achieving state-of-the-art performance at 8B parameter scale.

<div align="center">
  <img src="assets/pipeline.png" alt="WebExplorer Pipeline" width="800"/>
  <p><em>WebExplorer-QA Construction Pipeline</em></p>
</div>


## 🔥 News
- **[2025/01/08]** :fire: We released our model [WebExplorer-8B](https://huggingface.co/hkust-nlp/WebExplorer-8B) and dataset [WebExplorer-QA](https://huggingface.co/datasets/hkust-nlp/WebExplorer-QA) with 100 high-quality query-answer pairs!


## 📊 Key Results

<div align="center">
  <img src="assets/scores.png" alt="Performance Comparison" width="800"/>
  <p><em>Performance comparison of WebExplorer-8B across different benchmarks</em></p>
</div>

| Benchmark        | WebExplorer-8B |
|------------------|----------------|
| BrowseComp-en    | **15.7** |
| BrowseComp-zh    | **32.0** |
| GAIA             | **50.0** |
| WebWalkerQA      | **62.7** |
| FRAMES           | **75.7** |
| Xbench-DS        | **53.7** |
| HLE              | **17.3** |

## ✨ Key Features

- 🌐 **Long-horizon Reasoning**: Supports up to 128K context length and 100 tool calling turns
- 🛠️ **Tool Utilization**: Masters search and browse functionalities
- 🏆 **State-of-the-art Performance**: Achieves best-in-class results among models under 10B parameters





## 🚀 Resources

### 🤗 Models
| Model Name | Size | Description | Link |
|:-----------|:-----|:------------|:----:|
| **WebExplorer-8B** | 8B | Long-horizon web agent trained on WebExplorer-QA | [🤗 HuggingFace](https://huggingface.co/hkust-nlp/WebExplorer-8B) |

### 📚 Datasets
| Dataset Name | Size | Description | Link |
|:------------:|:-----|:------------|:----:|
| **WebExplorer-QA** | 100 samples | High-quality query-answer pairs for web agent training | [🤗 HuggingFace](https://huggingface.co/datasets/hkust-nlp/WebExplorer-QA) |


## 🛠️ Tool Schema

WebExplorer-8B supports two tools for web interaction:

### 1. Browse Tool

```json
{
    "name": "browse",
    "type": "function",
    "description": "Extract specific information from a webpage",
    "parameters": {
        "type": "object",
        "properties": {
            "url": {
                "type": "string",
                "description": "Target URL to browse. The webpage content will be processed by the LLM for information extraction."
            },
            "query": {
                "type": "string",
                "description": "Specific query about the webpage content. The LLM will analyze the content to answer this query."
            }
        },
        "required": ["url", "query"]
    }
}
```



### 2. Search Tool

```json
{
    "name": "search",
    "type": "function",
    "description": "Perform web search queries",
    "parameters": {
        "type": "object",
        "properties": {
            "queries": {
                "type": "array",
                "items": {
                    "type": "string"
                },
                "description": "List of search queries. Returns search results containing title, URL, and snippet for each query."
            }
        },
        "required": ["queries"]
    }
}
```


<!-- ## 📝 Citation

If you find our work useful, please consider citing:

```bibtex
@article{webexplorer2025,
  title={WebExplorer: Explore and Evolve for Training Long-Horizon Web Agents},
  author={Your Authors},
  journal={arXiv preprint},
  year={2025}
}
``` -->
