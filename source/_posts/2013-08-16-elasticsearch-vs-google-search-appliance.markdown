---
layout: post
title: "Elasticsearch vs Google Search Appliance"
date: 2013-08-16 22:23
comments: true
categories: elasticsearch gsa google-search-appliance
---

With the rise in popularity of Google Search Appliance and Elasticsearch, many companies are interested in the best search solution for them. While both are solid search tools which can meet most needs, they specialize in very different domains. To understand the strengths and weaknesses, one must first understand structured vs unstructured data.

Structured vs Unstructured
-------------------------

Structured data is data that naturally fits a hierarchical structure. Data represented by JSON, XML, or relational databases typically fits the requirements. A concrete example is a resume. Below is a resume, in JSON, which provides fairly structured data.

	firstName: Kevin
	lastName: Greene
	currentJob:
		jobTitle: Senior Software Engineer
		company: Spantree Technology
		dateJoined: 2013-05-12
	pastJobs:
		{
		jobTitle: Software Engineer
		company: Fundspire Inc.
		dateJoined: 2012-01-01
		}
	languagesKnown:
		Java,
		Groovy,
		Python,
		CoffeeScript,
		JavaScript
	frameworksKnown:
		Grails,
		Elasticsearch,
		Backbone

It is possible to go several layers deeper, e.g. each company has its own data, such as the CEO, public or private, etc.

Unstructured data is made of relatively freeform text. This data could be found in flat files, or on most web pages. An example is a blog article, which has a title, an author, a date-created, keywords, and default text. It's a very flat file structure.

Storing and Searching the Data
-------------------------

With Elasticsearch, all objects are stored as JSON. It also supports very complex mappings between objects, allowing very distinct mappings to be specified (e.g. all employees have 0 or more pastJobs, which have a structure of their own).

Because the data is stored in a complex manner, complex searches become simple. Using resumes as an example, a recruiter could want to search for everyone who was familiar with both Ruby on Rails and CoffeeScript, to make sure they had familiarity with the necessary tools. This can be done by either explicitly selecting these skills from a discrete set, or by simply typing in the desired skills.

Queries can get increasingly complex, e.g. searching for a former employee of Coca-cola who worked in marketing during the New Coke era.

Google Search Appliance, on the other hand, stores the data as a flat file. This limits the capabilities of the search to a few filters, and free-text search.

Add-ons / Effort
-------------------------

The true draw of the GSA isn't due to its superior power, but due to its ease of use. With the click of a few buttons, you can be harnessing the full power of Google, with autosuggest, automatic indexing, language translation, and more built into the search solution.

Elasticsearch can do nearly everything the GSA can do, but it requires some extra development effort. Some things, like adding synonyms or spellcheck, are relatively easy endeavors, although they would require a technical person. Others, like regularly indexing and crawling a site, requires harnessing other open source tools such as Apache Nutch, increasing the development effort.

Ongoing Costs
-------------------------

While the GSA can meet many needs, it comes at a price. Google licenses the boxes at $15,000 / year, with a minimum of a two year contract.

Elasticsearch, on the other hand, is completely free and open source software (supported by a multimillion dollar company).