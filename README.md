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

