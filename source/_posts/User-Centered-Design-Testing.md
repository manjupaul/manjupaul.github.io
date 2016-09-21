---
title: User Centered Design - Testing
date: 2016-09-19 13:50:53
categories:
- agile
tags:
- persona
- actor
---
In the last decade `Use cases` were often used elaborate the requirements, but with Agile, `User stories` are used as a replacement. Now the trend is changing, the whole fuss is about User Centered Design. In this post I will be throwing out few thought on how Testers should adapt to this paradigm shift.

- A use case narrates what system does or must do as a response to an actor's action.
- User stories are short, simple descriptions of a feature(or requirement) told from the perspective of the person who desires the new capability.

{% blockquote UsabilityFirst  http://www.usabilityfirst.com/about-usability/introduction-to-user-centered-design/ - User Persona %}
User-Centered Design (UCD) is the process of designing a tool, such as a website’s or application’s user interface, from the perspective of how it will be understood and used by a human user. Rather than requiring users to adapt their attitudes and behaviors in order to learn and use a system, a system can be designed to support its intended users’ existing beliefs, attitudes, and behaviors as they relate to the tasks that the system is being designed to support.
{% endblockquote %}


#### Actors

{% blockquote Wikipedia  https://en.wikipedia.org/wiki/Use_case#Actors - Use case %}
An actor might be a person, a company or organization, a computer program, or a computer system—hardware, software, or both.
{% endblockquote %}

So, a person using the sytem may be represented as different actors because he is playing different roles. Example 'Customer', 'Teller' etc are valid Actors of a banking system. So, "Joel" who is a `Teller` at PNC bank could become a `Customer` when he uses the ATM machine to withdraw cash from his own account.

#### Persona
Unlike actors, personas are not roles which people play. Personas are different because they describe an archetypical instance of an actor. The persona description of a 'Customer' at PNC bank is shown below:

{% blockquote Frances Miller  http://www.agilemodeling.com/artifacts/personas.htm -  Agile Modelling %}
**Frances Miller**
Sixty-seven year-old Frances is the mother of four children and the grandmother of twelve. She lives in her own home, bakes a pie once a week so that she has something to serve for Sunday visitors (usually one of her children and their immediate family), and has two cats. The cats' names are Fred and Wilma, names given to them by four-year old grandson Bobby. She likes to knit and do needlework, which she either gives away as presents to her family or donates to the annual sale to raise money for the church she belongs to.

Every morning she goes for a one hour walk along the lake front when the weather is good. On bad days she'll go with her neighbor to the local mall where a group of senior citizens "Mall Stroll" each morning before sitting down at one of the restaurants for coffee or tea. For breakfast Frances prefers a cup of Earl Grey tea and two slices of whole-wheat toast with her own home-made preserves. Lunch is typically a bowl of soup or a sandwich and then she'll have the opposite for dinner.

She is a middle-class retiree living on a fixed income. Her mortgage has been paid off and she has one credit card which she seldom uses. She has been a customer of the bank for 57 years although has never used an automated teller machine (ATM) and never intends to. She has no patience for phone banking and does not own a computer. Every Monday at 10:30 am she will visit her local bank branch to withdraw enough cash for the week. She prefers to talk with Selma the branch manager or with Robert, a CSR who was a high-school friend of her oldest son.
{% endblockquote %}



### Take home
In my opinion modelling the user personas is helpful than an actor description. It will help the tester to blend in the skin of a user and effectively be like one and there by write effective testcases.