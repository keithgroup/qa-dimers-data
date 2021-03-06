# Quantum alchemy data - Dimers

All PySCF calculation logs and JSON files for the dimer study of quantum alchemy.
A cumulative JSON file is provided with all files organized by atom and state (i.e., charge and multiplicity).

## Data generation

A [generator Python script](https://github.com/keithgroup/qa-atoms-dimers/blob/main/scripts/pyscf-calc-generator/generate-pyscf.qa-calculations.py) is used with dictionary of all desired calculations.
For more information, visit the [keithgroup/qa-atoms-dimers](https://github.com/keithgroup/qa-atoms-dimers) repository.

## JSON data

JSONs contain the following information.

- `"schema_name"`: Name of the JSON format.
- `"provenance"`: Origin of the JSON data.
    - `"creator"`: Name of the originating software.
    - `"version"`: Version of the originating software.
- `"molecule`": Information about the atoms making up the system.
    - `"geometry"`: Cartesian coordinates of all atoms in the system.
    - `"symbols"`: All chemical symbols in the system in the same order as in the `"geometry"`.
- `"molecular_charge"`: Total system charge.
- `"molecular_multiplicity"`: Multiplicity of the system, 2S + 1.
- `"name"`: Unique name specifying the calculation.
- `"atomic_numbers"`: List of atomic numbers of all atoms in the system in the same order as `"geometry"`.
- `"n_electrons"`: Total number of electrons in the system.
- `"model"`: Methods used to calculation system properties.
    - `"method"`: Overall quantum chemical method used.
    - `"basis"`: Employed basis set.
    - `"scf_conv_tol"`: Change in electronic energy SCF convergence criteria.
    - `"scf_conv_tol_grad"`: Norm of the gradient convergence criteria.
    - `"cc_conv_tol"`: Change in coupled cluster electronic energy convergence criteria.
    - `"cc_conv_tol_normt"`: Norm of the coupled cluster amplitude vectors convergence criteria.
- `"broken_symmetry"`: If start with an excited state guess.
- `"finite_diff_delta"`: $h$ used for central finite differences.
- `"finite_diff_acc"`: General accuracy for central finite difference.
- `"qa_lambdas"`: List of all calculations and their change in nuclear charge.
- `"electronic_energies"`: Total electronic energies of the systems.
- `"qats_energies"`: Predicted total electron energies with a Taylor series of nth order.
- `"qats_poly_coeffs"`: Taylor series polynomial coefficients (derivatives are from finite differences).
- `"hf_energies"`: Hartree&ndash;Fock energy contributions (if we are using coupled cluster).
- `"triples_corrections"`: Perturbative triple corrections (if selected).
- `"scf_converged"`: If the SCF iterations have converged.
- `"cc_converged"`: If the coupled cluster iterations have converged.
- `"scf_spin_squared"`: Spin squared expectation value of the last SCF iteration, S(S + 1).
- `"cc_spin_squared"`: Spin squared expectation value of the last coupled cluster iteration, S(S + 1).
- `"t1_diagnostic"`: T1 diagnostic for coupled cluster calculations.

<details>
<summary>Here is an example of a typical JSON file for a restricted CCSD(T) calculation.</summary>

```json
{
    "schema_name": "pyscf_qa_output",
    "provenance": {
        "creator": "PySCF",
        "version": "1.7.6"
    },
    "molecule": {
        "geometry": [[0.0, 0.0, 0.0], [1.0, 0.0, 0.0]],
        "symbols": [ "C", "H" ]
    },
    "molecular_charge": 1,
    "molecular_multiplicity": 1,
    "name": "c.h.chrg1.mult1.sep1.00-pyscf-ccsdt.ccpv5z",
    "atomic_numbers": [ 6, 1 ],
    "n_electrons": 6,
    "model": {
        "method": "CCSD(T)",
        "basis": "cc-pV5Z",
        "scf_conv_tol": 1e-09,
        "scf_conv_tol_grad": 1e-06,
        "cc_conv_tol": 1e-05,
        "cc_conv_tol_normt": 1e-07
    },
    "broken_symmetry": false,
    "finite_diff_delta": 0.01,
    "finite_diff_acc": 2,
    "qa_lambdas": [-2.0, -1.75, -1.5, -1.25, -1.0, -0.75, -0.5, -0.25, -0.02, -0.01, 0.0, 0.01, 0.02, 0.25, 0.5, 0.75, 1.0],
    "electronic_energies": [-15.168011627351744, -17.437652214354884, -19.871649392713696, -22.472909760910394, -25.243713749492237, -28.185775141987605, -31.30046405063705, -34.589032292721846, -37.769158718628724, -37.91080265134425, -38.0527287122824, -38.194936980292034, -38.33742753403346, -41.69279835543476, -45.51040751530531, -49.50653347347145, -53.681841227320525],
    "qats_energies": {
        "0": [-38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445, -38.052728712282445],
        "1": [-9.639295817503822, -13.19097492935115, -16.742654041198477, -20.294333153045805, -23.846012264893133, -27.39769137674046, -30.94937048858779, -34.50104960043512, -37.76859438333466, -37.91066154780855, -38.052728712282445, -38.19479587675634, -38.33686304123023, -41.60440782412977, -45.1560869359771, -48.70776604782443, -52.259445159671756],
        "2": [-15.283437245369, -17.512270710060427, -19.91748359437264, -22.49907589830564, -25.257047621859428, -28.191398765034002, -31.302129327829363, -34.58923931024551, -37.769158797477445, -37.91080265134425, -38.052728712282445, -38.194936980292034, -38.33742745537302, -41.692597533940166, -45.508845775218674, -49.50147343611797, -53.67048051663805],
        "3": [-15.178431136671875, -17.441924820835595, -19.87318414226604, -22.473439641299507, -25.243921858272287, -28.185861333520677, -31.30048860738097, -34.58903422018946, -37.769158692471336, -37.910802638218485, -38.052728712282445, -38.1949369934178, -38.337427560379126, -41.692802623996215, -45.51048649566707, -49.507010867631294, -53.68360628022519],
        "4": [-15.165878215006781, -17.434566528619314, -19.869212319395444, -22.47152421746145, -25.243137300668216, -28.185613094591265, -31.300439572530717, -34.58903115551132, -37.769158692345805, -37.91080263821064, -38.052728712282445, -38.194936993409954, -38.337427560253595, -41.692799559318075, -45.51043746081681, -49.50676262870188, -53.68282172262112]
    },
    "qats_poly_coeffs": [ -38.052728712282445, -14.206716447389311, -1.4110353569662948, -0.01312576358714068, 0.000784557604068444 ],
    "hf_energies": [-15.039397542797753, -17.306196946924697, -19.737151429446005, -22.33531689869329, -25.10306490226627, -28.042151890664666, -31.153962053106543, -34.43975796926096, -37.61745025305918, -37.758991404930605, -37.90081496635595, -38.04292101965761, -38.18530964699626, -41.53842403217207, -45.353806396989455, -49.34798452680033, -53.5216388132588],
    "triples_corrections": [-0.0023661770818066406, -0.002436591869254029, -0.0025221436893826266, -0.0026078797235260425, -0.0026825528418877014, -0.00274280659433309, -0.002790309777751178, -0.0028274750394940026, -0.0028536473448671044, -0.0028546165697939012, -0.0028555718050823236, -0.002856513055472478, -0.002857440325737153, -0.002874928905159725, -0.0028858628597366407, -0.002889514215818352, -0.002888325121872548],
    "scf_converged": [true, true, true, true, true, true, true, true, true, true, true, true, true, true, true, true, true],
    "cc_converged": [true, true, true, true, true, true, true, true, true, true, true, true, true, true, true, true, true],
    "t1_diagnostic": [0.018119050921357415, 0.015978960043895925, 0.014191612668712038, 0.012705161238841719, 0.011449031767649684, 0.01039494390889384, 0.009528368157857136, 0.00881696695589493, 0.00826086273579403, 0.008238268808428295, 0.008215785680011089, 0.008193410988157634, 0.00817114240042732, 0.007683329542885144, 0.007188483963259352, 0.006709734936384963, 0.006233299357290182]
}
```

</details>

## Naming convention

Each file is named following this convention: `<structure>-<calculation>-<options>`.
Information within each `<>` block is generally separated by a period; this minimizes the width of the file name.
Lowercase is always used to speed up navigation with a terminal.

- `<structure>`: A human-readable, unique label for the structure involved.
    It should also specify refinements (i.e., optimizations) to represent a breadcrumb trail.
    <br><br>
    **Example**

    The excited state for a Nitrogen atom with a charge of $-1$ would be labeled as `n.chrg-1.mult1`, whereas the ground state would be `n.chrg-1.mult3`.
    Neutral systems are still explicitly defined; for example, the ground state of a neutral Argon atom would be `ar.chrg0.mult1`.

- `<calculation>`: Specification of the program and calculation type for output files.
    Restarts should be specified by appending a `r`.
    <br><br>
    **Example**

    Every calculation is labeled as a `pyscf.qa` calculation as the driver Python script performs several PySCF calculations and calculates data for quantum alchemy.

- `<options>`: Calculation specifications or parameters.
    <br><br>
    **Example**

    Only the quantum chemical method and basis set are specified.
    Non-alphanumeric are dropped; for example, a CCSD(T)/aug-cc-pV5Z calculation would be `ccsdt.augccpv5z`.
    In these data, all coupled cluster triples corrections are perturbative.
    In the directory names, the `u` (for unrestricted) is typically dropped, but included in the file names.

## Citation

If you use this dataset, please cite the corresponding [manuscript](https://doi.org/10.26434/chemrxiv-2021-pt5gd) in addition to this repository as specified in `CITATION.cff`.

## License

[![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
