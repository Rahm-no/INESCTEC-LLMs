# INESCTEC-LLMs

## Model Parameter Tracing Process Cold/hot 

1. **Understanding Parameter Changes:**
   - Our work started by examining the frequency of changes for each model parameter.

2. **Optimization Profiling:**
   - We conducted profiling during the optimization step to analyze the frequency of changes for each parameter.

3. **Code for Parameter Tracing:**
   - The code used for this tracing can be found in [`Bert_from_scratch.ipynb`](/home/2023/rnouaj/llms-inesc/bert/Bert_from_scratch.ipynb).
     - Implemented an index mapping to track each model parameter.
     - Logged parameter frequency changes during the optimization step.

4. **Output Files:**
   - As a result, multiple runs generated `parameter_changes*.log` files capturing the changes.

## To understand Model layers dependency

We visualized the dependency using tensorboard SummaryWriter, the results are in  ['Bert_model_computation_graph.ipynb'](/home/2023/rnouaj/llms-inesc/bert/Bert_model_computation_graph.ipynb) and we did the same for GPT-2 and other models.

## Memory Profiling
For memory profiling, we worked with pytorch profiler that generates tensorboard for complete analysis. 
I followed this tutorial for complete memory profiling ['https://pytorch.org/blog/understanding-gpu-memory-1/]
The pickle file ['g0819.abci.local_Jun_19_20_03_26.pickle'](/home/2023/rnouaj/llms-inesc/gpt2-training/g0819.abci.local_Jun_19_20_03_26.pickle) is visualized using  https://pytorch.org/memory_viz, it is basically a memory snapshot.
The html file ['g0819.abci.local_Jun_19_20_16_36.html'] (/home/2023/rnouaj/llms-inesc/gpt2-training/g0819.abci.local_Jun_19_20_16_36.html) is a timeline for memory usage. 
The json files are visualized  using ['chrome://tracing/'].
We used also nvidia nsight tool for memory profiling which helps more to see  cuda execution and different function and system calls during forward backward optim step. The files are .qdrep, they are not in this repo because they are larger than 25MB. 
## Nvidia Nsight profiling for cuda mem calls and synchronization

Use the `nsys profile` command to start profiling. Wrap your Python training script with `nsys profile` as follows:
```bash
nsys profile -t cuda,nvtx python train_gpt2.py

      
`cuda` for CUDA API tracing and `nvtx` for NVIDIA Tools Extension (NVTX) API tracing, which provides additional annotations in the timeline. 

After the command completes, nsys will generate a report with a .qdrep file extension (e.g., report.qdrep). This file can be opened and analyzed using Nsight Systems GUI.



