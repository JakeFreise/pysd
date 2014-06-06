PySD
====

System Dynamics Modeling in Python

This project will create simple library for running [System Dynamics](http://en.wikipedia.org/wiki/System_dynamics) models in python, with the purpose of improving integration of 'Big Data' into the SD workflow. 

## Why create a new SD modeling engine?

There are a number of great SD programs out there ([Vensim](http://vensim.com/), [iThink](http://www.iseesystems.com/Softwares/Business/ithinkSoftware.aspx), [AnyLogic](http://www.anylogic.com/system-dynamics), [Insight Maker](http://insightmaker.com/), [Forio](http://forio.com/), and [others](http://en.wikipedia.org/wiki/List_of_system_dynamics_software)). Additionally, there are a number of existing python-based dynamic system modeling tools, such as [PyDSTool](http://www.ni.gsu.edu/~rclewley/PyDSTool/FrontPage.html) and [others](http://www.scipy.org/topical-software.html#dynamical-systems). In order not to waste our effort, or fall victim to the [Not-Invented-Here](http://en.wikipedia.org/wiki/Not_invented_here) fallacy, we should have a very good reason for starting a new project. 

That reason is this: There is a whole world of computational tools being developed in the larger technical community. **We should directly use the tools that other people are building, instead of replicating their functionality in SD specific software.** The best way to do this is to bring specific SD functionality to the domain where those other tools are being developed. 

The major benefit of this approach is that SD modelers will be able to take advantage of all the most recent developments in data science, and will be able to focus our efforts on improving the part of the stack that is unique to System Dynamics modeling.

#### What other tools are we talking about?

System dynamics and other programming and analysis techniques share a need for some common components:

Data components:

1. Data Gathering - possibly in real time, from web sources
2. Data Storage - potentially in distributed, cloud based databases
4. Data formatting, verification, transformation, 
5. Timeseries Data interpolation and alignment
5. Geographic Data Manipulation

Computational components:

1. High speed numerical integration - gpu techniques, etc
2. Multiprocessing - possibly distributed, cloud based parallel computing
7. Statistical analysis / inference
8. Machine Learning algorithms / Neural Networks / AI
9. Optimization Techniques

Display components:

1. Real-time data visualization 
2. Interactive data visualization - possibly web based, at scale
3. Theory/Documentation/Code/Result colocation

Collaboration components:

1. Real-time collaboration
2. Version Control
4. Open Sourcing/Archiving
3. Analysis Replicability - improving research replicating

The Future...

#### What components are specific to System Dynamics?

1. System Dynamics Model Equations
3. System Dynamics Model Diagrams - Stock and Flow, CLD
3. Advanced SD concepts - Coflows, Aging Chains, etc.
5. Units and bounds checking
4. Future Developments in SD modeling (Stochastic Sims?)

These are the components that will be included in PySD.


## Notional Capabilities Development Pathway

####Version 0:
1. Read [xmile](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=xmile) format models
2. Run model over arbitrary timescales, including single steps
4. Output to [pandas](http://pandas.pydata.org/)
3. Modify parameters

####Version 1:

2. Input SD model components in a natural, code-based way
3. Write xmile in order to save models
1. Display SD model diagrams

####Version 2:

4. Check model units
1. Value limit checking (ie, chicken population only valid on integers $0\rightarrow \infty$

####Version 3:

1. Modify locations of SD model diagram components using click-drag, save those modifications
2. Run Stochastic Models
3. High Performance Computing Support

####Someday/Maybe

- Manage varying the time step of integration/adaptive integration time step
- Infer logical ways to automatically lay out stock and flow diagrams
- Add hooks to vensim, other SD programs, to allow running models with other engines
- Turn off and on 'traces' or records of the values of variables
- Show different 'submodels' in the model diagram
- Infer units when possible from other areas
- Hover over stock/flow elements to get things like units, descriptions, values, etc.
- Output DataFrame including tags for units



## PySD Design Philosophy

- Do as little as possible. 
Anything that is not endemic to System Dynamics (such as plotting, integration, fitting, etc) should either be implemented using external tools, or omitted. Let other disciplines (ABM, Discrete Event Simulation, etc) create their own tools.
- Use the language of system dynamics.
- Be simple to use. Let SD practitioners who haven't used python before understand the basics.
- Take advantage of general python constructions. For instance, if we want to disaggregate by grade, we should be able to do something like: ` students = [sd.Stock(name='Grade%02i'%grade) for grade in range(1,13)]`
- Be simple to maintain.    
