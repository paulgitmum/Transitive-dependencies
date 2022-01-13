# Transitive-dependencies

### What are transitive dependencies ?
A component may have two different kinds of dependencies
 1. Direct dependencies 
 -<i>  are directly required by the component. A direct dependency is also referred to as a first level dependency </i>
 2. Transitive dependencies 
  -<i>  dependencies that your component needs, but only because another dependency needs them. </i>
           
### How to Upgrading versions of transitive dependencies ? 
- Direct dependencies can be upgraded to the required version with just a simple command line process <i> 'npm update@dependency-name' </i>. 
- But in the case of transitive dependencies, you may use <i> 'npm-force-resolutions' </i> method or come up with some work around strategy to upgrade them to required version.

### Using npm-force-resolutions strategy
How to use
- Step 1: Add a field resolutions with the dependency version you want to fix to your package.json, for example:

       "resolutions": 
                     {
                        "hoek": "4.2.1"
                     } 
- Step 2: add npm-force-resolutions to the preinstall script so that it patches the package-lock file before every npm install you run:

        "scripts":
                  {
                       "preinstall": "npx npm-force-resolutions"
                  }
                  
 - Step 3: then 

                 npm install               
                 
  - Final step: Confirm that the right version was installed, 

                npm ls hoek
            
