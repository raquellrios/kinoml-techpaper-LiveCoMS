# Pending tasks for this milestone

## Manuscript

- [ ] Agree on the story we want to tell
- [ ] Figures
- [ ] Content itself (might be already written, but rearrangement needed?)

JRG proposes a story line based on these key ideas:

- The MAIN idea: We want to build great models that use complex structural information and even free energies. Assessing that they are indeed great requires reproducible comparisons of increasingly sophisticated models against baselines. Reproducibility is the main issue here: building a framework that will allow for this by design. This needs:
  - Ensure the raw and 'cleaned' data is permanently accessible, long-term (KinoData)
    * https://github.com/openkinome/kinodata/blob/master/kinase-bioactivities-in-chembl/kinase-bioactivities-in-chembl.ipynb
    * https://github.com/openkinome/kinodata/releases 
  - Funnel the different types of data and formats into a unified object model (KinoML)
  - Featurize the objects into their tensorial representations using reproducible workflows that log everything. (experiments-binding-affinity)
  - Store tensors in disk for long-term archival. (experiments-binding-affinity)
  - ML models, defined in the KinoML library, are trained with platform-agnostic tensors from disk (Parquet files). (experiments-binding-affinity)
  - The featurization and training notebooks are based on templates, so the same structure can be used across different tensors / models. This is flexible to an extent. They also serve as reports, with annotated versions, seeds and other metadata needed for reproducibility. (experiments-binding-affinity)


- Journey from raw data to ML models (applied to kinase polypharmacology) - lessons learned

Stages of the journey -> diagram :
(0) (JDC/AV) Why do we need this?
    - We want to build great models that use complex structural information and even free energies. 
    - Assessing that they are indeed great requires reproducible comparisons of increasingly sophisticated models against baselines. 
    - Reproducibility is the main issue here: building a framework that will allow for this by design. 
(1) (AV/JRG) Data sources
    - Desiderata: what we hoped for but didn't find :)
        - large, homogeneous data sets ...
    - Which datasets can we find - have the highest value - in the context of kinase pharmacology? ChEMBL, PKIS2/KinomeScan
    - Pitfalls
    - Our approach/how did we engineer it to overcome the pitfalls: assign identifiers to versions, cleaning/filtering using state-of-the-art pipelines/advice

(2) (JRG/JDC/TK) Harmonized / combined measurement types and molecular representations
    - Desiderata: measurements would contain the same information and easy to be combine 
    - Use biophysical modelling
    - Pitfalls: different thresholds, proxy magnitudes are not directly comparable
    - Approach: observation and likelihood models -> describe object model

(3) (JRG/TK) Featurization 
    - Desiderata: framework-agnostic tensorial data that can be serialized to disk for (A) archival, (B) compatibility with ML frameworks
    - ...
    - Pitfalls: different kinds of models have different shape requirements, which affect the file format on disk and how they are ingested in the ML model.
    - Approach: review most interesting featurization for ligand/kinase/complex.

(3.5) (JRG/TK) Taking tensors to the ML framework
    - Desiderata: it just works natively
    - Pitfalls: it doesn't 
    - Approach: adapters and interfaces on KinoML
    
(4) (JRG) Reproducible learning
    - Desiderata: All studies can be re-run at any point in the future and results are the same
    - Pitfalls: Raw data, cleaning data, and featurization schemes need to be stable
    - Approach: Notebooks with tons of logging, automation, adapter to ML framework (pytorch , ...) 

## Journals
* https://www.livecomsjournal.org/
* -> 1-page summary for the journal (tutorial to best practices) by Fri. 9.7 ?
* other options
    - JCIM, JCheminf, ...
   --https://www.journals.elsevier.com/artificial-intelligence-in-the-life-sciences


-----------------

## Code

AFAIK, there were a couple rough edges here and there when I left, but I don't know if the team has ironed those out in the meantime? Open issues are [here](https://github.com/openkinome/kinoml/issues) and [here](https://github.com/openkinome/experiments-binding-affinity/issues). It would be useful to have the team write down their "wish list" or pain points here.

- [ ]
- [ ]


## Docs

This could use some work, honestly.

- [ ] No narrative documentation. The overview of the OpenKinome project is basically this manuscript, but we might need something else in the KinoML docs for context.
- [ ] Some key subpackages lack a top-module docstring that introduces the purpose of that namespace (e.g. `kinoml.core` should introduce the reader to the object model).
- [ ] Tutorials. Adapt the content from the workshop homework in the form of a notebook as an introduction to the different topics.