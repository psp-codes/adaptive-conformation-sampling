# Adaptive Conformation Sampling
This repository contains codes for the project detailed in the manuscript titled "Adaptive Stochastic Optimization to Improve Protein Conformation Sampling". The manuscript is currently under review and the link to the manuscript will be provided once published.

* Authors of the paper: Ahmed Bin Zaman, Toki Tahmid Inan, Kenneth De Jong, Amarda Shehu.
* The dataset for the codes can be found in, 
* The external libraries that the codes use are PyRosetta and NumPy.

## Code Files
### /modules/io.py
This module contains the input/output utility functions needed for the project. It contains the following functions.
* get_sequence_from_fasta: This function returns the amino-acid sequence of a protein from its fasta file.
  * Arguments:
    * fasta_file: A string containing the fasta file path.
  * Returns: A string containing the amino-acid sequence of the protein.

### /modules/population.py
This module provides methods for generating initial population of conformations as well as a variation operator to modify a conformation. It contains the following methods.

* monte_carlo_single: Performs Metropolis Monte Carlo (MMC) search with a specified move, a fixed number of times in a single trajectory. Metropolis criteria temperature is increased by a specific value if a specific number of consecutive moves fail.
  * Arguments:
    * pose: A pyrosetta Pose object representing initial conformation
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * successive_failures: A positive int indicating the threshold for consecutive number of failed moves before temperature increase.
    * temperature_increment: An int indicating the increase in temperature if a number of moves fail.
    * fixed_moves: A positive int indicating the number of moves in the search.
  * Returns: A pyrosetta Pose object containing the final conformation.

* monte_carlo_fixed: Performs Metropolis Monte Carlo (MMC) search with a specified move, a fixed number of times in different trajectories. Each trajectory is created by performing moves from the initial conformation passed in the argument.
  * Arguments:
    * pose: A pyrosetta Pose object representing initial conformation
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * trajectory: An integer indicating the number of trajectories.
    * fixed_moves: An integer indicating the number of moves in each trajectory.
  * Returns: A list containing the population generated by the MMC search.

* monte_carlo_failure: Performs Metropolis Monte Carlo (MMC) search starting with an initial population as different trajectories. The search in each trajectory terminates when a specific number of consecutive moves fail.
  * Arguments:
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * population_base: A list containing the initial population.
    * successive_failures: A positive integer indicating the threshold for consecutive number of failed moves in each trajectory.
  * Returns: A list containing the population generated by the MMC search.
  
* mutation_operator: Constructs a mutation operator to perform Molecular Fragment Replacements. The operator is a pyrosetta Mover, which can be used to introduce mutation on a population or a conformation.
  * Arguments:
    * fragment_length: An integer indicating the fragment length.
    * fragment_file: A string defining the path of the file containing the fragments.
  * Returns: A pyrosetta ClassicFragmentMover object that defines each move to be a Molecular Fragment Replacement.


### /modules/population_meta.py
This module provides methods for generating initial population of conformations as well as a variation operator to modify a conformation. The bookkeeping is for metamorphic proteins with two known native conformations. It contains the following methods.

* monte_carlo_single: Performs Metropolis Monte Carlo (MMC) search with a specified move, a fixed number of times in a single trajectory. Metropolis criteria temperature is increased by a specific value if a specific number of consecutive moves fail.
  * Arguments:
    * pose: A pyrosetta Pose object representing initial conformation
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * successive_failures: A positive int indicating the threshold for consecutive number of failed moves before temperature increase.
    * temperature_increment: An int indicating the increase in temperature if a number of moves fail.
    * fixed_moves: A positive int indicating the number of moves in the search.
  * Returns: A pyrosetta Pose object containing the final conformation.

* monte_carlo_fixed: Performs Metropolis Monte Carlo (MMC) search with a specified move, a fixed number of times in different trajectories. Each trajectory is created by performing moves from the initial conformation passed in the argument.
  * Arguments:
    * pose: A pyrosetta Pose object representing initial conformation
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * trajectory: An integer indicating the number of trajectories.
    * fixed_moves: An integer indicating the number of moves in each trajectory.
  * Returns: A list containing the population generated by the MMC search.

* monte_carlo_failure: Performs Metropolis Monte Carlo (MMC) search starting with an initial population as different trajectories. The search in each trajectory terminates when a specific number of consecutive moves fail.
  * Arguments:
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * population_base: A list containing the initial population.
    * successive_failures: A positive integer indicating the threshold for consecutive number of failed moves in each trajectory.
  * Returns: A list containing the population generated by the MMC search.
  
* mutation_operator: Constructs a mutation operator to perform Molecular Fragment Replacements. The operator is a pyrosetta Mover, which can be used to introduce mutation on a population or a conformation.
  * Arguments:
    * fragment_length: An integer indicating the fragment length.
    * fragment_file: A string defining the path of the file containing the fragments.
  * Returns: A pyrosetta ClassicFragmentMover object that defines each move to be a Molecular Fragment Replacement.

### /modules/population_meta_4.py
This module provides methods for generating initial population of conformations as well as a variation operator to modify a conformation. The bookkeeping is for metamorphic proteins with four known native conformations. It contains the following methods.

* monte_carlo_single: Performs Metropolis Monte Carlo (MMC) search with a specified move, a fixed number of times in a single trajectory. Metropolis criteria temperature is increased by a specific value if a specific number of consecutive moves fail.
  * Arguments:
    * pose: A pyrosetta Pose object representing initial conformation
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * successive_failures: A positive int indicating the threshold for consecutive number of failed moves before temperature increase.
    * temperature_increment: An int indicating the increase in temperature if a number of moves fail.
    * fixed_moves: A positive int indicating the number of moves in the search.
  * Returns: A pyrosetta Pose object containing the final conformation.

* monte_carlo_fixed: Performs Metropolis Monte Carlo (MMC) search with a specified move, a fixed number of times in different trajectories. Each trajectory is created by performing moves from the initial conformation passed in the argument.
  * Arguments:
    * pose: A pyrosetta Pose object representing initial conformation
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * trajectory: An integer indicating the number of trajectories.
    * fixed_moves: An integer indicating the number of moves in each trajectory.
  * Returns: A list containing the population generated by the MMC search.

* monte_carlo_failure: Performs Metropolis Monte Carlo (MMC) search starting with an initial population as different trajectories. The search in each trajectory terminates when a specific number of consecutive moves fail.
  * Arguments:
    * mover: A pyrosetta Mover object derermining the moves in MMC search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * temperature: An integer/float defining the temperature of MMC search.
    * population_base: A list containing the initial population.
    * successive_failures: A positive integer indicating the threshold for consecutive number of failed moves in each trajectory.
  * Returns: A list containing the population generated by the MMC search.
  
* mutation_operator: Constructs a mutation operator to perform Molecular Fragment Replacements. The operator is a pyrosetta Mover, which can be used to introduce mutation on a population or a conformation.
  * Arguments:
    * fragment_length: An integer indicating the fragment length.
    * fragment_file: A string defining the path of the file containing the fragments.
  * Returns: A pyrosetta ClassicFragmentMover object that defines each move to be a Molecular Fragment Replacement.
  
### /modules/improvement.py
This module provides a method that performs local search to improve the current fitness of a given conformation. It contains the following method.
* local_search: This function Performs greedy local search to improve fitness of a conformation. The local search performs specific moves to map a conformation to a nearby local minimum in the energy surface. The search is terminated when a specific number of moves fail to improve the score based on a specific fitness function.
  * Arguments:
    * pose: A pyrosetta Pose object representing a conformation.
    * mover: A pyrosetta Mover object that determines the moves in the local search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * successive_failures: An integer indicating the threshold for consecutive number of failed moves in each trajectory.
  * Returns: A pyrosetta Pose object containing the conformation with locally minimum fitness.

### /modules/improvement_meta.py
This module provides a method that performs local search to improve the current fitness of a given conformation. The bookkeeping is for metamorphic proteins with two native conformations. It contains the following method.
* local_search: This function Performs greedy local search to improve fitness of a conformation. The local search performs specific moves to map a conformation to a nearby local minimum in the energy surface. The search is terminated when a specific number of moves fail to improve the score based on a specific fitness function.
  * Arguments:
    * pose: A pyrosetta Pose object representing a conformation.
    * mover: A pyrosetta Mover object that determines the moves in the local search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * successive_failures: An integer indicating the threshold for consecutive number of failed moves in each trajectory.
  * Returns: A pyrosetta Pose object containing the conformation with locally minimum fitness.

### /modules/improvement_meta_4.py
This module provides a method that performs local search to improve the current fitness of a given conformation. The bookkeeping is for metamorphic proteins with four native conformations. It contains the following method.
* local_search: This function Performs greedy local search to improve fitness of a conformation. The local search performs specific moves to map a conformation to a nearby local minimum in the energy surface. The search is terminated when a specific number of moves fail to improve the score based on a specific fitness function.
  * Arguments:
    * pose: A pyrosetta Pose object representing a conformation.
    * mover: A pyrosetta Mover object that determines the moves in the local search.
    * score_function: A pyrosetta ScoreFunction object for scoring each move.
    * successive_failures: An integer indicating the threshold for consecutive number of failed moves in each trajectory.
  * Returns: A pyrosetta Pose object containing the conformation with locally minimum fitness.

### /modules/selection.py
This module provides functions to select next generation from current generation of individuals. It contains the following functions.
* truncation: This function implements truncation selection while ensuring elitism to select a specific number of members for the next generation.
  * Arguments:
    * parent_population: A list containing members of parent population.
    * child_population: A list containing members of offspring population.
    * parents_scores: A list containing scores of each member of the parent population. The format is: [member 1 score, member 2 score, ....]. The order of members has to be consistent with parent_population argument.
    * children_scores: A list containing scores of each member of the offspring population. The format is: [member 1 score, member 2 score, ....]. The order of members has to be consistent with child_population argument.
    * elitism_rate: A float between 0 and 1 indicating the elitism percentage.
  * Returns: A list of members for the next generation of population.

* fitness_proportional: This function implements fitness proportional selection to select a specific number of members for the next generation.
  * Arguments:
    * population: A list containing members of current population with parents and children combined.
    * scores: A list containing scores of each member of the population. The format is: [member 1 score, member 2 score, ....]. The order of members has to be consistent with population argument.
    * next_gen_number: An int indicating the number of members to be selected for the next generation.
    * random_seed: An int indicating the seed of the random number generator.
  * Returns: A list of members for the next generation of population.

* quaternary_tournament: This function implements quaternary tournament selection to select a specific number of members for the next generation.
  * Arguments:
    * population: A list containing members of current population with parents and children combined.
    * scores: A list containing scores of each member of the population. The format is: [member 1 score, member 2 score, ....]. The order of members has to be consistent with population argument.
    * next_gen_number: An int indicating the number of members to be selected for the next generation.
    * random_seed: An int indicating the seed of the random number generator.
  * Returns: A list of members for the next generation of population.

* uniform_stochastic: This function implements uniform stochastic selection to select a specific number of members for the next generation.
  * Arguments:
    * population: A list containing members of current population with parents and children combined.
    * next_gen_number: An int indicating the number of members to be selected for the next generation.
    * random_seed: An int indicating the seed of the random number generator.
  * Returns: A list of members for the next generation of population.

### /modules/tribal_competition.py
This module provides functions to perform competition between different subpopulations. It contains the following functions.
* free_energy_competition: This function implements free energy subpopulation competition via increasing the size of the best subpopulation by replicating the best solution in that subpopulation once, decreasing the size of the worst subpopulation by discarding the worst solution in that subpopulation, and utilizing free energy fitness of the subpopulations for the competition. The lower the fitness score, the better the subpopulation.
  * Arguments:
    * tribes: A 2D list containing the subpopulations. The format is: [ [subpopulation 1 member 1, subpopulation 1 member 2,....], [subpopulation 2 member 1, subpopulation 2 member 2,....], .... ].
    * member_fitness: A 2D list containing fitness scores of each member of the subpopulationa. The format is: [ [subpopulation 1 member 1 score, subpopulation 1 member 2 score,..], [subpopulation 2 member 1 score, subpopulation 2 member 2 score,..], .... ]. The order of subpopulations has to be consistent with tribes argument.
    * temperature: A float containing the temperature for free energy calculation.
  * Returns: A 2D list of subpopulations as a result of the competition. The format is: [ [subpopulation 1 member 1, subpopulation 1 member 2,....], [subpopulation 2 member 1, subpopulation 2 member 2,....], .... ].

* avg_tribe_fitness: This function implements a fitness function based on the average score for evaluating a subpopulation.
  * Arguments:
    * tribe_scores: A list containing fitness scores of each member of the subpopulation. The format is: [member 1 score, member 2 score, ....].
  * Returns: A float containing the fitness score for the given subpopulation.

* free_energy_fitness: This function implements a fitness function based on the free energy score for evaluating a subpopulation.
  * Arguments:
    * tribe_scores: A list containing fitness scores of each member of the subpopulation. The format is: [member 1 score, member 2 score, ....].
    * temperature: A float containing the temperature for free energy calculation.
  * Returns: A float containing the fitness score for the given subpopulation.

### /modules/tribal_utility.py
This module provides a function needed for subpopulation EAs. It contains the following function.
* leader_clustering: This function implements leader clustering in order to divide the members into subpopulationa. Each member who are within a certain distance from another member are clustered together.
  * Arguments:
    * population: A list containing the population.
    * distance: An int indicating the distance cutoff.
  * Returns: A 2D list of subpopulations as a result of the clustering. The format is: [ [subpopulation 1 member 1, subpopulation 1 member 2,....], [subpopulation 2 member 1, subpopulation 2 member 2,....], .... ].

### hea_ad.py
Generates conformations for an amino-acid sequence using HEA-AD conformation sampling algorithm.

__Output:__ The output is two .txt files and two .pdb files explained below.

* hea_ad_coordinates.txt: Contains Cα coordinates for each generated conformation.
* hea_ad_.txt: Contains three columns and each row represents one generated conformation. The first column provides the lRMSD to the Target 1 (a known native conformation) for the generated conformation, the second column provides the lRMSD to the Target 2 (another known native conformation) for the generated conformation and the third column provides the Rosetta score4 energy for the generated conformation.
* hea_ad_rmsd1.pdb: Contains coordinates for the lowest lRMSD conformation to the Target 1.
* hea_ad_rmsd2.pdb: Contains coordinates for the lowest lRMSD conformation to the Target 2.

__Input:__ Uses /configs/hea_ad.ini file for inputs. The inputs represented by key-value pairs in the /configs/hea_ad.ini file are explained below for each key.

* Section [init]
  * fastaPath: a string indicating the path to the .fasta file containing the amino-acid sequence of the protein.
  * pdb1Path: a string indicating the path to the .pdb file containing the coordinates for the Target 1 native conformation.
  * pdb2Path: a string indicating the path to the .pdb file containing the coordinates for the Target 2 native conformation.
  * population: an integer indicating the population size.
  * evalbudget: an integer indicating the evaluation budget.

* Section [initPopulation]
  * stage1moves: an integer indicating the number of moves for the stage 1 of the initial population generation.
  * stage1score: a string indicating the name of the Rosetta energy function to use for the stage 1 of the initial population generation.
  * stage2successiveFailures: an integer indicating the number of successive failures for the stage 2 of the initial population generation.
  * stage2score: a string indicating the name of the Rosetta energy function to use for the stage 2 of the initial population generation.
  * fragmentLength: an integer indicating the length of the fragments to be used for the initial population generation.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the initial population generation.
  * stage1temperature: an integer indicating the temperature for the MMC search in the stage 1 of the initial population generation.
  * stage2temperature: an integer indicating the temperature for the MMC search in the stage 2 of the initial population generation.

* Section [improvement]
  * score: a string indicating the name of the Rosetta energy function to use for the improvement operator.
  * fragmentLength: an integer indicating the length of the fragments to be used for the improvement operator.
  * successiveFailures: an integer indicating the number of successive failures for the improvement operator.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the improvement operator.

* Section [selection]
  * elitismRate: a float between 0 and 1 indicating the elitism rate for the truncation selection operator.
  
* Section [output]
  * filePrefix: a string indicating the path to the directory to save the output files.

### hea_tr.py
Generates conformations for an amino-acid sequence using HEA-TR conformation sampling algorithm.

__Output:__ The output is two .txt files and one .pdb files explained below.

* hea_tr_coordinates.txt: Contains Cα coordinates for each generated conformation.
* hea_tr_.txt: Contains two columns and each row represents one generated conformation. The first column provides the lRMSD to the known native conformation for the generated conformation and the second column provides the Rosetta score4 energy for the generated conformation.
* hea_tr_rmsd.pdb: Contains coordinates for the lowest lRMSD conformation to the known native conformation.

__Input:__ Uses /configs/hea_tr.ini file for inputs. The inputs represented by key-value pairs in the /configs/hea_tr.ini file are explained below for each key.

* Section [init]
  * fastaPath: a string indicating the path to the .fasta file containing the amino-acid sequence of the protein.
  * pdbPath: a string indicating the path to the .pdb file containing the coordinates for the known native conformation.
  * population: an integer indicating the population size.
  * evalbudget: an integer indicating the evaluation budget.

* Section [initPopulation]
  * stage1moves: an integer indicating the number of moves for the stage 1 of the initial population generation.
  * stage1score: a string indicating the name of the Rosetta energy function to use for the stage 1 of the initial population generation.
  * stage2successiveFailures: an integer indicating the number of successive failures for the stage 2 of the initial population generation.
  * stage2score: a string indicating the name of the Rosetta energy function to use for the stage 2 of the initial population generation.
  * fragmentLength: an integer indicating the length of the fragments to be used for the initial population generation.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the initial population generation.
  * stage1temperature: an integer indicating the temperature for the MMC search in the stage 1 of the initial population generation.
  * stage2temperature: an integer indicating the temperature for the MMC search in the stage 2 of the initial population generation.

* Section [improvement]
  * score: a string indicating the name of the Rosetta energy function to use for the improvement operator.
  * fragmentLength: an integer indicating the length of the fragments to be used for the improvement operator.
  * successiveFailures: an integer indicating the number of successive failures for the improvement operator.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the improvement operator.

* Section [selection]
  * elitismRate: a float between 0 and 1 indicating the elitism rate for the truncation selection operator.
  
* Section [output]
  * filePrefix: a string indicating the path to the directory to save the output files.

### hea_us.py
Generates conformations for an amino-acid sequence using HEA-US conformation sampling algorithm.

__Output:__ The output is two .txt files and one .pdb files explained below.

* hea_us_coordinates.txt: Contains Cα coordinates for each generated conformation.
* hea_us_.txt: Contains two columns and each row represents one generated conformation. The first column provides the lRMSD to the known native conformation for the generated conformation and the second column provides the Rosetta score4 energy for the generated conformation.
* hea_us_rmsd.pdb: Contains coordinates for the lowest lRMSD conformation to the known native conformation.

__Input:__ Uses /configs/hea_us.ini file for inputs. The inputs represented by key-value pairs in the /configs/hea_us.ini file are explained below for each key.

* Section [init]
  * fastaPath: a string indicating the path to the .fasta file containing the amino-acid sequence of the protein.
  * pdbPath: a string indicating the path to the .pdb file containing the coordinates for the known native conformation.
  * population: an integer indicating the population size.
  * evalbudget: an integer indicating the evaluation budget.

* Section [initPopulation]
  * stage1moves: an integer indicating the number of moves for the stage 1 of the initial population generation.
  * stage1score: a string indicating the name of the Rosetta energy function to use for the stage 1 of the initial population generation.
  * stage2successiveFailures: an integer indicating the number of successive failures for the stage 2 of the initial population generation.
  * stage2score: a string indicating the name of the Rosetta energy function to use for the stage 2 of the initial population generation.
  * fragmentLength: an integer indicating the length of the fragments to be used for the initial population generation.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the initial population generation.
  * stage1temperature: an integer indicating the temperature for the MMC search in the stage 1 of the initial population generation.
  * stage2temperature: an integer indicating the temperature for the MMC search in the stage 2 of the initial population generation.

* Section [improvement]
  * score: a string indicating the name of the Rosetta energy function to use for the improvement operator.
  * fragmentLength: an integer indicating the length of the fragments to be used for the improvement operator.
  * successiveFailures: an integer indicating the number of successive failures for the improvement operator.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the improvement operator.
  
* Section [output]
  * filePrefix: a string indicating the path to the directory to save the output files.

### hea_fp.py
Generates conformations for an amino-acid sequence using HEA-FP conformation sampling algorithm.

__Output:__ The output is two .txt files and one .pdb files explained below.

* hea_fp_coordinates.txt: Contains Cα coordinates for each generated conformation.
* hea_fp_.txt: Contains two columns and each row represents one generated conformation. The first column provides the lRMSD to the known native conformation for the generated conformation and the second column provides the Rosetta score4 energy for the generated conformation.
* hea_fp_rmsd.pdb: Contains coordinates for the lowest lRMSD conformation to the known native conformation.

__Input:__ Uses /configs/hea_fp.ini file for inputs. The inputs represented by key-value pairs in the /configs/hea_fp.ini file are explained below for each key.

* Section [init]
  * fastaPath: a string indicating the path to the .fasta file containing the amino-acid sequence of the protein.
  * pdbPath: a string indicating the path to the .pdb file containing the coordinates for the known native conformation.
  * population: an integer indicating the population size.
  * evalbudget: an integer indicating the evaluation budget.

* Section [initPopulation]
  * stage1moves: an integer indicating the number of moves for the stage 1 of the initial population generation.
  * stage1score: a string indicating the name of the Rosetta energy function to use for the stage 1 of the initial population generation.
  * stage2successiveFailures: an integer indicating the number of successive failures for the stage 2 of the initial population generation.
  * stage2score: a string indicating the name of the Rosetta energy function to use for the stage 2 of the initial population generation.
  * fragmentLength: an integer indicating the length of the fragments to be used for the initial population generation.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the initial population generation.
  * stage1temperature: an integer indicating the temperature for the MMC search in the stage 1 of the initial population generation.
  * stage2temperature: an integer indicating the temperature for the MMC search in the stage 2 of the initial population generation.

* Section [improvement]
  * score: a string indicating the name of the Rosetta energy function to use for the improvement operator.
  * fragmentLength: an integer indicating the length of the fragments to be used for the improvement operator.
  * successiveFailures: an integer indicating the number of successive failures for the improvement operator.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the improvement operator.
  
* Section [output]
  * filePrefix: a string indicating the path to the directory to save the output files.


### hea_qt.py
Generates conformations for an amino-acid sequence using HEA-QT conformation sampling algorithm.

__Output:__ The output is two .txt files and one .pdb files explained below.

* hea_qt_coordinates.txt: Contains Cα coordinates for each generated conformation.
* hea_qt_.txt: Contains two columns and each row represents one generated conformation. The first column provides the lRMSD to the known native conformation for the generated conformation and the second column provides the Rosetta score4 energy for the generated conformation.
* hea_qt_rmsd.pdb: Contains coordinates for the lowest lRMSD conformation to the known native conformation.

__Input:__ Uses /configs/hea_qt.ini file for inputs. The inputs represented by key-value pairs in the /configs/hea_qt.ini file are explained below for each key.

* Section [init]
  * fastaPath: a string indicating the path to the .fasta file containing the amino-acid sequence of the protein.
  * pdbPath: a string indicating the path to the .pdb file containing the coordinates for the known native conformation.
  * population: an integer indicating the population size.
  * evalbudget: an integer indicating the evaluation budget.

* Section [initPopulation]
  * stage1moves: an integer indicating the number of moves for the stage 1 of the initial population generation.
  * stage1score: a string indicating the name of the Rosetta energy function to use for the stage 1 of the initial population generation.
  * stage2successiveFailures: an integer indicating the number of successive failures for the stage 2 of the initial population generation.
  * stage2score: a string indicating the name of the Rosetta energy function to use for the stage 2 of the initial population generation.
  * fragmentLength: an integer indicating the length of the fragments to be used for the initial population generation.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the initial population generation.
  * stage1temperature: an integer indicating the temperature for the MMC search in the stage 1 of the initial population generation.
  * stage2temperature: an integer indicating the temperature for the MMC search in the stage 2 of the initial population generation.

* Section [improvement]
  * score: a string indicating the name of the Rosetta energy function to use for the improvement operator.
  * fragmentLength: an integer indicating the length of the fragments to be used for the improvement operator.
  * successiveFailures: an integer indicating the number of successive failures for the improvement operator.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the improvement operator.
  
* Section [output]
  * filePrefix: a string indicating the path to the directory to save the output files.

### spea.py
Generates conformations for an amino-acid sequence using SP-EA<sup>+</sup> conformation sampling algorithm.

__Output:__ The output is two .txt files and two .pdb files explained below.

* spea_coordinates.txt: Contains Cα coordinates for each generated conformation.
* spea_.txt: Contains three columns and each row represents one generated conformation. The first column provides the lRMSD to the Target 1 (a known native conformation) for the generated conformation, the second column provides the lRMSD to the Target 2 (another known native conformation) for the generated conformation and the third column provides the Rosetta score4 energy for the generated conformation.
* spea_rmsd1.pdb: Contains coordinates for the lowest lRMSD conformation to the Target 1.
* spea_rmsd2.pdb: Contains coordinates for the lowest lRMSD conformation to the Target 2.

__Input:__ Uses /configs/spea.ini file for inputs. The inputs represented by key-value pairs in the /configs/spea.ini file are explained below for each key.

* Section [init]
  * fastaPath: a string indicating the path to the .fasta file containing the amino-acid sequence of the protein.
  * pdb1Path: a string indicating the path to the .pdb file containing the coordinates for the Target 1 native conformation.
  * pdb2Path: a string indicating the path to the .pdb file containing the coordinates for the Target 2 native conformation.
  * population: an integer indicating the population size.
  * evalbudget: an integer indicating the evaluation budget.

* Section [initPopulation]
  * stage1moves: an integer indicating the number of moves for the stage 1 of the initial population generation.
  * stage1score: a string indicating the name of the Rosetta energy function to use for the stage 1 of the initial population generation.
  * stage2successiveFailures: an integer indicating the number of successive failures for the stage 2 of the initial population generation.
  * stage2score: a string indicating the name of the Rosetta energy function to use for the stage 2 of the initial population generation.
  * fragmentLength: an integer indicating the length of the fragments to be used for the initial population generation.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the initial population generation.
  * stage1temperature: an integer indicating the temperature for the MMC search in the stage 1 of the initial population generation.
  * stage2temperature: an integer indicating the temperature for the MMC search in the stage 2 of the initial population generation.

* Section [tribal]
  * rmsdLevelCutoff: an integer indicating the distance threshold for leader clustering.
  * competitionFrequency: an integer indicating frequency of subpopulation competition.
  * temperature: an integer indicating the temperature for free energy calculations.

* Section [improvement]
  * score: a string indicating the name of the Rosetta energy function to use for the improvement operator.
  * fragmentLength: an integer indicating the length of the fragments to be used for the improvement operator.
  * successiveFailures: an integer indicating the number of successive failures for the improvement operator.
  * fragmentFile: a string indicating the path to the file containing the fragments to use for the improvement operator.

* Section [selection]
  * elitismRate: a float between 0 and 1 indicating the elitism rate for the truncation selection operator.
  
* Section [output]
  * filePrefix: a string indicating the path to the directory to save the output files.

### relax_analysis.py
Contains code for evaluating energy function bias using Rosetta's FastRelax protocol.

__Output:__ The output is six values in the order below.

* Target 1 score4 energy pre-relax
* Target 2 score4 energy pre-relax
* Target 1 score4 energy post-relax
* Target 2 score4 energy post-relax
* lRMSD between Target 1 pre-relax and post-relax
* lRMSD between Target 2 pre-relax and post-relax

__Input:__ Uses /configs/relax_analysis.ini file for inputs. The inputs represented by key-value pairs in the /configs/relax_analysis.ini file are explained below for the only key.

* Section [init]
  * pdb1: a string indicating the name of the .pdb file containing the coordinates for the Target 1 native conformation.
  * pdb2: a string indicating the name of the .pdb file containing the coordinates for the Target 2 native conformation.
  * pdbPath: a string indicating the path to directory containing the .pdb files for the native conformations.
