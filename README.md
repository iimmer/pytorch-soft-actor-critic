### Description
------------
Reimplementation of [Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement
Learning with a Stochastic Actor](https://arxiv.org/pdf/1801.01290.pdf).


### Requirements
------------

- [mujoco-py](https://github.com/openai/mujoco-py)
- [TensorboardX](https://github.com/lanpa/tensorboardX)
- [PyTorch](http://pytorch.org/)

### Run
------------

#### For SAC :

```
python main.py --env-name Humanoid-v2 --alpha 0.025 
```

#### For SAC (Hard Update):

```
python main.py --env-name Humanoid-v2 --alpha 0.025 --tau 1 --target_update_interval 1000
```

#### For SAC (Deterministic, Hard Update):

```
python main.py --env-name Humanoid-v2 --policy Deterministic --tau 1 --target_update_interval 1000
```

### Parameters
-------------


| Parameters     | Value  |
| --------------- | ------------- |
|**Shared**|-|
| optimizer | Adam |
| learning rate(`--lr`)  | 1x10<sup>−3</sup> |
| discount(`--gamma`) (γ) | 0.99 |
| replay buffer size(`--replay_size`) | 1x10<sup>6</sup> |
|number of hidden layers (all networks)|2|
|number of hidden units per layer(`--hidden_size`)|256|
|number of samples per minibatch(`--batch_size`)|256|
|nonlinearity|ReLU|
|**SAC**|-|
|target smoothing coefficient(`--tau`) (τ)|0.005|
|target update interval(`--target_update_interval`)|1|
|gradient steps(`--updates_per_step`)|1|
|**SAC** *(Hard Update)*|-|
|target smoothing coefficient(`--tau`) (τ)|1|
|target update interval(`--target_update_interval`)|1000|
|gradient steps (except humanoids)(`--updates_per_step`)|4|
|gradient steps (humanoids)(`--updates_per_step`)|1|




| Environment **(`--env-name`)**| Temperature **(`--alpha`)**|
| --------------- | ------------- |
| HalfCheetah-v2  | 0.1 |
| Hopper-v2       | 0.1 |
| Walker2d-v2     | 0.1 |
| Ant-v2          | 0.1 |
| Humanoid-v2     | 0.025 |
