# Kinetic Modeling and Optimization of a Batch Ethanol Fermentation Process
### Samuel C Oliveira1*, Romulo C Oliveira2, Mariana V Tacin2 and Edwil AL Gattás2
This project aimed to replicate, and perhaps improve, the model developed in the above paper. The paper explores substrate limitation and inhibition by both the product ethanol and the substrate. Personal interest in this subject comes from the rising demand for fuel ethanol calls higher production and more efficient bioprocesses.The simplest models formulated to describe bioprocesses are the unstructured models. In these models, it is assumed that cellsare entities in solution that interact with the environment. Nointernal cell structure is recognized, and the cell population is treated as homogeneous. In structured models, the biomass structureis defined by means of more than one variable, which represent cellcomponents, such as the RNA content, enzymes, reactants and products.

These were my the ordinary differential equations used in the paper


The authors found their parameters to be k = 0.839 1/h, ks = 1.42 g/L, Y = 0.1204, kd = 0.0043 1/h. In my report, I took pH inhibition to be equal to 1 to simplify my analysis.

I decided to focus only on hydrogen productuion in this paper even though the authors showed results and models for several components. The model and experimental data that were found in the paper can be seen below:


Optimizing Parameters for a Model Fit
I performed my own model fit using the minimize function in python. The results were different than that of the paper, but I did not have as much confidence in them. There was not many attempts made by the solver and the error was around 11%. However, the parameters that were found produced a model that was similar to the original found in the paper. The following chart shows the model that was found in my analysis:


When comparing to the Authors' model, it can be seen that there is slightly more error associated with each data point, especially in the 15-35 hr region. The parameters that resulted in this optimization were as follows: k = 0.9 1/h, ks = 1.40 g/L, Y = 0.1, kd = 0.002 1/h. Overall, the resulting model was realistic, but there was room for improvement. Therefore, further analysis was completed to determine if the parameters could be narrowed down to more accurate values.

Bifurcation Analysis
To determine the stability and steady state behavior of the model, flow-on-a-line and bifurcation analyses were performed. The parameter chosen for the bifuraction was k, as it had a relatively simple relationship with the substrate consumption rate. The flow-on-a-line graph can be seen below:


It can be seen that there is a steady state relatively close to zero. After zooming in on the specific region, the steady state value of dS/dt was found to be roughly at S = 0.3. To determine how this would change upon alteration of the k parameter, several values of k were simulated and plotted for this equation. The results can be seen below:


To obtain a more finite result, the steady state S values were plotted as a function of k values. The following chart shows a more exact behavior of the bifurcation:


It can be seen that around k = 1.85, the steady state S value drops from 0.3 to around 0.1. This, then, should be kept in mind when completing further analysis of the parameters. If k were to become greater than 1.85, the system will exhibit different behavior and possibly hold a different model shape.

Sensitivity Analysis
To test the model's sensitivity to each parameter, an analysis of each was performed by slight perturbation of the parameter value. First, a 1% perturbation of each was tested. The resulting models were not distinct enough, therefore a 5% perturbation was tried. The following figures display the results of this analysis.



It can be seen that the k parameter affects the system the most and, therefore, should be explored more in-depth. Optimization was then revisited by only focusing on k and leaving the other parameters untouched. The resulting value determined by the minimize python function was k = 0.6973. If this value is simulated identically to the method described earlier, the model becomes slighlty closer to the data values. An image of the improved model can be seen, below:


When comparing to the Authors' model, there is slightly less errror, particularly in the 15-35 hr region. It is acknowledged, however, that this new model may not correctly account for all aspects of the real system as several simplifications were made for the scope of this project. Therefore, further, repeated analysis should be done with the other parameters and while taking the previously ignored aspects into account.

Overall, the explored model was able to be validated within a realistic degree of accuracy, and re-parameterization of k showed a slight improvement to the error held by the model.
