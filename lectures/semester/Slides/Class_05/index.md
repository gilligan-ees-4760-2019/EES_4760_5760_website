---
title: "Your First Model"
class_no: 5
class_date: "Tues. January 23"
qrimage: qrcode.png
qrbottom: '-90%'
pageurl: "ees4760.jgilligan.org/Slides/Class_05"
pdfurl: "ees4760.jgilligan.org/Slides/Class_05/EES_4760_5760_Class_05_Slides.pdf"
course      : "EES 4760/5760"
course_name : "Agent-Based & Individual-Based Computational Modeling"
author      : "Jonathan Gilligan"
semester    : Spring
year        : 2018
output:
  revealjs.jg::revealjs_presentation
---

# Homework {#homework-sec data-transition="fade-out" data-state="skip_slide"}

## Homework: {#homework data-transition="fade-in"}

> * In the mushroom hunt, were there always 80 red patches?
> * Any questions about modified mushroom hunt model?
> * Let's talk about ODD exercise.

## Writing a model from an ODD {#model-from-odd}

> * Questions about writing a model from Butterfly ODD?
> * Were there things the ODD was unclear about?

# Digression on Turtles

## Why "Turtles"?

::: {.fragment}

![Original Turtle](assets/images/Papert-Turtle-x640.jpg){style="height:900px;"}
![Seymour Papert](assets/images/Papert-x640.jpg){style="height:900px;"}

:::

# Butterfly Model {#butterfly-sec data-transition="fade-out" data-state="skip_slide"}

## Enhancing the Butterfly model {#butterfly .ninety .leftlist data-transition="fade"}

> * Download butterfly model from <https://ees4760.jgilligan.org/models/class_05/butterfly_model_class_5.nlogo>
> * Put a slider for *q*
> * Add patches-own variable to indicate whether it was visited.

::: {.fragment .fade-in style="max-height:100%;"}
```
patches-own
[ 
  elevation 
  visited? ; question mark means it's a true/false variable
]

to setup
[
  ...
  ask patches [
    set visited? false
    ...
    ]
  ...
]
```
:::
    

##  Enhancing the Butterfly model {#butterfly-2 .leftlist data-transition="fade"}

<ul>
<li>
Put a slider for *q*
</li><li>
Add patches-own variable to indicate whether it was visited.
</li><li class="fragment fade-in">
Add turtles-own variable to remember the patch where it started.
</li><li class="fragment fade-in">
Increase the number of butterflies to 50.
</li><li class="fragment fade-in">
Stop butterfly from moving if it's at the top of a  hill.
<ul><li class="fragment fade-in">
How can you tell whether it's on the top?
</li></ul>
</li>
</ul>

## Enhancing the Butterfly model {#butterfly-3 data-transition="fade-in"}

> * Write a reporter for corridor width<br/>
    <div style="border-top:20px;border-bottom:20px;">
    \[ \text{Corridor width} = \frac{\text{# patches visited}}{\text{distance from start}} \]
    </div>
>  * Put an **observer** on the interface
>  * Define a reporter:


. . .


```
to-report corridor-width
  let wid ... ; calculate corridor width
  report wid
end
```

# Behaviorspace {#behaviorspace-sec data-transition="fade-out" data-state="skip_slide"}

## Running Experiments: BehaviorSpace {#behaviorspace data-transition="fade-in"}

> * Vary any parameter that has a control on the model's interface
> * Writes output to `.csv` spreadsheet file (table output is the most useful).
>   
>   ![Behaviorspace experiment](assets/images/behaviorspace_expt.png){style="height:800px;"}


## Output from BehaviorSpace Experiments {#behaviorspace-output}

> * Note: Data written in spreadsheet might be out of order.
>
>   ::: {.stretch}
    ```
    "BehaviorSpace results (NetLogo 5.3.1)"
    "jg_butterfly_1.nlogo"
    "vary-q"
    "01/25/2016 23:08:47:963 -0600"
    "min-pxcor","max-pxcor","min-pycor","max-pycor"
    "0","149","0","149"
    "[run number]","q","[step]","corridor-width"
    "4","0","999","424.71585264477375"
    "3","0","999","407.8948972331853"
    "2","0","999","402.16008464319225"
    "1","0","999","413.09183879201066"
    "5","0","999","380.4175502215263"
    "6","0","999","408.25117143183326"
    "7","0","999","431.37461560574894"
    "8","0","999","408.38259535508286"
    "9","0","999","421.7254402334981"
    ```
    :::

## Analyzing Behaviorspace Output {#analyzing-behaviorspace}

> * Behaviorspace output format is annoying
>   * Each line is some tick of some run
>   * How to organize, and average over runs?
> * analyzeBehaviorspace app
>   * Works with Behaviorspace **table** output format.
>   * <https://analyze-behaviorspace.jgilligan.org>
>   * Or install on your own computer using R
>     * Instructions at <https://github.com/jonathan-g/analyzeBehaviorspace>
>     * After installing:

. . .

```
library(analyzeBehaviorspace)
launch_abs()
```

# Emergence {#emergence-sec data-transition="fade-out" data-state="skip_slide"}

## Emergence {#emergence data-transition="fade-in"}

> * A tricky concept.
> * *Growing Artificial Societies:* "stable macroscopic patterns arising from the local interaction of agents."
> * Epstein ten years later: "I have always been uncomfortable with the vagueness and occasional mysticism surrounding this word."
> * Epstein now prefers to talk about "_Generative_ Social Science"