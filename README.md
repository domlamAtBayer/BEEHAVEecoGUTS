## GUTS extension General Information

This repo contains an extension to the BEEHAVEecotox model. 

This extension adds a GUTS effect module as an alternative to the original Dose-response based effect module.

The original README with further information can be found below.

The BEEHAVEecotox model is available at https://github.com/ibacon-GmbH-Modelling/BEEHAVEecotox
This extension does NOT include the landscape extension, only the original BEEHAVEecotox model without landscape extension was changed.

A full model description and the related publication is located at [LINK, will be added soon]. This link includes the full model description in the form of an ODD protocoll. 


The GUTS module requires additional GUTS-parameters, which currently have to be hardcoded in the "to GUTS_init_globals" procedure, and then added to "GUTS_Pesticide" Chooser on the GUI.


### Instructions:
The GUTS extension adds 2 Choosers and 6 input fields to the GUI.

#### Inputfields "Guts_calc_timesteps", "GUTS_k_sr" and "GUTS_k_ca" should remain unchanged.

"Guts_calc_timesteps" defines number of steps to be used in Euler's method for calculation of GUTS. Lower values have previously caused issues, but increasing further increases runtime drastically. Original Value = 200

"GUTS_k_sr" and "GUTS_k_ca" are sourced from the BeeGUTS model (https://doi.org/10.1002/etc.5423) and describe how OralDose and ContactDose develop over time. The given values are honey bee specific.


#### "GUTS_Version" Chooser chooses which effect module to run. 

"NoGuts" runs Dose-response effect module, with parameter values from the GUI or Substance file, whichever is chosen in the "SubstanceApplied" Chooser of the ETOX Landscape update.

"GUTS-Red-SD" runs the GUTS effect module with the reduced SD model, GUTS-Red-SD

"GUTS-Red-IT" runs the GUTS effect module with the reduced IT model, GUTS-Red-IT


#### "GUTS_Pesticide" Chooser chooses which pesticide parameters will be used during the GUTS module. If "GUTS_Version" "NoGuts" was chosen, this chooser has no impact, as DR instead of GUTS will be used as effect module.


If a specific Pesticide is chosen, for example "Dimethoate", the GUTS parameters of this Pesticide will be used during the GUTS module. You should make sure that both the "GUTS_Pesticide"  and "SubstanceApplied" (of the landscape update) choosers use the same pesticide. With the current implementation, not choosing the same values for these choosers will lead to issues if you compare GUTS and DR outputs, as the parameter values will be for different pesticides.


To add new Pesticides to the GUTS module, locate the "to GUTS_init_globals" procedure. You will need to add the new pesticide with GUTS parameter values to both the GUTS-Red-SD and GUTS-Red-IT sections (locations are indicated in the code). The name of the new pesticide then has to be added to the "GUTS_Pesticide" chooser on the GUI as well.

#### Inputfields "GUTS_AppRateMult", "GUTS_TunnelMult" and "GUTS_ContactMult" should remain unchanged
These fields were used for specific experimental simulations. If they remain set to 1, the output of other simulations is unaffected.


#### All additions to the code are indicated with "START GUTS-BeeGUTS-Ecotox" and "END GUTS-BeeGUTS-Ecotox" comments in the code.




## Original ReadMe below:

## Terms of use of the software BEEHAVEecotox (2021)
BEEHAVEecotox (2021) is the implementation of an ecotoxicological module with the associated changes into the model BEEHAVE_BeeMapp2016, developed by Matthias Becher and colleagues (more information on this model is provided below).

This implementation is based on the software platform NetLogo (Wilensky 1999), and can be downloaded for free from https://github.com/BEEHAVE-Model/BEEHAVEecotox.

Please refer to the BEEHAVEecotox publication (Preuss et al., 2022) when using this version of the BEEHAVE model.

## Copyright and Licence Information for the software BEEHAVEecotox (2021):
Copyright 2021

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

A copy of the GNU General Public License can be found at http://www.gnu.org/licenses/gpl.html or write to the Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

## References
Becher, M. A., Grimm, V., Thorbek, P., Horn, J., Kennedy, P. J. & Osborne, J. L. (2014). BEEHAVE: a systems model of honeybee colony dynamics and foraging to explore multifactorial causes of colony failure. Journal of Applied Ecology, 51(2), 470-482.

Grimm, V., Berger, U., Bastiansen, F., Eliassen, S., Ginot, V., Giske, J., … & DeAngelis, D. L. (2006). A standard protocol for describing individual-based and agent-based models. Ecological modelling, 198(1-2), 115-126.

Grimm, V., Berger, U., DeAngelis, D. L., Polhill, J. G., Giske, J. & Railsback, S. F. (2010). The ODD protocol: a review and first update. Ecological modelling, 221(23), 2760-2768.

Grimm, V., Railsback, S. F., Vincenot, C. E., Berger, U., Gallagher, C., DeAngelis, D. L., … & Ayllón, D. (2020). The ODD protocol for describing agent-based and other simulation models: A second update to improve clarity, replication, and structural realism. Journal of Artificial Societies and Social Simulation, 23(2).

Preuss, T.G., Agatz, A., Goussen, B., Roeben, V., Rumkee, J., Zakharova, L. & Thorbek, P. (2022). The BEEHAVEecotox model - Integrating a mechanistic effect module into the honeybee colony model, Environmental Toxicology and Chemist, 41: 2870- 2882.

# Beehave_BeeMapp (2015)
## Terms of use of the software Beehave_BeeMapp (2015)
Beehave (2014) and Beehave_BeeMapp (2015) are implementations of the model BEEHAVE, developed by Matthias Becher and colleagues:

Becher, M.A., Grimm, V., Thorbek, P., Horn, J., Kennedy, P.J. & Osborne, J.L. (2014) BEEHAVE: A systems model of honeybee colony dynamics and foraging to explore multifactorial causes of colony failure. Journal of Applied Ecology.

This implementation is based on the software platform NetLogo (Wilensky 1999), and can be downloaded for free from http://beehave-model.net/.

## Copyright and Licence Information:
Copyright 2015 by Matthias Becher

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

A copy of the GNU General Public License can be found at http://www.gnu.org/licenses/gpl.html or write to the Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

## Recommendations when using BEEHAVE:
* Please refer to the BEEHAVE publication (Becher et al. 2014; see above) and the BEEHAVE website (http://beehave-model.net/) when using BEEHAVE.
* We recommend that any publication or report based on using BEEHAVE shall include, in the Supplementary Material, the very NetLogo file that was used to produce the corresponding figure, table, or other kinds of results, as well as the “Experiments” in the BehaviorSpace and all necessary input files (see Supplementary Material of Becher et al. 2013 as example).
* You might want to modify the NetLogo code implementing BEEHAVE, for example by adding further outputs, or running specific scenarios. To check whether you are still using the original version of BEEHAVE click the “Version Test” button, which runs the model under specific settings and defined random numbers and informs the user if the code was changed. Note that not all changes to the code can be detected by this test. If you changed the code, we recommend to document these changes in all detail and to provide a revised ODD model description in which the modified or added elements are highlighted.
