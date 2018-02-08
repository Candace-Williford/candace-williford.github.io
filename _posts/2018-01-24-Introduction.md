---
layout: post
comments: true
title: Introduction
---

Hey guys, I'm a software developer with experience in a broad spectrum of stuff such as C# and .NET webforms, Groovy, Velocity, CMSs (Intrexx in particular), some JavaScript and Git and a few other things sprinkled in between. What I'd really like to do is learn as much as I can about anything I can get my hands on.

This blog is to help me keep track of everything I'm learning. I'm a hands-on learner so things "stick" a lot better for me if I can actually DO them and then explain what I've learned. 

It's my goal right now to commit to my GitHub about 2-3 times a week and this blog about once a week.

Let me know if you guys have any suggestions for resources. I'm all ears!

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
