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

In determining which solution is right for the problem, one should consider if the problem is best modeled as structured vs unstructured data. Structured data is data that naturally fits a hierarchical structure. Data represented by JSON, XML, or relational databases typically fits the requirements. A concrete example is an employee database, which would have several different fields, e.g. firstName, lastName, department, etc. It is possible to go several layers deeper, e.g. each department has its own description, employees have lists of skills, etc.


Unstructured data is made of relatively freeform text. This data could be found in flat files, or on most web pages. An example is a magazine article, which has a title, an author, an issue published, and freeform text. It's a very flat file structure.

Because Elasticsearch is designed to deal primarily with documents as objects, it heavily supports structured data. On the other hand, because GSA grew out of webpage searches, which have relatively little structured data, GSA thrives with unstructured data.

Ongoing Costs
-------------------------

While the GSA can meet many needs, it comes at a price. Google licenses the boxes at $15,000 / year, with a minimum of a two year contract.

Elasticsearch, on the other hand, is completely free and open source software (supported by a multimillion dollar company).

Summary
-------------------------
Overall, Elasticsearch and GSA can both solve most problems, but to make sure the best tool is used, evaluate the type of data that needs to be indexed. If most data follows a clear structure, then Elasticsearch is the way to go. If most data follows the form of a webpage, with a few keywords but primarily freeform text, then GSA should be considered.

In our next issue, we will cover the differences of indexing between Elasticsearch and Google Search Appliance.