---
title: "From Animations To Science"
class_no: 6
class_date: "Thurs. January 25"
qrimage: qrcode.png
qrbottom: '-90%'
pageurl: "ees4760.jgilligan.org/Slides/Class_06"
pdfurl: "ees4760.jgilligan.org/Slides/Class_06/EES_4760_5760_Class_06_Slides.pdf"
course      : "EES 4760/5760"
course_name : "Agent-Based & Individual-Based Computational Modeling"
author      : "Jonathan Gilligan"
semester    : Spring
year        : 2018
output:
  revealjs.jg::revealjs_presentation
---

## Starting Up: {#start-up .ninety}

Download the following files<br/>
(see [download page](/downloads/butterfly_terrain/) at <https://ees4760.jgilligan.org/downloads/butterfly_terrain/>):

* A [butterfly model](/models/class_06/butterfly_class_06a.nlogo) 
  from Chapter 5:<br/>
  <https://ees4760.jgilligan.org/models/class_06/butterfly_class_06a.nlogo>

* A [version of the butterfly model](/models/class_06/butterfly_class_06b.nlogo) 
  with modifications:<br/>
  <https://ees4760.jgilligan.org/models/class_06/butterfly_class_06b.nlogo>

* Versions of the butterfly model with code for testing:<br/>
  <https://ees4760.jgilligan.org/models/class_06/butterfly_class_06c.nlogo> 
  and 
  <https://ees4760.jgilligan.org/models/class_06/butterfly_class_06c_testing.nlogo> 

* The NetLogo "[Testing Is Fun](/models/class_06/jg-tif.nls)" library<br/>
  <https://ees4760.jgilligan.org/models/class_06/jg-tif.nls>

* A [digital elevation map](/models/class_06/ElevationData.txt) of real hills<br/>
  <https://ees4760.jgilligan.org/models/class_06/ElevationData.txt>

* Start NetLogo and load 
  [`butterfly_class_06a.nlogo`](/models/class_06/butterfly_class_06a.nlogo)

# Projects {#project-sec data-transition="fade-out" data-state="skip_slide"}

## Planning {#projects .eighty data-transition="fade-in"}

* Absence:
    * I will miss class Feb. 8, Mar. 13--15, and Apr. 10--12. 
      * I will schedule make-up sessions for the classes I miss.

* Semester Project:
    * Fri. Feb. 9: Pick a model from one of the open-source 
      repositories, or NetLogo "model library" that you want to work with.
      * One-page description of model and thoughts for extending it (post to Box)
    * Feb. 22: Examine ODD and code of your chosen model.
      * Short write-up of how model works and output from running it
    * Fri. Mar. 16: ODD for extending model
    * Apr. 17-19: Presentations on experiments with extended models
    * Apr. 24: Write-up of research project (around 10 pages)

* Team Project:
    * Each team (2--3 students) will code a model from an ODD in the textbook (Ch. 10 or Ch. 13)
    * Use model to do exercises from book
    * Make presentation about what you learned (Tues. Feb. 27)

* Detailed Assignments on Brightspace

# Experiments with the Butterfly Model {#butterfly-sec}

## Plot Corridor Width

* On the interface tab, add a plot

  ![plot dialog box](assets/images/plot_dlg.png){height=600}

* On the code tab, add a line to `go` to plot the corridor width

  ```
  plot corridor-width
  ```

## Enhance Interface

* Add a button to export the plot to a file:
  ```
  export-plot "Corridor-width" (word "corridor-output-for-q-" (precision q 2) ".csv")               
  ```

* Add a button to increment _q_ by 0.1

## BehaviorSpace {#behaviorspace .ninety}

* If your model is having problems, compare it to `butterfly_class_06b.nlogo`

* Open BehaviorSpace and create an experiment
  * Call it `experiment`
  * Vary `real-terrain` between `false` and `true`
  * Vary `q` from 0 to 1 in steps of 0.2
  * Run 20 repetitions for each value of _q_.
  * Measure `corridor-width` at the last tick only
  * Set time limit to 0 to let model run until it stops
* Run BehaviorSpace experiment
  * Save "table" output
  * Speed things up by unchecking "Update view" and "Update plots and monitors"
* Open the [analyzeBehaviorspace app](https://analyze-behaviorspace.jgilligan.org) 
  at 
  <https://analyze-behaviorspace.jgilligan.org><br/>
  and use it to compare the relationship between corridor width and _q_ for each terrain

# Practice {#practice-sec data-transition="fade-out" data-state="skip_slide"}

## Practice {#practice data-transition="fade-in"}

* Work together with a partner
* Add a button to erase the tracks of the turtles (Exercise 5.2)
* Using the realistic terrain, play with _q_ and see what values do best at 
  helping butterflies find mates near hilltops.

# Testing {#testing-sec data-transition="fade-out" data-state="skip_slide"}

## Testing Models {#testing-models .ninety data-transition="fade-in"}

* Using monitors
* Unit testing resource "Testing Is Fun"
  * Open "`butterfly_class_06a_testing.nlogo`"
  * At beginning of code:
    ```
    __includes ["jg-tif.nls"]
    ```
  * In `to_setup` add:
    ```
    initialize-tests
    ```
  * In `to go` add:
    ```
    set-context "Reporting corridor-width"
    test-that "# visited patches should equal # yellow patches"  
    expect-that (count patches with [visited?]) equals (count patches with [pcolor = yellow])            
    ...
    if ticks >= 1000 or all? turtles [finished?]
    [
      resume-all-tests
      stop
    ]
    ```

# Emergence {#emergence-sec data-transition="fade-out" data-state="skip_slide"}

## Emergence {#emergence data-transition="fade-in"}

* A tricky concept
* Early definition: _"stable macroscopic patterns arising from the local interaction of agents"_ --- Joshua Epstein, 1996
* Epstein ten years later: _"I have always been uncomfortable with the vagueness and occasional mysticism surrounding this word."_
* Epstein now prefers to talk about _"__Generative__ Social Science"_
* Other scientists (especially in natural sciences: biology, physics, etc.) are more comfortable talking about _emergence_.