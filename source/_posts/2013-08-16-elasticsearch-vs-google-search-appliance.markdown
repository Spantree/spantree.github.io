---
layout: post
title: "Elasticsearch vs Google Search Appliance Part 1 - Overview / History"
date: 2013-09-04 12:00
comments: true
author: Kevin Greene
categories: elasticsearch gsa google-search-appliance
---

With the rise in popularity of Google Search Appliance and Elasticsearch, many companies are interested in the best search solution for them. At Spantree, we've been asked several times if the GSA or Elasticsearch is a better solution, and we have decided to cover the various strengths and weaknesses in a series of blog posts. While both are solid search tools which can meet most needs, they specialize in very different domains. To understand the strengths and weaknesses, it's important to note what the general philosophy of each technology is.

Elasticsearch
-------------------------
Elasticsearch was built upon Apache Lucene, and carries several of the same principals. Both focus on document storage and retrieval, focusing on searching and sorting many different fields within a document. For example, searching for a list of books would allow you to search and sort by author, title, keywords, etc. In Elasticsearch, this specification can be explicit, by specifying the author, or implicit, by searching for the author's name, results will be returned that contain the desired author.

Elasticsearch specifically was built do to the poor scalability of Lucene at the time. Shay Banon was hoping to extend his existing library, Compass, to be more scalable, when he realized it required a new solution entirely. Elasticsearch was built from the ground up to be a scalable search, providing the power of Apache Lucene across multiple cores.

In 2012, a company was created around Elasticsearch, providing more financial and developer support, and adding to the ever-growing features list.


Google Search Appliance
-------------------------
GSA was Google's extension of their own product into the business marketplace. Many businesses desired the same power and consistency that Google offers, but for their own sites and files. GSA has very much so captured the feel of a private Google, as the business that purchases it acquires the actual hardware box, which is used as the search server.

Because of its roots in Google, GSA focuses on full-text search, which it can do over websites, files, and databases. Because it has the security of Google built in, many companies use it for both intranet and internet search, hosting their private records on one, and their public records on another.

Google has continued to upgrade it over the years, both directly and via the upgrades of their search algorithms.

Structured vs Unstructured Data
-------------------------

The two products primarily differ in the way they represent the data.  The GSA works with web pages and other documents which are essentially composed of flat text.  On the other hand, Elasticsearch documents are JSON objects with a nested hierarchy, which are useful for indexing data that has a lot of inherent structure.

As an example, you can think of two types of data sources.  One is a database of employees at a company and the other is a site full of employee biographies.  If the employee biographies are just plain text, it may be hard to determine where in the text to find an employee's name or when they started working at the company.  On the other hand, this information could be readily available in a database.  

Since the GSA is a little bit of Google in your infrastructure, it is unbeatable at finding a whole document that is most relevant for a certain query.  But, since it treats documents as objects, Elasticsearch shines at finding some subset of a document that is most relevant for a query.  Of course, this oversimplifies things, as both solutions can be massaged into handling both kinds of data.  But it is the ease with which you can deal with one sort of data or the other that is important to keep in mind when making a decision.

Ongoing Costs
-------------------------

While the GSA can meet many needs, it comes at a price. Google licenses the boxes at $15,000 / year, with a minimum of a two year contract.

Elasticsearch, on the other hand, is completely free and open source software (supported by a multimillion dollar company).

Summary
-------------------------
Overall, Elasticsearch and GSA can both solve most problems, but to make sure the best tool is used, evaluate the type of data that needs to be indexed. If most data follows a clear structure, then Elasticsearch is the way to go. If most data follows the form of a webpage, with a few keywords but primarily freeform text, then GSA should be considered.

In our next issue, we will cover the differences of indexing between Elasticsearch and Google Search Appliance.