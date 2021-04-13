# Synthetic Data Work

This repository is here to house synthetic data work.

The repo has two main components:

1. Synthea usage
2. Analysis

## Synthea Usage

The Synthea usage can be found in the Synthea folder. This folder is more or less a git clone of the main synthea branch located [here](https://github.com/synthetichealth/synthea) with README file intact and more. For more detailed information regarding Synthea specifically, please refer to their documentation and their **excellent** [WIKI](https://github.com/synthetichealth/synthea/wiki).

The main difference between this repository's "Synthea folder" and the Synthea source is that this repo contains a pre-compiled executable. These were built and run on MacOS so your mileage may vary based on OS.

However, you should be able to:

```bash
git clone https://github.com/UK-IPOP/synthetic.git
cd synthea

./run_synthea
```

and get results :)

If that fails, inside the synthea directory you can run:

```bash
./gradlew build check test
```

to build the executable. This will require [Java](https://www.java.com/en/) to be installed on your machine.

### Synthea Customization

As far as customizations to Synthea itself, we added the Opioid Use Disorder Module which can be found [here](synthea/src/main/resources/modules/prescribing_opioids_for_chronic_pain_and_treatment_of_oud.json).

We also edited some base Synthea configuration including the CSV append functionality which effectively means each new Synthea patient generated will have their data added to the running data list located inside the _output/csv_ folder.

Example commands that were run to generate the existing data inside the output/csv folder are:

```bash
./run_synthea
./run_synthea -p 100 -m opioid*
./run_synthea -p 100 -m opioid* Kentucky
```

## Analysis

This part of the project is still a work in progress but we hope to share the analysis we are doing on the data here in easy to read Jupyter Notebooks (using Python).

The only notebook that exists currently is a procedure to combine the various csv files that Synthea exports in an attempt to recreate a sample-synthetic PDMP table. The results of analysis are usually output into the data folder.

In the near future we hope to make it easier for developers/researchers to run these analyses on their own machines by providing requirements documents for the Python virtual environment.
