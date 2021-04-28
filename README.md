# HCC Benchmarks
## Generic batch job for testing GPUs

```shell
#!/bin/bash
#SBATCH --time=01:00:00
#SBATCH --job-name=<gpu_type>_benchmark
#SBATCH --partition=gpu
#SBATCH --gres=gpu
#SBATCH --constraint=gpu_<gpu_type>
#SBATCH --ntasks=8
#SBATCH --output=<gpu_type>_benchmark.out
#SBATCH --error=<gpu_type>_benchmark.err

module load anaconda cuda
module load tensorflow-gpu/py38/2.4
pip install ai_benchmark
python -c \
'from ai_benchmark import AIBenchmark; benchmark = AIBenchmark(); results = benchmark.run()'
```
