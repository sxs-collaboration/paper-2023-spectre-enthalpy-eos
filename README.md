Distributed under the MIT License.
See LICENSE.txt for details.

These input files are designed to be run on spectre version 2023.01.13,
available at
https://github.com/sxs-collaboration/spectre/releases/tag/v2023.01.13
and associated with doi
https://doi.org/10.5281/zenodo.7535144

The input files follow standard yaml syntax, and can
be read using utilities such as pyyaml (https://pyyaml.org/)

For further information about Options as specified in these files, see spectre
documentation at  https://spectre-code.org/

The equation of state information is encapsulated in the subsection of the file
`AnalyticSolution`, we intitialize the evolution via solving the TOV equations
with a particular central density, coordinates, and equation of state.
The equations of state we use are `PolytropicFluid` denoting a simple
polytrope, `Spectral`, denoting a spectral EoS, or `Enthalpy`, denoting
the enthalpy parametrization.  The enthalpy parametrization must additionally
be provided the low-density equation of state to be used.  For example, in the
file labeled `enthalpy-pt-mc-70.yaml` indicating a PT EoS being evolved
at ~70 meter finite-difference grid spacing, the EoS used is
`Enthalpy(Enthalpy(Enthalpy(Spectral)))` Indicating there are
3 enthalpy segments supplemented by a low density spectral EoS.

The parameters of the enthalpy parametrization are documented in the spectre
code, in the paper "Simulating neutron stars with a flexible enthalpy-based
equation of state parametrization in SpECTRE" certain variables are used to
denote certain parameters in the input file. See the paper for descriptions.
Note the variable k which sets the scale of trigonometric oscillations is
referred to as `TrigScaling` in the input file.  The variable referred to as
`TransitionDeltaEpsilon` is unused in any of the input files we provide,
and is not used in the paper. The low-density equation of state
is itself a parameter to the `Enthalpy` EoS, in the input file an
`Enthalpy` EoS with a low-density `Spectral` completion, will
have a field `Spectral`, which is the low-density spectral EoS

Note that all densities, `ReferenceDensity`, `MinimiumDensity`,
`ReferenceDensity`, and `MaximumDensity` are given in geometric
units, Msol^{-2}.

For a simple example of an input file with a polytropic
parametrization, see polytropic-polytrope-mc-130.yaml

For an example of a pure spectral EoS, see spectral-sly-mc-220.yaml
