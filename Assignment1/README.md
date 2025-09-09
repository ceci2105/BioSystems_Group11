# 1a: 
The maximal reaction values are generally not equal along the linear metabolic pathways. For example consider figure ![Alt text](glucolysisLinearPathway.png) This part of the glucolysis pathway retained same fluxes between GAPD:PKG and PGM:ENO in the interactive session. However, the values are clearly different now! This could be because maximal reaction value is not the same as steady state flux and therefore, doesn't have to retain the mass balance property. While steady state flux are dictated by the Linear Optimization under stochoimetric constraint modeling; The maximal activation values of reactions, on the other hand, are dictated by enzyme availability derived from gene expressions.

# 1b:
I have found 2 reaction types that don't have data in the gene expression data. The 2 reaction types are EXCHANGE & BIOMASS reactions. As shwon on figure: ![Alt text](noDataReactions.png) Any exchange and THE biomass reaction don't have any data avaialble. This makes absolute sense since Exchange reactions exist to maintain mass balance in the system and are there purely for mmodeling purpose; while biomass reaction flux is our objective function, a byproduct of network capabilities defined (among others) by gene expressions.

# 2
For this one we just loaded the model like in practical and manually set the upper & lower bounds as per instructions.

# 3a

We carried out a FVA for all reactions in the "E_coli_core" model.  
This analysis reports the minimal and maximal flux values possible for each reaction, considering all network and expression-based constraints.  

Below is an example:

FVA minimal and maximal fluxes
          minimum    maximum
PFK      0.334677  11.153556
PFL      0.000000   1.000000
PGI     -0.085323   9.020351
PGK    -17.596002  -0.879355
PGL      0.000000   4.522388
ACALD   -1.160000   0.000000
AKGt2r  -3.100000   0.000000
PGM    -17.038932  -0.879355
PIt2r    0.000000   1.783077
ALCD2x  -1.160000   0.000000

From the FVA results we see that most reactions have a minimum flux of 0, meaning they can be inactive depending on the network solution.  
We can notice that reversible reactions show symmetric ranges, while irreversible reactions are constrained to positive or negative values only.  


# 3b

Among reactions with expression-imposed upper bounds, we identified several that cannot reach their allowed upper bound in FVA.  
This means that other network constraints, like stoichiometry or competing reactions, prevent them from using the full enzymatic capacity.   
Number of such reactions: **36**  
List: `['PFK', 'PGI', 'PGL', 'PIt2r', 'ACONTa', 'ACONTb', 'PPCK', 'ADK1', 'AKGDH', 'ATPS4r', 'PTAr', 'PYK', 'CO2t', 'RPE', 'CS', 'CYTBD', 'ENO', 'SUCDi', 'TALA', 'TKT1', 'TKT2', 'TPI', 'FBA', 'FUM', 'G6PDH2r', 'GAPD', 'GLCpts', 'GLUDy', 'GLUN', 'GLUSy', 'GND', 'ICDHyr', 'ICL', 'MALS', 'O2t', 'PDH']`

 
We can notice that gene expression data alone is not sufficient to predict actual metabolic fluxes.  
Even if an enzyme is present in high amounts, the network may restrict its flux due to mass-balance requirements.  
This is consistent with what we saw in exercise 1a, in which the maximal reaction activities are not equal along linear pathways, because unlike steady-state fluxes they do not obey the same mass balance constraints.

# 3c

We also counted reactions with a positive minimal flux in FVA.  
These reactions must always carry flux in the forward direction regardless of the optimization.  
They usually represent essential processes like energy maintenance (ATPM).  
Number of such reactions: **16**  
List: `['PFK', 'ATPM', 'ATPS4r', 'PTAr', 'CS', 'CYTBD', 'ENO', 'TPI', 'EX_h_e', 'EX_h2o_e', 'FBA', 'GAPD', 'GLCpts', 'ICDHyr', 'NADH16', 'O2t']`

The fact that some reactions always have a positive flux indicates that they represent core functions of the metabolism.  
These are reactions that the model cannot skip, because they are directly linked to essential cellular requirements such as ATP hydrolysis.  
This explain the idea of “essential reactions” in metabolic networks, which remain active across different conditions due to their fundamental role in supporting basic cellular functions.





# Use of GenAI
Coopilot to help with using the many many different python functions. Essentially I would write in a comment what I want to acheive and let the copilot do the job. That way me (human) did all the conceptual and decision making work while not having to code much (I can't).