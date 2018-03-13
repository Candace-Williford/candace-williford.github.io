---
layout: post
comments: true
title: Catching up
---

Alright, I'm back. I took a hiatus a little longer than I intended but I think I'm going to try and be less worried about creating a post on such a rigorous schedule. It's extremely difficult to maintain while trying to keep studies up between meetups and watching tutorials and not to mention the routine ups and downs of everyday life. 

I'd also really like to start contributing more to open source as well. There's a lot of material out there on getting started on it but I feel like it's still a bit intimidating. I just took a look at my first issue the other day (https://github.com/dotnet/roslyn/issues/25303#issuecomment-372351917) and my old laptop won't even run a project as large as .NET's Roslyn! So now I'm working on upgrading/getting a new system. Trying to understand the code of a project as big as Roslyn is also difficult and the issue I linked actually includes ILSpy's ICSharpcode.Decompiler project as well so I was actually looking at TWO large projects which made it more interesting. 

One tip I can give that most people likely know about already is to almost just follow the keywords to start. For example, the issue describes that when decompiling an 'int' that the spacing should be "prettier". So, I started by searching the project in question for the keyword 'decompile'. That's when I stumbled on an instantiation of a class called CSharpDecompiler. That then led me to the file that contained the dependencies for the project that contained the referenced to ILSpy's ICSharpCode.Decompiler. I then followed the method calls all the way down the rabbit hole narrowing down the change to the CSharpOutputVisitor.cs file and led to the generation of a new issue in ILSpy's project (https://github.com/icsharpcode/ILSpy/issues/1088). I had some help in understanding what I found of course and must give thanks to @siegfriedpammer, @sharwell, and @CyrusNajmabadi. They've all been very helpful so far! After I get me a system straightened out, I will be getting back with @siegfriedpammer on the best way to implement the changes he described in the new issues. I'm all about getting it done right the first time.

Before I delved into that over the weekend I also spent about a week combing through a bunch of security stuff, trying to find some decent resources to learn from. The best I have found so far is actually PluralSight.com. At $29.99/month you will have quite literally, a wealth of knowledge at your fingertips, not even just security related content but almost anything IT related. PluralSight has what they call a "Path" that contains 75 whopping hours of security content under the "Ethical Hacking" path. Another good resource is Offensive-security.com which allows you to run through a course and then take a test for a corresponding certification at the end. This option is much more cost prohibitive though, their cheapest course running $450.

However, I have very much found that I need to just focus on one career path for now. I'm spreading myself too thin trying to learn 2 different career paths at once and found myself feeling overwhelmed. But the way I see it, I'm only 23 years old. I've got my whole life to do both if I want to. For now I will stick with and continue on with a career focus in software development in the .NET stack and become a master in it. Security can wait a decade or so! It's certainly not going anywhere.

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
