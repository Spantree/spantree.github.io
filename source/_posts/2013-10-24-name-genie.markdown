---
layout: post
title: "Autogenerating Fake Users with Name Genie"
date: 2013-10-24 15:08
comments: true
published: false
author: Kevin Greene
categories: 
---

When developing most applications, there is some concept of a User, Customer, Person, etc. If you are making an application for people to use, then you should be able to represent those people.

Like many companies, we've always had issues coming up with reasonable, believeable names. Initially, we simply used

```
people: [
    {firstName: first1, lastName: last1},
    {firstName: first2, lastName: last2}
]
```

But this detracts from the feeling that they are supposed to represent real live people using your application. This was followed by the more traditional computer science version:

```
people: [
    {firstName: Alice, lastName: Allison},
    {firstName: Bob, lastName: Brown}
]
```

While this will do for a simple example, eventually it still leads to the same feeling. Not to mention you are limited to 26 names following this convention, or even less if you use the [traditional cryptographic names](http://en.wikipedia.org/wiki/Alice_and_Bob).

So, we set out to fix this issue, and created [Name Genie](https://github.com/Spantree/name-genie). Name Genie is your one stop shop for generating fake users, and we plan on building out the feature set over time. Currently, you can generate names, occupations, companies, and avatars.