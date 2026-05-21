# Human-Like Memory Systems

**Authors:** [Taewoon Kim](https://taewoon.kim/), [Michael Cochez](https://www.cochez.nl/), [Vincent Francois-Lavet](http://vincent.francois-l.be/), [Mark Neerincx](https://ocw.tudelft.nl/teachers/m_a_neerincx/), and [Piek Vossen](https://vossen.info/).

Code for heuristic agents with explicit episodic and semantic memory that operate in
[RoomEnv-v0](https://github.com/humemai/room-env).

For the research overview, see the
[project page](https://humem.ai/projects/human-like-memory-systems) or the paper on
[arXiv](https://arxiv.org/abs/2204.01611).

This README focuses on the code, setup, and handcrafted policies.

## Repository layout

- [`agent.py`](./agent.py): handcrafted agent policies with explicit memory
- [`train.py`](./train.py): runs experiments in RoomEnv-v0
- [`train.yaml`](./train.yaml): configuration for the experiment runs
- [`figures/`](./figures): generated plots and saved results
- [`test/`](./test): tests

## Prerequisites

1. Python 3.10 or higher
1. A virtual environment is recommended
1. Install the requirements with `pip install -r requirements.txt`

## Run experiments

```sh
python train.py
```

Configure the experiment in [`train.yaml`](./train.yaml). Generated figures are written
to [`figures/`](./figures).

## Handcrafted policies

The repository implements four main single-agent policies.

- **Handcrafted 1**: episodic memory only, forget the oldest item, answer from the
  latest relevant episodic memory
- **Handcrafted 2**: semantic memory only, forget the weakest item, answer from the
  strongest relevant semantic memory
- **Handcrafted 3**: episodic and semantic memory together, with compression from
  episodic experience into semantic memory
- **Handcrafted 4**: episodic memory plus pretrained semantic memory initialized with
  ConceptNet commonsense knowledge

All agents use the same total memory budget. The repository also includes multi-agent
variants that answer questions from combined memory.

## Results

|          Handcrafted 1           |          Handcrafted 2           |
| :------------------------------: | :------------------------------: |
| ![](./figures/episodic-1-v0.png) | ![](./figures/semantic-1-v0.png) |

|               Handcrafted 3               |                   Handcrafted 4                    |
| :---------------------------------------: | :------------------------------------------------: |
| ![](./figures/episodic_semantic-1-v0.png) | ![](./figures/episodic_semantic_pretrain-1-v0.png) |

| Total rewards with respect to different handcrafted policies and memory capacities. |
| :---------------------------------------------------------------------------------: |
|                       ![](./figures/best-strategies-1-v0.png)                       |

| Total rewards with respect to the number of agents. The lighter and narrower bars account for the single agent. |
| :-------------------------------------------------------------------------------------------------------------: |
|                                 ![](./figures/single-and-double-agents-v0.png)                                  |

## Further reading

- [Project page](https://humem.ai/projects/human-like-memory-systems)
- [Paper on arXiv](https://arxiv.org/abs/2204.01611)
- [RoomEnv-v0](https://github.com/humemai/room-env)

## Cite our paper

```bibtex
@misc{kim2026machinehumanlikememorysystems,
      title={A Machine With Human-Like Memory Systems},
      author={Taewoon Kim and Michael Cochez and Vincent Francois-Lavet and Mark Neerincx and Piek Vossen},
      year={2022},
      eprint={2204.01611},
      archivePrefix={arXiv},
      primaryClass={cs.AI},
      url={https://arxiv.org/abs/2204.01611},
}
```
