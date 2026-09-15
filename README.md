# TeleQnA reproduction

This repository records my evaluation of GPT-3.5 Turbo and GPT-4 on the TeleQnA telecommunications benchmark. It is a reproduction of the benchmark experiment, not the original TeleQnA project.

## Results

The evaluation produced answers for 9,999 questions. The final item in the 10,000-question dataset was skipped by an off-by-one boundary in the original runner, so the reported values use 9,999 questions rather than silently presenting them as a complete 10,000-question run.

| Model | Correct | Accuracy |
| --- | ---: | ---: |
| GPT-3.5 Turbo | 6,653 / 9,999 | 66.54% |
| GPT-4 | 7,424 / 9,999 | 74.25% |

| Category | Questions | GPT-3.5 Turbo | GPT-4 |
| --- | ---: | ---: | ---: |
| Lexicon | 500 | 80.60% | 87.00% |
| Research overview | 2,000 | 68.10% | 74.10% |
| Research publications | 4,500 | 69.80% | 76.93% |
| Standards overview | 1,000 | 66.90% | 74.30% |
| Standards specifications | 1,999 | 53.93% | 65.13% |

The compact outcome files are in [`results/`](results/). They include the question ID, selected option, correctness flag, and category for every evaluated question. The full local outputs are not duplicated because they repeat the complete benchmark text.

## Run

Install the dependency, download the TeleQnA dataset from the original project, and expose the API key through the environment:

```bash
pip install -r requirements.txt
export OPENAI_API_KEY="..."
python run.py
```

The dataset itself is not duplicated here. `evaluation_tools.py` reads `OPENAI_API_KEY`; no API key is stored in this repository.

## Source and attribution

TeleQnA was introduced by Maatouk et al. in *TeleQnA: A Benchmark Dataset to Assess Large Language Models Telecommunications Knowledge*. The benchmark paper is available at [arXiv:2310.15051](https://arxiv.org/abs/2310.15051), and the original project is [netop-team/TeleQnA](https://github.com/netop-team/TeleQnA).

The evaluation code and license originate from that project. The per-question outcomes and measurements in this repository are from my reproduction runs.
