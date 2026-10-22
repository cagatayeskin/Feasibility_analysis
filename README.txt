Feasibility as a moving target

Code for the article "Feasibility as a moving target: Fluctuating species interactions lead to universal power law in equilibrium abundances" by Cagatay Eskin, Vu Nguyen and Dervis Can Vural.

All analyses are Jupyter notebooks written in Python 3.


CONTENTS

equilibrium_abundance_pdf/equilibrium_pdf.ipynb
    Probability distribution of the equilibrium abundances, its Gaussian approximation, the power law tails, the contour maps of the two species system and the critical noise levels. The system used for the critical noise levels is read from parameters.txt in the same folder.

empirical_abundance_tails/abundance_tail_analysis.ipynb
    Power law fits, goodness of fit tests and model comparisons for the lake and mesocosm time series, and the combined figure.

feasibility_loss_analysis_empirical_nets/parametrize_analyze_nets.ipynb
    Parameterizes the empirical networks, simulates them until feasibility is lost and compares the results with the escape rate predictions.


REQUIREMENTS

numpy, scipy, pandas, matplotlib, statsmodels, joblib, threadpoolctl, kneed, networkx and pygraphviz. pygraphviz is only needed to draw the network diagram.


DATA

The empirical data are not included in this repository. They can be downloaded from the original sources and placed in the folders below with the given file names.

1. Lake data: BioTIME database, dataset 638 (Carpenter and Pace 2018), https://biotime.st-andrews.ac.uk. Keep only the rows of Paul Lake (latitude 46.2512, longitude -89.5034) and save them as empirical_abundance_tails/raw_data_638.csv with the columns ABUNDANCE, BIOMAS, valid_name, SAMPLE_DESC, LATITUDE, LONGITUDE, DAY, MONTH, YEAR.

2. Mesocosm data: Benincà et al. 2008, Chaos in a long-term experiment with a plankton community, Nature 451, 822 to 825, https://doi.org/10.1038/nature06512. Save the original time series in Supplementary Information (Appendix S1, worksheet 1) as empirical_abundance_tails/species_abundances_original.csv.

3. Ecological networks: Web of Life database, https://www.web-of-life.es. Download all networks as binary data in csv format, without species names (105 networks in August 2025), into feasibility_loss_analysis_empirical_nets/web-of-life_2025/. We removed the three largest and plant-herbivore networks. The remaining 98 networks are 82 mutualistic networks (M_), 16 food webs (FW_).


RUNNING THE ANALYSES

The notebooks equilibrium_pdf.ipynb and abundance_tail_analysis.ipynb run from top to bottom and save their figures next to the notebook.

parametrize_analyze_nets.ipynb also runs from top to bottom. It first parameterizes the networks and saves them in parameterized_networks_M/ and parameterized_networks_FW/. The simulation cell then calibrates the noise level of each network, runs the simulations and writes the results to results_M/ and results_FW/.
