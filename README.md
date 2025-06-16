# Empathy Contagion Network Simulation

A Python simulation framework for modeling the spread of empathy through social networks using graph theory and contagion dynamics.

## Overview

This project implements a sophisticated network-based model to simulate how empathy spreads through social structures. The simulation supports multiple network topologies and provides detailed analysis tools to understand empathy transmission patterns, network characteristics, and temporal dynamics.

## Features

- **Multiple Network Models**: Support for Erdős–Rényi, Barabási-Albert, and Watts-Strogatz network topologies
- **Configurable Contagion Parameters**: Customizable transmission rates, thresholds, and initial conditions
- **Dynamic Threshold Modeling**: Optional time-varying empathy thresholds
- **Comprehensive Visualization**: Network graphs, temporal plots, heatmaps, and statistical distributions
- **Network Analysis**: Clustering coefficients, path lengths, degree distributions, and structural metrics

## Requirements

```python
networkx>=2.8
numpy>=1.21.0
matplotlib>=3.5.0
seaborn>=0.11.0
scikit-learn>=1.0.0
scipy>=1.7.0
```

## Installation

```bash
pip install networkx numpy matplotlib seaborn scikit-learn scipy
```

## Quick Start

```python
import networkx as nx
import numpy as np
from empathy_simulation import create_network, spread_empathy

# Create a Barabási-Albert network
G = create_network("barabasi_albert")

# Initialize empathy states
empathy_state = {node: 0 for node in G.nodes()}
initial_nodes = np.random.choice(G.nodes(), size=5, replace=False)
for node in initial_nodes:
    empathy_state[node] = 1

# Run simulation
for t in range(50):
    empathy_state = spread_empathy(G, empathy_state, 
                                 transmission_rate=0.3, 
                                 threshold=2)
```

## Configuration Parameters

### Network Parameters
- `n_nodes`: Number of nodes in the network (default: 100)
- `p_edge`: Edge probability for Erdős–Rényi model (default: 0.1)
- `m`: Number of edges for Barabási-Albert model (default: 3)
- `k_neighbors`: Neighbors for Watts-Strogatz model (default: 4)
- `rewiring_prob`: Rewiring probability for Watts-Strogatz (default: 0.3)

### Empathy Contagion Parameters
- `transmission_rate`: Probability of empathy transmission (default: 0.3)
- `initial_empathy_percentage`: Initial empathetic nodes ratio (default: 0.05)
- `threshold`: Minimum empathetic neighbors for contagion (default: 2)
- `time_steps`: Simulation duration (default: 50)
- `dynamic_threshold`: Enable time-varying threshold (default: False)

## Network Models

### Erdős–Rényi Random Graph
Classical random network where each pair of nodes is connected with probability `p_edge`.

### Barabási-Albert Preferential Attachment
Scale-free network generated through preferential attachment, creating hub-like structures.

### Watts-Strogatz Small World
Regular lattice with random rewiring, balancing clustering and short path lengths.

## Visualization Features

- **Network Topology**: Node-link diagrams with empathy state coloring
- **Temporal Analysis**: Time series of empathy spread
- **Heatmaps**: Spatiotemporal empathy distribution
- **Degree Distribution**: Network connectivity patterns
- **Statistical Metrics**: Clustering and path length analysis

## Example Results

For a typical Barabási-Albert network (n=100, m=3):
- Average Clustering Coefficient: 0.1407
- Average Shortest Path Length: 2.6085
- Network Diameter: 5

## Applications

- Social psychology research
- Epidemiological modeling
- Information diffusion studies
- Network resilience analysis
- Community behavior prediction

## Contributing

1. Fork the repository
2. Create a feature branch
3. Implement changes with proper documentation
4. Add tests for new functionality
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Citation

If you use this simulation in your research, please cite:

```bibtex
@software{empathy_contagion_sim,
  title={Empathy Contagion Network Simulation},
  author={Bijay},
  year={2025},
  url={https://github.com/vijaybartaula/empathy-contagion-sim}
}
```

## Acknowledgments

Built using NetworkX, NumPy, Matplotlib, and the scientific Python ecosystem.
