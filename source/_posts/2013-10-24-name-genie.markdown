---
layout: post
title: "Autogenerating Fake Users with Name Genius"
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

So, we set out to fix this issue, and created [Name Genius](https://github.com/Spantree/name-genius). Name Genius is your one stop shop for generating fake users, and we plan on building out the feature set over time. Currently, you can generate names, occupations, companies, and avatars. We've open sourced and pushed this to Maven Central, so that anyone can easily bootstrap new users.

### Adding Name Genius

SEE ABOUT EMBEDDING ONE OF THOSE SELECTORS

### Using Name Genius

We've designed Name Genius to hopefully be as simple as possible to use. The following is an example of generating 10 people (no job title or company) with Groovy:

```groovy
import net.spantree.NameGenius
import net.spantree.Person

NameGenius genius = new NameGenius()
def people = []
10.times {
    people << genius.generate()
}
people.each { Person person ->
    println "${person.firstName} ${person.lastName} (${person.gender})"
}
```

which yields the output

```
Leone Noseworthy (Female)
Elmer Kuruppillai (Male)
Annice Gaebel (Female)
Chauncey Ficken (Male)
Nicola Whiskin (Female)
Davis Wurtz (Male)
Otelia Raab (Female)
Hunter Callender (Male)
Scot Thibeault (Male)
Lise Tresrch (Female)
```

If you would like to instead make an Employee, use `genius.generateEmployee()`, which adds `jobName` and `companyName` to the resulting object.


### Example Webservice

There is a small example in 
