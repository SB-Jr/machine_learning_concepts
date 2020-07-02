# Transfer Learning

<div id='md-toc-content' >
</div>

## Introduction

Transfer learning is a machine learning technique where a model trained on one task is re-purposed on a second related task.

Transfer learning only works in deep learning if the model features learned from the first task are general.

Terms such as *Learning to Learn*, *Knowledge Consolidation*, and *Inductive Transfer* are used interchangeably with transfer learning.

The main motivation for Transfer Learning is to see how we can leverage knowledge from a pre-trained models and use it to solve new problems.

<img src='../assets/tl.png' />



## Formal Definition

 In their paper, [*A Survey on Transfer Learning*](https://www.cse.ust.hk/~qyang/Docs/2009/tkde_transfer_learning.pdf), Pan and Yang use domain, task, and probabilities to present a framework for understanding transfer learning. The framework is defined as follows:

A domain, ***D***, is defined as a two-element tuple consisting of feature space, ***ꭕ***, and probability, ***P(Χ)***, where ***Χ*** is a sample data point and  ***X = {x~1~, x~2~, ….. x~n~}*** . Thus, we can represent the domain mathematically as ***D = {ꭕ,P(Χ)}***

Here ***xᵢ*** represents a specific vector as represented in the above depiction.

 A task, ***T***, on the other hand, can be defined as a two-element tuple of the label space, ***γ***, and objective function, ***η***. The objective function can also be denoted as ***P(γ| Χ)*** from a probabilistic view point.

So ***T = {γ, P(Y|X) = {γ, η)*** and ***Y = {y~1~, y~2~, …. y~n~}***

> Given a source domain ***D~s~*** , a corresponding source task ***T~s~***, as well as a target domain ***D~T~*** an a target task ***T~T~***, the objectve of transfer learning now is to enable us to learn the target conditional probability distribution ***P(T~T~ | X~T~)*** in ***D~T~***  with the information gained from ***D~S~*** and ***T~S~*** where ***D~S***~ $\not=$ ***D~T~*** and ***T~S~*** $\not =$ ***T~T~***.
>
> In most cases a limited number of labeled target examples, which is exponentially smller than the numbe of labeled source examples are assumed to be available.



## Scenarios

There are 4 scenarios which can take place:

- ***X~S~ $\not =$ X~T~*** i.e. feature space of the source and target domain are different.
  - eg: Documents written in 2 languages where source and target language are different and we have to process the document.
- ***P(X~S~ )$\not =$ P(X~T~)*** i.e.  probability distribution of source and target domain are different
  - eg: Document written in different topics that need to be processed,source and target topics are diffferent
- ***Y~S~ $\not =$ Y~T~*** i.e. Label spaces between the 2 tasks are different.
  - eg: document need to be assigned in different tasks. This is rare that labels are different by conditional spaces are same.
- ***P(Y~S~|X~S~) $\not =$ P(Y~T~|X~T~)*** i.e. conditional probability distributions of the source and target tasks are different.
  - eg: Source and target document with regard to their classes.



## Key Question to Answer

- **What to transfer:** This is the first and the most important step in the whole process. We try to seek answers about which part of the knowledge can be transferred from the source to the target in order to improve the performance of the target task. When trying to answer this question, we try to identify which portion of knowledge is source-specific and what is common between the source and the target.
- **When to transfer:** There can be scenarios where transferring knowledge for the sake of it may make matters worse than improving anything (also known as negative transfer). We should aim at utilizing transfer learning to improve target task performance/results and not degrade them. We need to be careful about when to transfer and when not to.
- **How to transfer:** Once the *what* and *when* have been answered, we can proceed towards identifying ways of actually transferring the knowledge across domains/tasks. This involves changes to existing algorithms and different techniques, which we will cover in later sections of this article. Also, specific case studies are lined up in the end for a better understanding of how to transfer.



## Strategies

<img src='../assets/tl2.png' />

### Inductive Transfer Learning

In this scenario, the source and target domains are the same, yet the source and target tasks are different from each other. The algorithms try to utilize the inductive biases of the source domain to help improve the target task. Depending upon whether the source domain contains labeled data or not, this can be further divided into two subcategories, similar to multitask learning and self-taught learning, respectively.

### Unsupervised Transfer Learning

 This setting is similar to inductive transfer itself, with a focus on unsupervised tasks in the target domain. The source and target domains are similar, but the tasks are different. In this scenario, labeled data is unavailable in either of the domains.

### Transductive Transfer Learning

 In this scenario, there are similarities between the source and target tasks, but the corresponding domains are different. In this setting, the source domain has a lot of labeled data, while the target domain has none. This can be further classified into subcategories, referring to settings where either the feature spaces are different or the marginal probabilities.

<table>
  <thead>
    <tr>
      <th>Learning Strategy</th>
      <th>Realated Areas</th>
	    <th>Source And Target Domains</th>
  	  <th>Source Domain Labels</th>
    	<th>Target Domain Labels</th>
    	<th>Source And Target Tasks</th>
    	<th>Tasks</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Inductive Trasnfer Learning</td>
      <td>Muti-Task Learning</td>
      <td>Same</td>
      <td>Available</td>
      <td>Available</td>
      <td>Different but Related</td>
      <td>
        <ul>
        	<li>Regression</li>
          <li>Classification</li>
        </ul>
       </td>
    </tr>
    <tr>
      <td>-</td>
      <td>Slef-Taught Learning</td>
      <td>Same</td>
      <td>Unavailable</td>
      <td>Available</td>
      <td>Different but Related</td>
      <td>
        <ul>
          <li>Regression</li>
          <li>Classification</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Unsupervised Transfer Learning</td>
      <td>-</td>
      <td>Different but Related</td>
      <td>Unavailable</td>
      <td>Unvailable</td>
      <td>Different but Related</td>
      <td>
        <ul>
          <li>Clustering</li>
          <li>Dimensionality Reduction</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Transductive Transfer Learning</td>
      <td>
        <ul>
          <li>Domain Adaption</li>
          <li>Sample Selection Bias and Covariate Shift</li>
        </ul>
      </td>
      <td>Different but Related</td>
      <td>Available</td>
      <td>Unavailable</td>
      <td>Same</td>
      <td>
        <ul>
          <li>Regression</li>
          <li>Classification</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>



## What to Transfer

### Instance Transfer

Reusing knowledge from the source domain to the target task is usually an ideal scenario. In most cases, the source domain data cannot be reused directly. Rather, there are **certain instances from the source domain that can be reused along with target data to improve results**. In case of inductive transfer, modifications such as AdaBoost by Dai and their co-authors help utilize training instances from the source domain for improvements in the target task.

### Feature Representation Transfer

This approach aims to minimize domain divergence and reduce error rates by identifying good feature representations that can be utilized from the source to target domains. Depending upon the availability of labeled data, supervised or unsupervised methods may be applied for feature-representation-based transfers.

### Parameter Transfer

This approach works on the assumption that the models for related tasks share some parameters or prior distribution of hyperparameters. Unlike multitask learning, where both the source and target tasks are learned simultaneously, for transfer learning, we may apply additional weightage to the loss of the target domain to improve overall performance.

### Relational Knowledge Transfer

Unlike the preceding three approaches, the relational-knowledge transfer attempts to handle non-IID data, such as data that is not independent and identically distributed. In other words, data, where each data point has a relationship with other data points; for instance, social network data utilizes relational-knowledge-transfer techniques.

<table>
  <thead>
    <tr>
      <th>Transfer Method</th>
      <th>Inductive Transfer Learning</th>
      <th>Transductive Transfer Learning</th>
      <th>Unsupervised Trasnfer Learning</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Instance Transfer</td>
      <td>☑️</td>
      <td>☑️</td>
      <td>-</td>
    </tr>
    <tr>
      <td>Feature Representation Transfer</td>
      <td>☑️</td>
      <td>☑️</td>
      <td>☑️</td>
    </tr>
    <tr>
      <td>Parameter Transfer</td>
      <td>☑️</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <td>Relational Knowledge Transfer</td>
      <td>☑️</td>
      <td>-</td>
      <td>-</td>
    </tr>
  </tbody>
</table>



## Transfer Learning In DEEP LEARNING

Deep learning models are representative of what is also known as ***inductive learning***.