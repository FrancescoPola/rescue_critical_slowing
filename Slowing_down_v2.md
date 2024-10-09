---
title: "Slowing down in recovery of phytoplankton community due to recurrent heatwaves"
author: "Francesco Polazzo"
date: "01 October, 2024"
output:
  bookdown::html_document2:
    toc: true
    toc_float:
      collapsed: true
      smooth_scroll: true
    code_folding: hide
    keep_md: yes
editor_options: 
  markdown: 
    wrap: 72
---





# Introduction

With this article we wanted to test two major ecological framework that are commonly applied to systems facing repeated perturbations: 

- Critical slowing down (https://www.journals.uchicago.edu/doi/full/10.1086/516845) (https://www.nature.com/articles/nature10723)

- Community rescue (https://www.nature.com/articles/s41559-020-1134-5)

For this we used data coming from an outdoor pond mesocosm experiment (2021 Spain) where a semi-natural phytoplankton community was exposed to three subsequent heatwaves. Heatwaves are becoming more frequent and more intense, rising concerns about whether and how natural communities can face these perturbations and keep performing their functions. Critically, increasing research is suggesting that heatwaves can cause ecological systems to transition.

This transitions, also called tipping points, represent particular points at which complex systems can shift abruptly from one state to another, and they are notoriously difficult to predict.
Attention has thus turned to inferring process from pattern – identifying phenomenological signals in measurable aspect of a biological system that indicates shifts in the under-lying processes that may alter the structure and function of the system. A key development in the search for such pattern-based indicators is early warning signals (EWSs) derived from dynamic systems theory (all Scheffer's papers)

Theory proposes that early warning signals may be based on the phenomenon that recovery rates from perturbations should tend to zero when approaching a tipping point. However, evidence that this happens in living systems is scarce (at best).



Community rescue occurs when ecological or evolutionary processes restore positive growth in a highly stressful environment that was lethal to the community in its ancestral form, thus averting biomass collapse in a deteriorating environment. Very few empirical examples exist about community rescue, yet it is though to be one key mechanism that increases stress resistance in communities and contribute maintaining aggregate community properties such as biomass under stressful conditions.

Here we test whether a semi-natural phytoplankton community undergoing repeated heatwave perturbation shows signs of critical slowing down or community rescue. 



# Results
## Water temperature time series
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/temperature_plot-1.png" alt="Water temperature dynamics over time."  />
<p class="caption">(\#fig:temperature_plot)Water temperature dynamics over time.</p>
</div>
The water temperature manipulation using the TENTACLE machinery [https://www.sciencedirect.com/science/article/pii/S2468067222000529] worked quite well. 

## Ecosystem functioning endpoints

### Dissolved oxygen 


Oxygen shows an impaired recovery after the third heatwave. The contrast with the first two heatwave is striking. Indeed, the first two heatwaves determined a decline in DO only while happening, with DO quickly returning to levels higher than the control. The third heatwave strongly decreased DO during its course, and slowed down its recovery in the post HW phase so that it never got back to control levels.
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/oxygen_plot-1.png" alt="Dissolved oxygen dynamics over time. The red areas show the three heatwaves. The figure shows the difference in DO between mesocosm undergoing the HWs treatment and the control (dashed line at zero)."  />
<p class="caption">(\#fig:oxygen_plot)Dissolved oxygen dynamics over time. The red areas show the three heatwaves. The figure shows the difference in DO between mesocosm undergoing the HWs treatment and the control (dashed line at zero).</p>
</div>

We now look specifically at how the slope of recovery changes after each HW. To do that we look at the slope of the linear regression between two subsequent time points (during and after a HW) of the difference between DO in control and HW mesocosms.
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/oxygen_slopes-1.png" alt="Change in the slope of the linear regression connecting two subsequent time point ((during and after a HW) of the difference between DO in control and HW mesocosms."  />
<p class="caption">(\#fig:oxygen_slopes)Change in the slope of the linear regression connecting two subsequent time point ((during and after a HW) of the difference between DO in control and HW mesocosms.</p>
</div>

Summary plot for the manuscript

<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/oxy_combined-1.png" alt="combined plot for manuscript"  />
<p class="caption">(\#fig:oxy_combined)combined plot for manuscript</p>
</div>

Creating model for oxygen

``` r
model_ox <- lmer(log(ox) ~ Treatment * Day + (1 | Cosm), data = ox)
```

Model diagnostics
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/check_ox_model-1.png" alt="Checking assumption for oxygen model"  />
<p class="caption">(\#fig:check_ox_model)Checking assumption for oxygen model</p>
</div>
Not bad.


<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> effect </th>
   <th style="text-align:left;"> group </th>
   <th style="text-align:left;"> term </th>
   <th style="text-align:right;"> estimate </th>
   <th style="text-align:right;"> std.error </th>
   <th style="text-align:right;"> statistic </th>
   <th style="text-align:right;"> df </th>
   <th style="text-align:right;"> p.value </th>
   <th style="text-align:right;"> 2.5% </th>
   <th style="text-align:right;"> 97.5% </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:right;"> 2.435 </td>
   <td style="text-align:right;"> 0.039 </td>
   <td style="text-align:right;"> 62.613 </td>
   <td style="text-align:right;"> 26.146 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 2.361 </td>
   <td style="text-align:right;"> 2.508 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:right;"> 0.060 </td>
   <td style="text-align:right;"> 0.055 </td>
   <td style="text-align:right;"> 1.090 </td>
   <td style="text-align:right;"> 26.146 </td>
   <td style="text-align:right;"> 0.286 </td>
   <td style="text-align:right;"> -0.044 </td>
   <td style="text-align:right;"> 0.164 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 1.957 </td>
   <td style="text-align:right;"> 46.000 </td>
   <td style="text-align:right;"> 0.056 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.007 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:right;"> -0.007 </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> -2.689 </td>
   <td style="text-align:right;"> 46.000 </td>
   <td style="text-align:right;"> 0.010 </td>
   <td style="text-align:right;"> -0.012 </td>
   <td style="text-align:right;"> -0.002 </td>
  </tr>
</tbody>
</table>






Post - hoc analysis. Let see when the HW treatment had a significant impact on phyto abundance
<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> contrast </th>
   <th style="text-align:right;"> Day </th>
   <th style="text-align:right;"> estimate </th>
   <th style="text-align:right;"> SE </th>
   <th style="text-align:right;"> df </th>
   <th style="text-align:right;"> t.ratio </th>
   <th style="text-align:right;"> p.value </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> -4 </td>
   <td style="text-align:right;"> -0.087 </td>
   <td style="text-align:right;"> 0.063 </td>
   <td style="text-align:right;"> 35.683 </td>
   <td style="text-align:right;"> -1.381 </td>
   <td style="text-align:right;"> 0.176 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:right;"> -0.040 </td>
   <td style="text-align:right;"> 0.050 </td>
   <td style="text-align:right;"> 19.228 </td>
   <td style="text-align:right;"> -0.802 </td>
   <td style="text-align:right;"> 0.432 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:right;"> 0.007 </td>
   <td style="text-align:right;"> 0.040 </td>
   <td style="text-align:right;"> 8.677 </td>
   <td style="text-align:right;"> 0.182 </td>
   <td style="text-align:right;"> 0.860 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 15 </td>
   <td style="text-align:right;"> 0.041 </td>
   <td style="text-align:right;"> 0.036 </td>
   <td style="text-align:right;"> 6.142 </td>
   <td style="text-align:right;"> 1.122 </td>
   <td style="text-align:right;"> 0.304 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 24 </td>
   <td style="text-align:right;"> 0.101 </td>
   <td style="text-align:right;"> 0.041 </td>
   <td style="text-align:right;"> 9.486 </td>
   <td style="text-align:right;"> 2.490 </td>
   <td style="text-align:right;font-weight: bold;"> 0.033 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 30 </td>
   <td style="text-align:right;"> 0.142 </td>
   <td style="text-align:right;"> 0.049 </td>
   <td style="text-align:right;"> 18.925 </td>
   <td style="text-align:right;"> 2.869 </td>
   <td style="text-align:right;font-weight: bold;"> 0.010 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 38 </td>
   <td style="text-align:right;"> 0.195 </td>
   <td style="text-align:right;"> 0.065 </td>
   <td style="text-align:right;"> 37.548 </td>
   <td style="text-align:right;"> 3.023 </td>
   <td style="text-align:right;font-weight: bold;"> 0.004 </td>
  </tr>
</tbody>
</table>




Visualization of model prediction (linear trend)
![](Slowing_down_v2_files/figure-html/unnamed-chunk-9-1.png)<!-- -->

### Chlorophyll - a


Chlorophyll - a shows probably the most dramatic response. There is not much change happening until the third heatwave, which determines a drop in chlorphyll - a. This strong decline reflect the compositional change and especially the reduction in biomass. 

<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/chlorophyll_plot-1.png" alt="CHlorophyll-a dynamics over time. The red areas show the three heatwaves"  />
<p class="caption">(\#fig:chlorophyll_plot)CHlorophyll-a dynamics over time. The red areas show the three heatwaves</p>
</div>


We now look specifically at how the slope of recovery changes after each HW. To do that we look at the slope of the linear regression between two subsequent time points (during and after a HW) of the difference between chlorophyll - a concentration in control and HW mesocosms.
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/chla_slopes-1.png" alt="Change in the slope of the linear regression connecting two subsequent time point (during and after a HW) of the difference between chlorophyll - a concentration in control and HW mesocosms."  />
<p class="caption">(\#fig:chla_slopes)Change in the slope of the linear regression connecting two subsequent time point (during and after a HW) of the difference between chlorophyll - a concentration in control and HW mesocosms.</p>
</div>
Summary plot for the manuscript
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/chla_combined-1.png" alt="combined plot for manuscript"  />
<p class="caption">(\#fig:chla_combined)combined plot for manuscript</p>
</div>


Creating model for chla

``` r
model_chla <- lmer(log(chla) ~ Treatment * Day + (1 | Cosm), data = chla)
```

<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> effect </th>
   <th style="text-align:left;"> group </th>
   <th style="text-align:left;"> term </th>
   <th style="text-align:right;"> estimate </th>
   <th style="text-align:right;"> std.error </th>
   <th style="text-align:right;"> statistic </th>
   <th style="text-align:right;"> df </th>
   <th style="text-align:right;"> p.value </th>
   <th style="text-align:right;"> 2.5% </th>
   <th style="text-align:right;"> 97.5% </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:right;"> 0.657 </td>
   <td style="text-align:right;"> 0.214 </td>
   <td style="text-align:right;"> 3.071 </td>
   <td style="text-align:right;"> 25.799 </td>
   <td style="text-align:right;"> 0.005 </td>
   <td style="text-align:right;"> 0.252 </td>
   <td style="text-align:right;"> 1.062 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:right;"> -0.650 </td>
   <td style="text-align:right;"> 0.303 </td>
   <td style="text-align:right;"> -2.148 </td>
   <td style="text-align:right;"> 25.799 </td>
   <td style="text-align:right;"> 0.041 </td>
   <td style="text-align:right;"> -1.222 </td>
   <td style="text-align:right;"> -0.078 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:right;"> 0.011 </td>
   <td style="text-align:right;"> 0.010 </td>
   <td style="text-align:right;"> 1.108 </td>
   <td style="text-align:right;"> 46.000 </td>
   <td style="text-align:right;"> 0.274 </td>
   <td style="text-align:right;"> -0.008 </td>
   <td style="text-align:right;"> 0.029 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:right;"> -0.020 </td>
   <td style="text-align:right;"> 0.014 </td>
   <td style="text-align:right;"> -1.440 </td>
   <td style="text-align:right;"> 46.000 </td>
   <td style="text-align:right;"> 0.157 </td>
   <td style="text-align:right;"> -0.046 </td>
   <td style="text-align:right;"> 0.007 </td>
  </tr>
</tbody>
</table>





Model diagnostics
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/check_chla_model-1.png" alt="Checking assumption for chlorophyll - a model"  />
<p class="caption">(\#fig:check_chla_model)Checking assumption for chlorophyll - a model</p>
</div>
Not too bad, but homogeneity of variance a bit messy. Consider transformation.


Post - hoc analysis. Let see when the HW treatment had a significant impact on phyto abundance
<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> contrast </th>
   <th style="text-align:right;"> Day </th>
   <th style="text-align:right;"> estimate </th>
   <th style="text-align:right;"> SE </th>
   <th style="text-align:right;"> df </th>
   <th style="text-align:right;"> t.ratio </th>
   <th style="text-align:right;"> p.value </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> -4 </td>
   <td style="text-align:right;"> 0.571 </td>
   <td style="text-align:right;"> 0.346 </td>
   <td style="text-align:right;"> 35.284 </td>
   <td style="text-align:right;"> 1.652 </td>
   <td style="text-align:right;"> 0.107 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:right;"> 0.709 </td>
   <td style="text-align:right;"> 0.273 </td>
   <td style="text-align:right;"> 18.979 </td>
   <td style="text-align:right;"> 2.596 </td>
   <td style="text-align:right;font-weight: bold;"> 0.018 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:right;"> 0.847 </td>
   <td style="text-align:right;"> 0.219 </td>
   <td style="text-align:right;"> 8.627 </td>
   <td style="text-align:right;"> 3.861 </td>
   <td style="text-align:right;font-weight: bold;"> 0.004 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 15 </td>
   <td style="text-align:right;"> 0.946 </td>
   <td style="text-align:right;"> 0.201 </td>
   <td style="text-align:right;"> 6.140 </td>
   <td style="text-align:right;"> 4.700 </td>
   <td style="text-align:right;font-weight: bold;"> 0.003 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 24 </td>
   <td style="text-align:right;"> 1.123 </td>
   <td style="text-align:right;"> 0.225 </td>
   <td style="text-align:right;"> 9.421 </td>
   <td style="text-align:right;"> 5.004 </td>
   <td style="text-align:right;font-weight: bold;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 30 </td>
   <td style="text-align:right;"> 1.242 </td>
   <td style="text-align:right;"> 0.272 </td>
   <td style="text-align:right;"> 18.681 </td>
   <td style="text-align:right;"> 4.569 </td>
   <td style="text-align:right;font-weight: bold;"> 0.000 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 38 </td>
   <td style="text-align:right;"> 1.400 </td>
   <td style="text-align:right;"> 0.355 </td>
   <td style="text-align:right;"> 37.154 </td>
   <td style="text-align:right;"> 3.940 </td>
   <td style="text-align:right;font-weight: bold;"> 0.000 </td>
  </tr>
</tbody>
</table>
As expected from the plot, the estimate increases with time, and there is a big jump from day 31 to 38, corresponding to the drop in chla.




Visualization of model prediction (linear trend)
![](Slowing_down_v2_files/figure-html/unnamed-chunk-16-1.png)<!-- -->

## Compositional dynamics




### Total phytoplankton biomass dynamics


<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/phyto_bio_plot-1.png" alt="Phytoplankton biomass dynamics over time. The red areas show the three heatwaves"  />
<p class="caption">(\#fig:phyto_bio_plot)Phytoplankton biomass dynamics over time. The red areas show the three heatwaves</p>
</div>

We now look specifically at how the slope of recovery changes after each HW. To do that we look at the slope of the linear regression between two subsequent time points (during and after a HW) of the difference between phytoplankton biomass in HW mesocosms and controls .
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/phyto_bio_slopes-1.png" alt="Change in the slope of the linear regression connecting two subsequent time point (during and after a HW) of the difference between phytoplankton biomass in HW and control mesocosms."  />
<p class="caption">(\#fig:phyto_bio_slopes)Change in the slope of the linear regression connecting two subsequent time point (during and after a HW) of the difference between phytoplankton biomass in HW and control mesocosms.</p>
</div>




Creating model for phyto biomass

``` r
model_phyto_bio <- lmer(log(total) ~ Treatment * Day + (1 | Sample), data = try)
```

<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> effect </th>
   <th style="text-align:left;"> group </th>
   <th style="text-align:left;"> term </th>
   <th style="text-align:right;"> estimate </th>
   <th style="text-align:right;"> std.error </th>
   <th style="text-align:right;"> statistic </th>
   <th style="text-align:right;"> df </th>
   <th style="text-align:right;"> p.value </th>
   <th style="text-align:right;"> 2.5% </th>
   <th style="text-align:right;"> 97.5% </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:right;"> 0.891 </td>
   <td style="text-align:right;"> 0.051 </td>
   <td style="text-align:right;"> 17.457 </td>
   <td style="text-align:right;"> 52 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.793 </td>
   <td style="text-align:right;"> 0.989 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:right;"> -0.103 </td>
   <td style="text-align:right;"> 0.072 </td>
   <td style="text-align:right;"> -1.432 </td>
   <td style="text-align:right;"> 52 </td>
   <td style="text-align:right;"> 0.158 </td>
   <td style="text-align:right;"> -0.242 </td>
   <td style="text-align:right;"> 0.035 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:right;"> 0.001 </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 0.255 </td>
   <td style="text-align:right;"> 52 </td>
   <td style="text-align:right;"> 0.800 </td>
   <td style="text-align:right;"> -0.004 </td>
   <td style="text-align:right;"> 0.005 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:right;"> -0.006 </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> -1.664 </td>
   <td style="text-align:right;"> 52 </td>
   <td style="text-align:right;"> 0.102 </td>
   <td style="text-align:right;"> -0.012 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>





Model diagnostics
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/check_phyto_bio_model-1.png" alt="Checking assumption for chlorophyll - a model"  />
<p class="caption">(\#fig:check_phyto_bio_model)Checking assumption for chlorophyll - a model</p>
</div>
Not too bad, but homogeneity of variance a bit messy. Consider transformation.


Post - hoc analysis. Let see when the HW treatment had a significant impact on phyto abundance
<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> contrast </th>
   <th style="text-align:right;"> Day </th>
   <th style="text-align:right;"> estimate </th>
   <th style="text-align:right;"> SE </th>
   <th style="text-align:right;"> df </th>
   <th style="text-align:right;"> t.ratio </th>
   <th style="text-align:right;"> p.value </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> -4 </td>
   <td style="text-align:right;"> 0.081 </td>
   <td style="text-align:right;"> 0.083 </td>
   <td style="text-align:right;"> 37.643 </td>
   <td style="text-align:right;"> 0.979 </td>
   <td style="text-align:right;"> 0.334 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:right;"> 0.120 </td>
   <td style="text-align:right;"> 0.065 </td>
   <td style="text-align:right;"> 20.521 </td>
   <td style="text-align:right;"> 1.851 </td>
   <td style="text-align:right;"> 0.079 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:right;"> 0.159 </td>
   <td style="text-align:right;"> 0.051 </td>
   <td style="text-align:right;"> 8.935 </td>
   <td style="text-align:right;"> 3.099 </td>
   <td style="text-align:right;font-weight: bold;"> 0.013 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 15 </td>
   <td style="text-align:right;"> 0.187 </td>
   <td style="text-align:right;"> 0.047 </td>
   <td style="text-align:right;"> 6.155 </td>
   <td style="text-align:right;"> 4.003 </td>
   <td style="text-align:right;font-weight: bold;"> 0.007 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 24 </td>
   <td style="text-align:right;"> 0.237 </td>
   <td style="text-align:right;"> 0.053 </td>
   <td style="text-align:right;"> 9.827 </td>
   <td style="text-align:right;"> 4.503 </td>
   <td style="text-align:right;font-weight: bold;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 30 </td>
   <td style="text-align:right;"> 0.270 </td>
   <td style="text-align:right;"> 0.064 </td>
   <td style="text-align:right;"> 20.192 </td>
   <td style="text-align:right;"> 4.187 </td>
   <td style="text-align:right;font-weight: bold;"> 0.000 </td>
  </tr>
  <tr>
   <td style="text-align:left;font-weight: bold;"> Control - HW </td>
   <td style="text-align:right;"> 38 </td>
   <td style="text-align:right;"> 0.314 </td>
   <td style="text-align:right;"> 0.085 </td>
   <td style="text-align:right;"> 39.467 </td>
   <td style="text-align:right;"> 3.689 </td>
   <td style="text-align:right;font-weight: bold;"> 0.001 </td>
  </tr>
</tbody>
</table>






### Relative biomass 
Now we want to see if this gradual decline in oxygen and chla is related to taxonomic differences. 
We start looking at the relative biomass of different phytoplankton group over time


Let's have a look at how different taxonomic groups of phytoplankton change over time in terms of relative biomass 

The relative abundance of different groups changes largely over time, and may align with the drop in ecosystem functioning endpoints. 
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/relative_abundance_plot-1.png" alt="Change in relative abundance of phytoplankton groups over time in the control and heatwave treatment"  />
<p class="caption">(\#fig:relative_abundance_plot)Change in relative abundance of phytoplankton groups over time in the control and heatwave treatment</p>
</div>




we now look if this visual turnover in relative groups biomass is statistically significant

### PERMANOVA



<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:right;"> Day </th>
   <th style="text-align:right;"> F </th>
   <th style="text-align:right;"> R2 </th>
   <th style="text-align:right;"> p_value </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> -4 </td>
   <td style="text-align:right;"> 0.8948819 </td>
   <td style="text-align:right;"> 0.1297893 </td>
   <td style="text-align:right;"> 0.367 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:right;"> 3.0912488 </td>
   <td style="text-align:right;"> 0.3400247 </td>
   <td style="text-align:right;"> 0.067 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:right;"> 4.3762727 </td>
   <td style="text-align:right;"> 0.4217577 </td>
   <td style="text-align:right;font-weight: bold;"> 0.027 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 15 </td>
   <td style="text-align:right;"> 1.7662055 </td>
   <td style="text-align:right;"> 0.2274219 </td>
   <td style="text-align:right;"> 0.150 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 24 </td>
   <td style="text-align:right;"> 0.7826261 </td>
   <td style="text-align:right;"> 0.1153869 </td>
   <td style="text-align:right;"> 0.569 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 30 </td>
   <td style="text-align:right;"> 3.1091493 </td>
   <td style="text-align:right;"> 0.3413216 </td>
   <td style="text-align:right;font-weight: bold;"> 0.032 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 38 </td>
   <td style="text-align:right;"> 2.5529821 </td>
   <td style="text-align:right;"> 0.2984903 </td>
   <td style="text-align:right;font-weight: bold;"> 0.026 </td>
  </tr>
</tbody>
</table>

Significant differences on day 2, 10, 30, and 38



### SIMPER

SIMPER analysis - results and biomass comparison by day




Table results Day -4 


<table class="table table-striped table-hover" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>(\#tab:unnamed-chunk-28)SIMPER Analysis Results for Day -4: HW vs Control</caption>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> species </th>
   <th style="text-align:right;"> average </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> ratio </th>
   <th style="text-align:right;"> ava </th>
   <th style="text-align:right;"> avb </th>
   <th style="text-align:right;"> cumsum </th>
   <th style="text-align:right;"> p </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:right;"> 0.206 </td>
   <td style="text-align:right;"> 0.171 </td>
   <td style="text-align:right;"> 1.207 </td>
   <td style="text-align:right;"> 293.749 </td>
   <td style="text-align:right;"> 99.457 </td>
   <td style="text-align:right;"> 0.371 </td>
   <td style="text-align:right;"> 0.401 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:right;"> 0.133 </td>
   <td style="text-align:right;"> 0.131 </td>
   <td style="text-align:right;"> 1.013 </td>
   <td style="text-align:right;"> 228.716 </td>
   <td style="text-align:right;"> 42.859 </td>
   <td style="text-align:right;"> 0.611 </td>
   <td style="text-align:right;"> 0.083 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:right;"> 0.133 </td>
   <td style="text-align:right;"> 0.104 </td>
   <td style="text-align:right;"> 1.273 </td>
   <td style="text-align:right;"> 215.925 </td>
   <td style="text-align:right;"> 206.102 </td>
   <td style="text-align:right;"> 0.850 </td>
   <td style="text-align:right;"> 0.319 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:right;"> 0.072 </td>
   <td style="text-align:right;"> 0.036 </td>
   <td style="text-align:right;"> 2.011 </td>
   <td style="text-align:right;"> 109.057 </td>
   <td style="text-align:right;"> 35.663 </td>
   <td style="text-align:right;"> 0.980 </td>
   <td style="text-align:right;"> 0.177 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:right;"> 0.007 </td>
   <td style="text-align:right;"> 0.006 </td>
   <td style="text-align:right;"> 1.157 </td>
   <td style="text-align:right;"> 14.110 </td>
   <td style="text-align:right;"> 2.809 </td>
   <td style="text-align:right;"> 0.992 </td>
   <td style="text-align:right;"> 0.728 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.004 </td>
   <td style="text-align:right;"> 0.695 </td>
   <td style="text-align:right;"> 6.179 </td>
   <td style="text-align:right;"> 0.373 </td>
   <td style="text-align:right;"> 0.997 </td>
   <td style="text-align:right;"> 0.428 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 0.768 </td>
   <td style="text-align:right;"> 0.559 </td>
   <td style="text-align:right;"> 1.160 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.875 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> NaN </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>



Table results Day 3


<table class="table table-striped table-hover" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>(\#tab:unnamed-chunk-30)SIMPER Analysis Results for Day 3: HW vs Control</caption>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> species </th>
   <th style="text-align:right;"> average </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> ratio </th>
   <th style="text-align:right;"> ava </th>
   <th style="text-align:right;"> avb </th>
   <th style="text-align:right;"> cumsum </th>
   <th style="text-align:right;"> p </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:right;"> 0.513 </td>
   <td style="text-align:right;"> 0.289 </td>
   <td style="text-align:right;"> 1.779 </td>
   <td style="text-align:right;"> 75.579 </td>
   <td style="text-align:right;"> 230.067 </td>
   <td style="text-align:right;"> 0.741 </td>
   <td style="text-align:right;"> 0.051 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:right;"> 0.076 </td>
   <td style="text-align:right;"> 0.091 </td>
   <td style="text-align:right;"> 0.834 </td>
   <td style="text-align:right;"> 8.011 </td>
   <td style="text-align:right;"> 21.363 </td>
   <td style="text-align:right;"> 0.850 </td>
   <td style="text-align:right;"> 0.332 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:right;"> 0.047 </td>
   <td style="text-align:right;"> 0.081 </td>
   <td style="text-align:right;"> 0.584 </td>
   <td style="text-align:right;"> 16.870 </td>
   <td style="text-align:right;"> 1.239 </td>
   <td style="text-align:right;"> 0.919 </td>
   <td style="text-align:right;"> 0.908 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:right;"> 0.042 </td>
   <td style="text-align:right;"> 0.062 </td>
   <td style="text-align:right;"> 0.682 </td>
   <td style="text-align:right;"> 0.342 </td>
   <td style="text-align:right;"> 17.338 </td>
   <td style="text-align:right;"> 0.980 </td>
   <td style="text-align:right;"> 0.037 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:right;"> 0.007 </td>
   <td style="text-align:right;"> 0.010 </td>
   <td style="text-align:right;"> 0.642 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.684 </td>
   <td style="text-align:right;"> 0.990 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:right;"> 0.005 </td>
   <td style="text-align:right;"> 0.006 </td>
   <td style="text-align:right;"> 0.766 </td>
   <td style="text-align:right;"> 1.439 </td>
   <td style="text-align:right;"> 0.804 </td>
   <td style="text-align:right;"> 0.997 </td>
   <td style="text-align:right;"> 0.944 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.705 </td>
   <td style="text-align:right;"> 0.186 </td>
   <td style="text-align:right;"> 0.747 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.370 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> NaN </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>



Table results Day 10


<table class="table table-striped table-hover" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>(\#tab:unnamed-chunk-32)SIMPER Analysis Results for Day 10: HW vs Control</caption>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> species </th>
   <th style="text-align:right;"> average </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> ratio </th>
   <th style="text-align:right;"> ava </th>
   <th style="text-align:right;"> avb </th>
   <th style="text-align:right;"> cumsum </th>
   <th style="text-align:right;"> p </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:right;"> 0.272 </td>
   <td style="text-align:right;"> 0.237 </td>
   <td style="text-align:right;"> 1.147 </td>
   <td style="text-align:right;"> 32.657 </td>
   <td style="text-align:right;"> 135.963 </td>
   <td style="text-align:right;"> 0.407 </td>
   <td style="text-align:right;"> 0.031 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:right;"> 0.148 </td>
   <td style="text-align:right;"> 0.121 </td>
   <td style="text-align:right;"> 1.224 </td>
   <td style="text-align:right;"> 9.747 </td>
   <td style="text-align:right;"> 65.023 </td>
   <td style="text-align:right;"> 0.628 </td>
   <td style="text-align:right;"> 0.053 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:right;"> 0.146 </td>
   <td style="text-align:right;"> 0.108 </td>
   <td style="text-align:right;"> 1.347 </td>
   <td style="text-align:right;"> 13.064 </td>
   <td style="text-align:right;"> 45.836 </td>
   <td style="text-align:right;"> 0.846 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:right;"> 0.072 </td>
   <td style="text-align:right;"> 0.078 </td>
   <td style="text-align:right;"> 0.926 </td>
   <td style="text-align:right;"> 5.035 </td>
   <td style="text-align:right;"> 34.741 </td>
   <td style="text-align:right;"> 0.954 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:right;"> 0.023 </td>
   <td style="text-align:right;"> 0.025 </td>
   <td style="text-align:right;"> 0.911 </td>
   <td style="text-align:right;"> 3.339 </td>
   <td style="text-align:right;"> 11.008 </td>
   <td style="text-align:right;"> 0.988 </td>
   <td style="text-align:right;"> 0.184 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:right;"> 0.005 </td>
   <td style="text-align:right;"> 0.007 </td>
   <td style="text-align:right;"> 0.803 </td>
   <td style="text-align:right;"> 0.550 </td>
   <td style="text-align:right;"> 2.366 </td>
   <td style="text-align:right;"> 0.996 </td>
   <td style="text-align:right;"> 0.946 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.004 </td>
   <td style="text-align:right;"> 0.713 </td>
   <td style="text-align:right;"> 1.014 </td>
   <td style="text-align:right;"> 0.765 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.975 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> NaN </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>



Table results Day 15


<table class="table table-striped table-hover" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>(\#tab:unnamed-chunk-34)SIMPER Analysis Results for Day 15: HW vs Control</caption>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> species </th>
   <th style="text-align:right;"> average </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> ratio </th>
   <th style="text-align:right;"> ava </th>
   <th style="text-align:right;"> avb </th>
   <th style="text-align:right;"> cumsum </th>
   <th style="text-align:right;"> p </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:right;"> 0.430 </td>
   <td style="text-align:right;"> 0.249 </td>
   <td style="text-align:right;"> 1.729 </td>
   <td style="text-align:right;"> 68.053 </td>
   <td style="text-align:right;"> 307.782 </td>
   <td style="text-align:right;"> 0.687 </td>
   <td style="text-align:right;"> 0.120 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:right;"> 0.091 </td>
   <td style="text-align:right;"> 0.089 </td>
   <td style="text-align:right;"> 1.021 </td>
   <td style="text-align:right;"> 46.209 </td>
   <td style="text-align:right;"> 26.590 </td>
   <td style="text-align:right;"> 0.832 </td>
   <td style="text-align:right;"> 0.949 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:right;"> 0.063 </td>
   <td style="text-align:right;"> 0.077 </td>
   <td style="text-align:right;"> 0.808 </td>
   <td style="text-align:right;"> 10.681 </td>
   <td style="text-align:right;"> 29.374 </td>
   <td style="text-align:right;"> 0.932 </td>
   <td style="text-align:right;"> 0.062 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:right;"> 0.030 </td>
   <td style="text-align:right;"> 0.024 </td>
   <td style="text-align:right;"> 1.232 </td>
   <td style="text-align:right;"> 8.345 </td>
   <td style="text-align:right;"> 15.295 </td>
   <td style="text-align:right;"> 0.980 </td>
   <td style="text-align:right;"> 0.403 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:right;"> 0.009 </td>
   <td style="text-align:right;"> 0.008 </td>
   <td style="text-align:right;"> 1.069 </td>
   <td style="text-align:right;"> 0.773 </td>
   <td style="text-align:right;"> 4.510 </td>
   <td style="text-align:right;"> 0.993 </td>
   <td style="text-align:right;"> 0.113 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.004 </td>
   <td style="text-align:right;"> 0.626 </td>
   <td style="text-align:right;"> 1.057 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.998 </td>
   <td style="text-align:right;"> 0.893 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:right;"> 0.001 </td>
   <td style="text-align:right;"> 0.001 </td>
   <td style="text-align:right;"> 2.037 </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 0.639 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> NaN </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>



Table results Day 24


<table class="table table-striped table-hover" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>(\#tab:unnamed-chunk-36)SIMPER Analysis Results for Day 24: HW vs Control</caption>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> species </th>
   <th style="text-align:right;"> average </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> ratio </th>
   <th style="text-align:right;"> ava </th>
   <th style="text-align:right;"> avb </th>
   <th style="text-align:right;"> cumsum </th>
   <th style="text-align:right;"> p </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:right;"> 0.232 </td>
   <td style="text-align:right;"> 0.325 </td>
   <td style="text-align:right;"> 0.713 </td>
   <td style="text-align:right;"> 456.690 </td>
   <td style="text-align:right;"> 21.977 </td>
   <td style="text-align:right;"> 0.393 </td>
   <td style="text-align:right;"> 0.866 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:right;"> 0.152 </td>
   <td style="text-align:right;"> 0.151 </td>
   <td style="text-align:right;"> 1.008 </td>
   <td style="text-align:right;"> 80.832 </td>
   <td style="text-align:right;"> 125.624 </td>
   <td style="text-align:right;"> 0.652 </td>
   <td style="text-align:right;"> 0.740 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:right;"> 0.106 </td>
   <td style="text-align:right;"> 0.161 </td>
   <td style="text-align:right;"> 0.654 </td>
   <td style="text-align:right;"> 29.724 </td>
   <td style="text-align:right;"> 53.875 </td>
   <td style="text-align:right;"> 0.831 </td>
   <td style="text-align:right;"> 0.543 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:right;"> 0.049 </td>
   <td style="text-align:right;"> 0.050 </td>
   <td style="text-align:right;"> 0.990 </td>
   <td style="text-align:right;"> 6.142 </td>
   <td style="text-align:right;"> 23.099 </td>
   <td style="text-align:right;"> 0.915 </td>
   <td style="text-align:right;"> 0.078 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:right;"> 0.029 </td>
   <td style="text-align:right;"> 0.037 </td>
   <td style="text-align:right;"> 0.785 </td>
   <td style="text-align:right;"> 23.128 </td>
   <td style="text-align:right;"> 1.110 </td>
   <td style="text-align:right;"> 0.964 </td>
   <td style="text-align:right;"> 0.365 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:right;"> 0.019 </td>
   <td style="text-align:right;"> 0.011 </td>
   <td style="text-align:right;"> 1.748 </td>
   <td style="text-align:right;"> 21.166 </td>
   <td style="text-align:right;"> 4.900 </td>
   <td style="text-align:right;"> 0.996 </td>
   <td style="text-align:right;"> 0.459 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.966 </td>
   <td style="text-align:right;"> 1.106 </td>
   <td style="text-align:right;"> 0.848 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.619 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> NaN </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>



Table results Day 30


<table class="table table-striped table-hover" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>(\#tab:unnamed-chunk-38)SIMPER Analysis Results for Day 30: HW vs Control</caption>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> species </th>
   <th style="text-align:right;"> average </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> ratio </th>
   <th style="text-align:right;"> ava </th>
   <th style="text-align:right;"> avb </th>
   <th style="text-align:right;"> cumsum </th>
   <th style="text-align:right;"> p </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:right;"> 0.332 </td>
   <td style="text-align:right;"> 0.264 </td>
   <td style="text-align:right;"> 1.256 </td>
   <td style="text-align:right;"> 31.725 </td>
   <td style="text-align:right;"> 165.021 </td>
   <td style="text-align:right;"> 0.452 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:right;"> 0.180 </td>
   <td style="text-align:right;"> 0.169 </td>
   <td style="text-align:right;"> 1.066 </td>
   <td style="text-align:right;"> 41.734 </td>
   <td style="text-align:right;"> 99.096 </td>
   <td style="text-align:right;"> 0.697 </td>
   <td style="text-align:right;"> 0.933 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:right;"> 0.110 </td>
   <td style="text-align:right;"> 0.158 </td>
   <td style="text-align:right;"> 0.696 </td>
   <td style="text-align:right;"> 12.816 </td>
   <td style="text-align:right;"> 59.473 </td>
   <td style="text-align:right;"> 0.847 </td>
   <td style="text-align:right;"> 0.306 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:right;"> 0.095 </td>
   <td style="text-align:right;"> 0.090 </td>
   <td style="text-align:right;"> 1.055 </td>
   <td style="text-align:right;"> 2.670 </td>
   <td style="text-align:right;"> 53.407 </td>
   <td style="text-align:right;"> 0.976 </td>
   <td style="text-align:right;"> 0.058 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:right;"> 0.010 </td>
   <td style="text-align:right;"> 0.009 </td>
   <td style="text-align:right;"> 1.016 </td>
   <td style="text-align:right;"> 5.289 </td>
   <td style="text-align:right;"> 3.337 </td>
   <td style="text-align:right;"> 0.989 </td>
   <td style="text-align:right;"> 0.936 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:right;"> 0.006 </td>
   <td style="text-align:right;"> 0.005 </td>
   <td style="text-align:right;"> 1.127 </td>
   <td style="text-align:right;"> 0.250 </td>
   <td style="text-align:right;"> 3.758 </td>
   <td style="text-align:right;"> 0.998 </td>
   <td style="text-align:right;"> 0.113 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.519 </td>
   <td style="text-align:right;"> 0.835 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.971 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> NaN </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>



Table results Day 38


<table class="table table-striped table-hover" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
<caption>(\#tab:unnamed-chunk-40)SIMPER Analysis Results for Day 38: HW vs Control</caption>
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> species </th>
   <th style="text-align:right;"> average </th>
   <th style="text-align:right;"> sd </th>
   <th style="text-align:right;"> ratio </th>
   <th style="text-align:right;"> ava </th>
   <th style="text-align:right;"> avb </th>
   <th style="text-align:right;"> cumsum </th>
   <th style="text-align:right;"> p </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:left;"> Cryptophyta </td>
   <td style="text-align:right;"> 0.230 </td>
   <td style="text-align:right;"> 0.162 </td>
   <td style="text-align:right;"> 1.420 </td>
   <td style="text-align:right;"> 4.567 </td>
   <td style="text-align:right;"> 100.140 </td>
   <td style="text-align:right;"> 0.304 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:left;"> Dinophyta </td>
   <td style="text-align:right;"> 0.173 </td>
   <td style="text-align:right;"> 0.194 </td>
   <td style="text-align:right;"> 0.895 </td>
   <td style="text-align:right;"> 3.471 </td>
   <td style="text-align:right;"> 167.298 </td>
   <td style="text-align:right;"> 0.533 </td>
   <td style="text-align:right;"> 0.147 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:left;"> Chlorophyta </td>
   <td style="text-align:right;"> 0.130 </td>
   <td style="text-align:right;"> 0.166 </td>
   <td style="text-align:right;"> 0.783 </td>
   <td style="text-align:right;"> 3.894 </td>
   <td style="text-align:right;"> 80.553 </td>
   <td style="text-align:right;"> 0.704 </td>
   <td style="text-align:right;"> 0.039 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:left;"> Charophyta </td>
   <td style="text-align:right;"> 0.127 </td>
   <td style="text-align:right;"> 0.055 </td>
   <td style="text-align:right;"> 2.308 </td>
   <td style="text-align:right;"> 32.507 </td>
   <td style="text-align:right;"> 93.918 </td>
   <td style="text-align:right;"> 0.872 </td>
   <td style="text-align:right;"> 0.967 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:left;"> Bacillariophyta </td>
   <td style="text-align:right;"> 0.059 </td>
   <td style="text-align:right;"> 0.047 </td>
   <td style="text-align:right;"> 1.260 </td>
   <td style="text-align:right;"> 11.421 </td>
   <td style="text-align:right;"> 31.128 </td>
   <td style="text-align:right;"> 0.950 </td>
   <td style="text-align:right;"> 0.429 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:left;"> Cyanobacteria </td>
   <td style="text-align:right;"> 0.027 </td>
   <td style="text-align:right;"> 0.024 </td>
   <td style="text-align:right;"> 1.147 </td>
   <td style="text-align:right;"> 5.863 </td>
   <td style="text-align:right;"> 14.455 </td>
   <td style="text-align:right;"> 0.986 </td>
   <td style="text-align:right;"> 0.967 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:left;"> Euglenophyta </td>
   <td style="text-align:right;"> 0.011 </td>
   <td style="text-align:right;"> 0.010 </td>
   <td style="text-align:right;"> 1.004 </td>
   <td style="text-align:right;"> 5.281 </td>
   <td style="text-align:right;"> 3.097 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.929 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:left;"> Synurophyta </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> NaN </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 0.000 </td>
   <td style="text-align:right;"> 1.000 </td>
   <td style="text-align:right;"> 0.001 </td>
  </tr>
</tbody>
</table>






### NMDS plot
Not sure if this makes sense, as the change in relative biomass plot looks much nicer
<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/composition_plot_NMDS-1.png" alt="Non-Metric Multidimensional Scaling plot of compositional dynamics over time."  />
<p class="caption">(\#fig:composition_plot_NMDS)Non-Metric Multidimensional Scaling plot of compositional dynamics over time.</p>
</div>



## Zooplankton

<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/bio_plot_zoo-1.png" alt="Zooplankton biomass dynamics over time. The red areas show the three heatwaves"  />
<p class="caption">(\#fig:bio_plot_zoo)Zooplankton biomass dynamics over time. The red areas show the three heatwaves</p>
</div>

Creating model for zoo biomass

``` r
dd_zoo_model <- dd_zoo_long %>% 
  group_by(Mesocosm.No, Treatment, Day) %>%
  summarize(total = sum(biomass)) %>%
  ungroup()
model_zoo_bio <- lmer(log10(total +1) ~ Treatment * Day + (1 | Mesocosm.No), data = dd_zoo_model)
```

<table class="table" style="color: black; width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:left;"> effect </th>
   <th style="text-align:left;"> group </th>
   <th style="text-align:left;"> term </th>
   <th style="text-align:right;"> estimate </th>
   <th style="text-align:right;"> std.error </th>
   <th style="text-align:right;"> statistic </th>
   <th style="text-align:right;"> df </th>
   <th style="text-align:right;"> p.value </th>
   <th style="text-align:right;"> 2.5% </th>
   <th style="text-align:right;"> 97.5% </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:right;"> 0.142 </td>
   <td style="text-align:right;"> 0.048 </td>
   <td style="text-align:right;"> 2.928 </td>
   <td style="text-align:right;"> 28 </td>
   <td style="text-align:right;"> 0.007 </td>
   <td style="text-align:right;"> 0.050 </td>
   <td style="text-align:right;"> 0.234 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW </td>
   <td style="text-align:right;"> -0.029 </td>
   <td style="text-align:right;"> 0.069 </td>
   <td style="text-align:right;"> -0.419 </td>
   <td style="text-align:right;"> 28 </td>
   <td style="text-align:right;"> 0.678 </td>
   <td style="text-align:right;"> -0.158 </td>
   <td style="text-align:right;"> 0.101 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> Day </td>
   <td style="text-align:right;"> 0.006 </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 2.859 </td>
   <td style="text-align:right;"> 28 </td>
   <td style="text-align:right;"> 0.008 </td>
   <td style="text-align:right;"> 0.002 </td>
   <td style="text-align:right;"> 0.010 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:left;"> fixed </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> TreatmentHW:Day </td>
   <td style="text-align:right;"> 0.001 </td>
   <td style="text-align:right;"> 0.003 </td>
   <td style="text-align:right;"> 0.235 </td>
   <td style="text-align:right;"> 28 </td>
   <td style="text-align:right;"> 0.816 </td>
   <td style="text-align:right;"> -0.005 </td>
   <td style="text-align:right;"> 0.006 </td>
  </tr>
</tbody>
</table>










### Relative biomass 

Let's have a look at how different taxonomic groups of zooplankton change over time in terms of relative biomass 

<div class="figure" style="text-align: center">
<img src="Slowing_down_v2_files/figure-html/relative_bio_zoo_plot-1.png" alt="Change in relative biomass of zooplankton groups over time in the control and heatwave treatment"  />
<p class="caption">(\#fig:relative_bio_zoo_plot)Change in relative biomass of zooplankton groups over time in the control and heatwave treatment</p>
</div>



![](Slowing_down_v2_files/figure-html/unnamed-chunk-47-1.png)<!-- -->

