---
layout: post
comments: true
title: Models and Entity Framework
---

This week I watched the segments about models and entity framework. The two really go hand in hand because Entity Framework will use your models to figure out your table structure and how to manipulate data accordingly but you can use models without Entity Framework.

There are actually two different types of models, the first one being entity models. The purpose of these models is pretty straight forward in that their primary purpose is to provide a data structure for the objects that you need in your program that can be easily used to interact with the database. This is usually just a class with a bunch of properties. You can also set up data annotations, or attributes, that operate as constraints when updating the properties on the model.

The other type of model is a view model, also known as data transfer objects. These models are used to interact with a view. They usually receive a list of entity models to populate the view or a single entity model for when the user is creating a new object. On update or insert the page, or view, will usually then send a view model back to the controller to handle the action.

One benefit to using a view model is that it helps prevent overposting, which is the action of a user adding additional data to the request allowing them to manipulate data they don't have access to. The view model will typically have a subset of fields that you allow to be edited by a view that will then set the corresponding data on the entity model (hence the name "data transfer object". This is favorable to passing the entire entity model itself because that would open up access to all properties.

ASP.NET Core also attaches a token to the users form that corresponds to their HTTP request. This token helps prevent cross-site request forgery. The framework can check it to make sure that that is actually a form that was sent to the user by the current request. To do this add the `[ValidateAntiForgeryToken]` attribute to the action on the controller that is handling the form and then invoke the `ModelState.IsValid` check.

It's also interesting that there are supporting arguments that entities and models are NOT the same things as they are actually considered to be in the ASP.NET MVC framework. The argument is that entities take care of data persistence only, be it through methods and/or properties and that the model holds the business logic. ASP.NET's flexibility on the use of the two terms is most evident by the fact that you can place your entity models in a folder titled either "Models" or "Entities". However, if you are properly using the framework, maintaining it's flexibility in it's support for Entity Framework, then it's best to think of the entity models as entities because their sole purpose is actually data interaction and the business logic is handled by the viewmodel (cpratt).

Because of the configurability and flexibility of the MVC framework, it's very quick and simple to set up Entity Framework. Entity Framework is an "open-sourced ORM framework for .NET applications" that allows the developer to interact with the database in an object oriented manner. It was developed in .NET 3.5 as a solution to having to manually write out all data access code (EntityFrameworkTutorial). To set it up, all we have to do is set up a DbContext, which is used to hold information about the database, and configure the services to send the DbContext the database connection string. This will then allow us to create an initial migration that will take care of creating our DB and the schema we need to run the application. You can also add any initial SQL you might need to run, such as creating some initial data or creating indexes.

A database migration is a way of taking the class structure in an application and transforming it into a database. One advantage to using migrations is that you don't have to manage your DB code separately because any updates are automatically handled. Though in certain systems this could be seen as a disadvantage if you expect to be doing frequent database configuration updates. It could potentially make refactoring more difficult or doing things like changing fields data types or moving data between columns during data clean-up.

My next post will be about Razor views and authentication. It'll probably be a couple weeks before I get that out because I want to take a look at HackerOne and BugCrowd and see what they're all about.

<cite>
Pratt, Chris. “Entities Are Not Models.” Chris Pratt, Chris Pratt, 10 Dec. 2014, cpratt.co/entities-are-not-models/.
</cite>

<cite>
"What is Entity Framework?" 17 February 2018, entityframeworktutorial.net/what-is-entityframework.aspx.
</cite>

<cite>
Yates, Alex. “Critiquing Two Different Approaches to Delivering Databases: Migrations vs State.” Working with Devs..., 18 June 2015, workingwithdevs.com/delivering-databases-migrations-vs-state/.
</cite>

{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/

var disqus_config = function () {
this.page.url = {{ page.url }};  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = {{ page.id }}; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};

(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://candace-williford.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            
{% endif %}
