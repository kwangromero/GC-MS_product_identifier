# GC-MS_product_identifier

Problem: When multiple types of reactants (between 2-10) are mixed together, many different products can arise from the reaction between any of these input molecules.
But what exactly are these products? We can identify the masses of potentially interesting products by mass spectrometry as implemented by a GC-MS instrument.
However, what we don't know is what molecules were involved to form such product.

Preliminary solution: The GC-MS_product_identifier script is the first step in answering such questions. Assuming that each input molecule can be fragmented into a 
certain number of components, the script then finds all possible combinations between these fragments and only outputs the combinations that match the product mass
seen from a GC-MS mass output.

General work flow example:
1) Three different types of reactants (i.e. A, B, and C) are added to a reaction tube along with any additional reagents that are necessary for the reaction to occur.
2) Suppose each of the three reactants can be fragmented into two components:
(A => A1 + A2), 
(B => B1 + B2), 
(C => C1 + C2)
3) Assuming a product is formed by forming bonds between two fragments, the possible products that may form include:
A1-B1, A1-B2, A1-C1, A1-C2, A2-B1, A2-B2, A2-C1, A2-C2, B1-C1, B1-C2, C1-B2
4) The user will manually input the masses of each component (i.e., A1, A2, B1, B2, C1, C2) in a separate csv file titled "fragment_molar-masses"
5) The script will read-in the masses of each fragment from fragment_molar-masses.csv and determine the corresponding masses of all possible products as listed in 
step 3.
6) The user will input a mass in the variable `obs_GC_mass` (located in section 1 of the Jupyter Notebook) which is the mass they observe from GC-MS output 
and what they deem to be the mass of a product.
7) The output of the script will be a dataframe that lists out all possible products that have masses that are between +/- 1 of the mass inputted by the user in the variable `obs_GC_mass`
