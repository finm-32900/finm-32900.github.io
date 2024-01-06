What is Data Science? Where does this course fit in? 
======================================================

## The Two-Fold Objective Of This Course

The two objectives of this course are based on definition of "Data Science."

1.	**The "Science" in Data Science.** Teach a core set of software tools and principles behind creating modern data analytic workflows that are reproducible and scalable from end to end. The idea is that this set of computational tools will serve as a technical foundation for any subfield of data science that the student wishes to pursue. This is born out of the idea that reproducibility is fundamental to good science.
2.	**The "Data" in Data Science.** Give students hands-on experience with a series of important and commonly used financial data sets and/or sources, including CRSP, Compustat, FRED, BEA data, FINRA TRACE, TreasuryDirect, EDGAR, and NYSE TAQ. Not only does each data set require some degree of domain specific knowledge (e.g., to clean and interpret properly), but each data set also poses different computational challenges to use effectively. For example, using EDGAR means working with large amounts of unstructured text or data from NYSE TAQ involves learning to work with big data (approximately 100 GBs per day). Each case study is designed to give students the basic knowledge and tools to use these data sets effectively.

Now, I recognize that the term "data science" is a broad term and that the field has a wide scope. Given this, this course focuses on a common skill set across various data science subfields. In my opinion, this core set of skills arises from the definition of "data science." That is, this core set of skills are those that make up the elements of the analytical pipeline: from data extraction and cleaning to exploratory analysis, visualization, and modeling, and finally, publication and deployment. This course aims to teach the tools and principles behind creating reproducible and scalable workflows, including build automation, dependency management, unit testing, the command-line environment, shell scripting, Git for version control, and GitHub for team collaboration. Furthermore, given that this course is aimed towards students studying quantitative finance, these tools are taught through a series of case studies that are designed to give students practical experience with key financial data sets and sources, such as CRSP and Compustat for pricing and financials, macroeconomic data from FRED and the BEA, bond transactions from FINRA TRACE, Treasury auction data from TreasuryDirect, textual data from EDGAR, and high-frequency trade and quote data from NYSE. 


## What is Data Science?

Given the increasing complexity of the computational sciences, the ability to produce readable, reusable, and reproducible code and analyses is increasingly important in order to produce good science and to add value within an organization. Recognizing that data science is a broad term encompassing many fields, this course introduces a core set of practical tools and techniques common to all subfields of data science as they are used within quantitative finance, with a special emphasis on those necessary to build behind creating reproducible and scalable workflows (e.g., reproducible analytical pipelines). 

A common characterization of data science describes it as a combination of coding/computer skills, mathematics and statistics, and domain specific knowledge (see the following figure). 

!["The Data Science Venn Diagram", by Drew Conway](assets/data_science_venn_diagram.png)


These computer skills, colloquially referred to as "hacking skills," are called such because they refer to skills that are often not taught in a traditional computer science curriculum. A computer science curriculum might include theoretical courses on algorithms, operating systems, or programming languages, whereas the practical skills related to the computing ecosystem---the command-line environment, shell scripting, data wrangling and visualization, or version control---are often left to the individual to learn on their own. (This was even the motivation for a supplementary CS course at MIT, ["The Missing Semester of Your CS Education."](https://missing.csail.mit.edu/)) In this course, I provide a structured overview of these important tools and demonstrate, by example, how they can be used to (1) collect, clean, and analyze economic and financial data; (2) facilitate collaboration among groups of researchers; and (3) to create analyses that are easy for outside users to reproduce. All of the examples and/or case studies used to illustrate these concepts and to teach these tools come from common tasks or applications within quantitative finance, including data wrangling, feature engineering, time series forecasting, performance evaluation, portfolio optimization, back testing, and reporting results. 

### An Aside On The Data Science And This History Of Science

The concept of reproducibility has been a cornerstone in the development of the scientific method and, by extension, the broader history of science. Reproducibility refers to the ability of an experiment or study to be repeated with similar results by different researchers, using the same methods under the same conditions. This principle is crucial for validating the reliability and universality of scientific findings.

As an example, consider the accomplishments of the historical astronomer Galileo Galilei. Galileo's work exemplifies how reproducible findings are fundamental for advancing scientific knowledge and challenging established theories.
In the early 17th century, Galileo improved the design of the telescope and made astronomical observations that challenged the prevailing geocentric model, which placed the Earth at the center of the universe. He observed, among other things, the moons of Jupiter and the phases of Venus. These observations were reproducible in the sense that other scientists could and did construct similar telescopes to see the same phenomena. This reproducibility was crucial for the acceptance of the heliocentric model, which posits the Sun at the center of the solar system. 


```{admonition} Discussion
:class: tip 
What are ways in which principles of reproducibility in the hard sciences might be reflected in data science?
```

## Principles of Reproducibility and Data Science

- **The Scientific Revolution**: The 17th century's Scientific Revolution further solidified reproducibility as a scientific norm. The works of scientists like Kepler, Galileo, and Newton were often replicated by their contemporaries, which helped establish the credibility of their findings. In data science, our work gains more credibility when it is easy to reproduce, given the right resources.

- **Standardization of Methods**: The 20th century also saw the development of standardized methods and protocols in various scientific fields, which further reinforced the reproducibility of experiments. In data science, we want to adopt the common state-of-the art software tools used by other data scientist for ease of communication and reproducibility. 

- **Reliability of Results**: Reproducibility ensures that scientific findings are not the result of chance, bias, or unique conditions. It is a test of the validity of the findings.

- **Scientific Progress**: Science advances by building on previous work. Reproducibility allows subsequent scientists to rely on existing findings as they push the boundaries of knowledge. As an example, the open source movement facilitates scientific progress by making research methods, data, and tools publicly accessible, allowing scientists to easily replicate and build upon previous work. This transparency and availability of resources enhance the reproducibility and reliability of scientific findings, accelerating the advancement of knowledge. For example, you will find many projects available as open source projects on GitHub. The open science movement, as an example, emphasizes transparency, open access to data and methods, and collaborative research, partly as a response to reproducibility issues.

```{seealso} 
As an example, see the ["Open Source Asset Pricing"](https://www.openassetpricing.com/) project on GitHub: https://github.com/OpenSourceAP/CrossSection/
```

- **Reproducibility Crisis**: Recently, various fields, especially in psychology and biomedical sciences, have faced a "reproducibility crisis." This has led to increased scrutiny of experimental methods and statistical practices. 


```{admonition} Discussion
:class: tip 
Finance, unlike fields like Psychology, do not rely on clinical experiments. It relies on data that is, to a large degree, open to anyone to use. Would we expect there to be a reproducibility crisis in finance, given that everybody is using the same data? We will explore this in more depth shortly.
```
