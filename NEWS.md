# CHANGES IN FLCore VERSION 2.6

## NEW FEATURES
- FLModelSim and FLModelSims new classes
- [<- FLArray now accepts an input FLQuant and keeps the structure, still recyling as appropriate.
- New FLStockLen class for length-based stock data and results.
- New tS and tS<- method to extract and replace individual time steps in an object with
  years and seasons
- tsp method for FLQuant returns 'tsp' attribute: start, end and frequency (seasons)
- Arith method for FLQuant is now unit-aware, see ?units
- wireframe method from lattice now available for FLQuant
- [ method for FLQuantDistr
- FLIndexBiomass class for biomass-based indices of abundance.

## USER-VISIBLE CHANGES
- model.frame(FLComp) now has an mcf=TRUE argument to correct slots of different dim
- computeLogLik method added to FLModel. Will return a logLik object calculated with the data and params in the object
- New iterMedians(FLQuant) method to applky median along iter dim
- coerce method for data.frame to FLPar now assumes a 2D structure with iters as rows and params as columns
- rlnorm(FLPar, ...) and rnorm(FLPar, ...) now available
- mvrnorm(numeric, FLQuant) and mvrnorm(numeric, FLQuant, matrix) now available
- propagate(FLComp) now propagates FLPar slots as well
- FLFleet, FLMetier and FLCatch classes (plus their plurals) and methods have been moved to the FLFleet package
- ifelse has now been definedx for test="FLQuant"
- as.data.frame for FLQuant(s) and FLComp now has an option cohort=FALSE to return a column named cohort, calculated as year-age. Ony for age-quanted objects
- getPlural is now an S4 method dispatching on singular classes and returning the name of the corresponding FLlst-based class
- as.data.frame(FLQuants) returns qname as factor with levels in the order of the input object
- modified quantile(FLQuant) so dimnames in iter follow quantile(array), e.g. 50%
- tail method for FLQuant, operates by default along the year dimension.
- deprecated sr function is now a method to return aligned stock/recruits FLQuants from an FLStock
- propagate(FLComp) accepts extending an object to existing nu mber of iters for all other slots of length 1.
- trim(FLS) u[pdates min/maxfbar if needed
- transform(FLComp) now accepts a named FLQuants object as substitution argument (...)
- FLQuants() now accepts an FLCOMP object and a list of names/functions to be used to extract individual FLQuant(s)
- FLPar validity now checks that content is numeric. Default frist dimname is now 'params'
- FLIndices class can take both FLIndex and FLIndexBiomass objects

## BUG FIXES
- iterMeans(FLQuant) was not operating along the 6th dim
- coerce from FLPar to data.frame now works as expected
- Added check for range names to FLComp class validity. Elements must be named with non-empty strings and contain, at least, min, max, minyear and maxyear
- coerce from data.frame to FLPar now handles correctly iters
- apply(FLArray) did not keep the object units
- rnorm, rlnorm and rpois did not keep tje object units
- code2name for FLSR did not reocngize properly bevholtSV
- fmle() can now use method="Brent" for one parameter problems
- New ple4.biol with data up to 2008. No integer value
- prototype object for FLComp VIRTUAl class has name as character(1)
- as.FLQuant(df) failed on objects with no 'year' column
- propagate(FLQuant) now accepts iter == dim[6]
- Faulty comparison in expand(FLArray) fixed #7
- Wrong test in validity for FLModelSim
- Fixed bug in FLPar %% FLPar when objects were actually equal in dims, always returned product
- quantile(FLQuant) returned oject with wrong dimensions

## UTILITIES

## DOCUMENTATION

## DEPRECATED & DEFUNCT
- FLFleet, FLMetier and FLCatch classes (plus their plurals) and methods have been moved to the FLFleet package
