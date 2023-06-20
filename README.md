# Selection Choice Encoding

This repository contains code with algorithms for encoding system architecture selection choices:
discrete choices (e.g. between different material types or fuel types) that influence each other.
It is useful in the context of system architecture optimization, where some model of the architecture design space
is created and automatically searched (optimized) to find the best architecture instance.

For more background on architecture optimization and modeling architecture design spaces, see:
[System Architecture Design Space Exploration: An Approach to Modeling and Optimization](https://www.zenodo.org/record/4672182)

An encoder is instantiated and queried for a given encoding scenario, specified by:
- A list of nodes, representing elements of the architecture (design space)
- A list of choice nodes mapping to mutually-exclusive option nodes
- An influence matrix
- A choice constraint map

The *influence matrix* is an `n_nodes x n_nodes` matrix, specifying for each node their status and influence:
- On the diagonal, the initial node status is defined
- On the off-diagonal, the influence of node `i` on node `j` is defined

| Status code | Diagonal             | Off-diagonal              |
|-------------|----------------------|---------------------------|
| 0           | Not selected         | No influence              |
| 1           | Selected/included    | Node `i` selects node `j` |
| 2           | Removed              | Node `i` removes node `j` |
| 3           | Invalid architecture |                           |
| 4           | Choice made          |                           |

The *choice constraint map* (optional) defines for each choice-option pair which other choice-option pairs are removed.
This is used for modeling choice linking and other constraints.

## Installation

Clone the repository and:
```
pip install -e .
```

## Contributing

The project is coordinated by: Jasper Bussemaker (*jasper.bussemaker at dlr.de*)

If you find a bug or have a feature request, please file an issue using the Github issue tracker.
If you require support for using SelectionChoiceEncoding or want to collaborate, feel free to contact me.

Contributions are appreciated:
- Fork the repository
- Add your contributions to the fork
  - Update/add documentation
  - Add tests and make sure they pass (tests are run using `pytest`)
- Read and sign the [Contributor License Agreement (CLA)](SelectionChoiceEncoding%20DLR%20Individual%20Contributor%20License%20Agreement.docx)
  , and send it to the project coordinator
- Issue a pull request
