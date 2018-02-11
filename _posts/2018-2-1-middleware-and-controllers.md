---
layout: post
comments: true
title: Middleware and Controllers
---

Okay, work's been a bit crazy this week so I didn't get much time to study but I did finally manage to squeeze in a couple days. I decided I'd start with learning about ASP.NET Core since I keep hearing about it more and more these days. I started watching the ASP.NET Core course on PluralSight and so far it looks pretty awesome. I finished the first and second modules which went over middleware, configuration, controllers, routing, and action results. 

Configuration is handled in the `Startup.cs` file and requires a `ConfigureServices` method and a `Configure` method. 
`Configure` utilizes dependency injection to set up the request pipeline for the application by adding middleware. This method takes instances of `IApplicationBuilder` and `IHostingEnvironment` to handle any specific properties of your application, and also any other objects you may need to set up your middleware. The `IApplicationBuilder` instance is what you add your middleware to.

`ConfigureServices` is where you register all of your services that aren't automatically registered by ASP.NET Core. Most commonly, you are going to register custom services or the MVC service. An interesting fact about this method is that apparently "dependency injection isn't set up until after `ConfigureServices` is invoked" (Microsoft).

After all the configuration is done you have to add your middleware, which is done by adding it to your application's instance of `IApplicationBuilder`. Middleware is the first component to handle an HTTP request. You can have multiple pieces of middleware, each one passing the request off to the next one after it finihes handling it. This is called the "pipeline" and is why the order in which you invoke your middleware is important. One piece of middleware may affect the way the response is handled by the next piece.

The final piece of middleware in the pipeline then passes the request on to a controller. Controllers are used to "route" incoming requests to the correct action, or method, based on the URL of the original HTTP request. You can set up these routes using conventional and/or attribute based configuration. It can actually be beneficial to use both configurations in tandem. Use convention based routing to set up a default routing template, and then use attribute based routing if you require some custom behaviour.

Conventional routing is ideal for keeping all of your configuration in one place and defining templates, and can be set up by adding a `ConfigureRoutes` method to the 'Startup.cs' file. This `ConfigureRoutes` method takes an instance of `IRoutingBuilder` that will allow you to map your routes. To do this, you pass a friendly name and your routing configuration to `routingBuilder.MapRoute`. Your routing configuration will generally look similar to `{controller}/{action}`. You can also setup defaults on that configuration by specifying which controller and action you want to invoke if it's not specified in the request. So a standard route mapping might look like 
```C#
routingBuilder.MapRoute("Default", "/{controller=Home}/{action=Index}");
```
This configuration tells .NET Core to go to the Home controller, which is a class called `HomeController`, and then to a method on that controller called 'Index'.

Attribute based routing behaves much the same way but is set up using attributes on the controller and provides a little more flexibility than convention based routing. To set this up, you add a `[Route("")]` attribute at the class level to specify what url path you want the controller to be mapped to and do the same at the action level. .NET Core MVC will handle the rest.

After the controller's action is done handling the request, it then generates an action result that implements `IActionResult`. This action result is then used to format and handle the response. However it should be noted that the action result is not executed until later in the pipeline when the response is actually being rendered. This is better separation of concerns by enabling the controller to only be concerned with WHAT should be done and not having to worry about having to actually DO that action.

When the action is handled it will either get returned as a response to some other service such as a REST API, or it will get rendered into a view as HTML. I will write about that next week after I go through some more of the course. I will also be talking about models and integrating with Entity Framework. I don't have a lot of experience with Entity Framework so it will be really nice to check that out. It will also be interesting to get SQL Server up and running on my system because I'm actually on Ubuntu right now. 

I'm also going to try and get a theme on my blog soon. I've got one picked out that I like, I've just had trouble finding the time to do it so stay tuned for that!

<cite>
Anderson, R., Michaelis, M., Smith, S., Roth, D., & Latham, L. (2018, January 11). Configuration in ASP.NET Core App. Retrieved January 31, 2018, from https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration
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
