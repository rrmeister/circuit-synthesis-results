# Result data for _Exploring_ ab initio _machine synthesis of quantum circuits_
This repository collects the data produced for the paper _Exploring_ ab initio _machine synthesis of quantum circuits_ (arXiv:[2206.11245](https://arxiv.org/abs/2206.11245)).
The filenames are in the format

```<target>_<n>qb_<method>_<gateset>.json```

where `target` is the unitary we are trying to produce, `n` is the number of qubits of the target, `method` is either `tabu` for tabu search,
or `rand` for random search, and `gateset` is either `all-controlled` for controlled rotations with all-to-all connectivity, `nn-controlled`
for controlled rotations with only nearest-neighbour connectivity on a linear chain, or `swap` for local rotations plus a parametrised SWAP
gate between neighbouring qubits in a linear chain. There may be a self-explanatory comment in the filename after the gate set as well.

The structure of the JSON files is quite straightforward. There are some general parameters reiterating information from the filename, as well
as the maximum number of iterations used. The `runs` array contains all attempts at synthesising a circuit, each having the final `energy` of
the attempt, the number of `iterations`, the `time` as measured by the code itself, as well as the `walltime` calculated from SLURM logfiles
(these should be roughly identical for completed runs that exited normally), whether the run `finished` normally or was terminated by a
timeout, the number `n_gates` of gates in the final circuit, what the energy was througout each iteration (`energy_progression`), as well as
the final `circuit` the run produced, where each gate has target qubits and a rotation angle.
