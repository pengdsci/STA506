---
title: "Assignment 8: Bootstrap Methods and Applications"
author: "Your Name "
date: " Due: "
output:
  word_document: 
    toc: yes
    toc_depth: 4
    fig_caption: yes
    keep_md: yes
  html_document: 
    toc: yes
    toc_depth: 4
    toc_float: yes
    number_sections: no
    toc_collapsed: yes
    code_folding: hide
    code_download: yes
    smooth_scroll: yes
    highlight: monochrome
    theme: spacelab
  pdf_document: 
    toc: yes
    toc_depth: 4
    fig_caption: yes
    number_sections: yes
    fig_width: 3
    fig_height: 3
editor_options: 
  chunk_output_type: inline
---




 
 \
 
## **Assignment Objectives** 

<p>
* Reinforce the understanding of Bootstrap sampling .

* Understand the bootstrap estimation: confidence interval and sampling distribution.
</p>


## **Policies of Using AI Tools**

<p>
**Policy on AI Tool Use**: Please adhere to the AI tool policy specified in the course syllabus. The direct copying of AI-generated content is strictly prohibited. All submitted work must reflect your own understanding; where external tools are consulted, content must be thoroughly rephrased and synthesized in your own words.
</p>

<p>
**Code Inclusion Requirement**: Any code included in your essay must be properly commented to explain the purpose and/or expected output of key code lines. Submitting AI-generated code without meaningful, student-added comments will not be accepted.
</p>


<p>**Log-normal Distribution Revisited**</p>

<p>
If $Y = \ln(X) \sim N(\mu, \sigma^2)$, then $X$ follows a lognormal distribution $X \sim \text{Lognormal}(\mu, \sigma^2)$. The probability density is given by

$$
f(x|\mu,\sigma) = \frac{1}{x\sigma\sqrt{2\pi}} \exp\left(-\frac{(\ln x - \mu)^2}{2\sigma^2}\right), \quad x > 0
$$

After some algebra, we can express the mean and variance of the above lognormal distribution in the following

$$
\begin{align}
\mathbb{E}[X] &= \exp\left(\mu + \frac{\sigma^2}{2}\right) \\
\text{Var}(X) &= [\exp(\sigma^2) - 1] \exp(2\mu + \sigma^2)
\end{align}
$$

Using the relationship between normal and log-normal distribution and a sample $\{x_1, x_2, \dots, x_n\}$, the MLE estimators of $\mu$ and $\sigma^2$ are given by

$$
\begin{align}
\hat{\mu} &= \frac{1}{n}\sum_{i=1}^n \ln(x_i) \\
\hat{\sigma}^2 &= \frac{1}{n}\sum_{i=1}^n (\ln(x_i) - \hat{\mu})^2
\end{align}
$$

Using the plug-in principle of MLE, we have the MLE of $\mathbb{E}[X]$ and $\text{Var}(X)$ in the following

$$
\boxed{\widehat{\mathbb{E}[X]} = \exp\left(\hat{\mu} + \frac{\hat{\sigma}^2}{2}\right)}
$$

</P>



<p><font color = "blue">**This assignment focuses on constructing various bootstrap confidence intervals of the lognormal population mean $\mathbb{E}[X]$**</font></p>


\

## **Question: Trace Metal Concentrations in Soil**

<p>
Soil lead (Pb) concentrations (mg/kg) from 55 urban garden sites. Trace metals in environmental media typically follow lognormal distributions due to:

* Multiplicative processes controlling accumulation

* Positive constraints (concentrations cannot be negative)

* Right-skewed nature of contamination patterns
</p>

<p>
```
0.85, 1.23, 0.92, 3.45, 2.11, 1.56, 4.89, 2.34, 1.78, 6.72, 0.95, 1.34, 8.91, 
2.67, 1.89, 5.43, 1.12, 3.78, 2.45, 7.65, 1.05, 1.45, 12.34, 2.89, 2.01, 4.56, 
1.23, 4.32, 2.67, 9.87, 0.99, 1.56, 15.23, 3.12, 2.34, 3.89, 1.34, 5.67, 2.89, 
11.45, 1.12, 1.67, 18.90, 3.45, 2.56, 3.45, 1.45, 6.78, 3.12, 14.56, 1.23, 1.78, 
22.34, 3.78, 2.78
```
</p>

<p>
Assuming the data follow a log-normal distribution. For each of the following questions, first describe your reasoning process for the analysis, then write code to perform the actual analysis. Finally, summarize the results to conclude the question.
</P>

<p>
a). Perform 5000 bootstrap samples to estimate the **bootstrap sampling distribution** of $\boxed{\widehat{\mathbb{E}[X]}$ and plot it as either a histogram or a kernel density curve. Comment on the shape and patterns observed in the bootstrap sampling distribution.

b) Construct a **95% bootstrap percentile confidence interval for $\mathbb{E}[X]$**.

c) Construct a **95% bootstrap BCa confidence interval** for $\mathbb{E}[X]$.

d) Assuming both confidence intervals above are valid, compare them in terms of performance and recommend which method should be used in this analysis. Justify your recommendation.
</p>




