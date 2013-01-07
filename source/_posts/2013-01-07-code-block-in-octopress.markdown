---
layout: post
title: "Code block in Octopress"
date: 2013-01-07 11:12
comments: true
categories: Octopress
---

One of the highlight feature of Octopress is [Code block][0]

It can let you share the code with syntax highlight easily.

However, it doesn't work on my Windows 7 machine.

It always throw out the following error

{% codeblock "Error message" %}
 $ rake generate
 ## Generating Site with Jekyll
 unchanged sass/screen.scss
 Configuration from d:/MyProject/Git/octopress/_config.yml
 Building site: source -> public
 Liquid Exception: No such file or directory - python c:/Ruby193/lib/ruby/gems/1.9.1/gems/pygments.rb-0.3.7/lib/pygments/mentos.py in 2013-01-06-octopress.markdown
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/posix-spawn-0.3.6/lib/posix/spawn.rb:162:in 'spawn'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/posix-spawn-0.3.6/lib/posix/spawn.rb:162:in 'spawn'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/posix-spawn-0.3.6/lib/posix/spawn.rb:307:in 'popen4'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/pygments.rb-0.3.7/lib/pygments/popen.rb:41:in 'start'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/pygments.rb-0.3.7/lib/pygments/popen.rb:203:in 'mentos'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/pygments.rb-0.3.7/lib/pygments/popen.rb:192:in 'highlight'
 d:/MyProject/Git/octopress/plugins/pygments_code.rb:24:in 'pygments'
 d:/MyProject/Git/octopress/plugins/pygments_code.rb:14:in 'highlight'
 d:/MyProject/Git/octopress/plugins/code_block.rb:82:in 'render'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/liquid-2.3.0/lib/liquid/block.rb:94:in 'block in render_all'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/liquid-2.3.0/lib/liquid/block.rb:92:in 'collect'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/liquid-2.3.0/lib/liquid/block.rb:92:in 'render_all'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/liquid-2.3.0/lib/liquid/block.rb:82:in 'render'
 c:/Ruby193/lib/ruby/gems/1.9.1/gems/liquid-2.3.0/lib/liquid/template.rb:124:in 'render'
 {% endcodeblock %}

I followed exactly the steps of installation that I found. No one mentions this problem.

Moreover, I can't find anyone else having this issue.

I guess I am on my own.

First I need to figure out how Octopress does this feature.

It seems like Octopress use [Pygments][1] from this error message.

So I tried to update pyments to the latest version. But it doesn't work.

Then I found out [Pygments][2] uses Python to work.

And I didn't have Python installed.

Well, I guess that should be it.

But thing doesn't seem like that easy. It still doesn't work after I installed [Python 2.7 / 3.3][3].

After hours and hours thinking, I noticed I can't run Python beside its folder.

OMG ! It is PATH !

After I add correct path to windows environment, IT STILL REFUSED WORK.

I entered ```path``` in the cmd. It doesn't show the path I just added.

Apparently, I need to reboot my machine to get it to work.

(another way is use SET PATH=%PATH%;C:\pathoftheprogram to avoid reboot.)

Finally ! It works like a charm after reboot.

{% codeblock lang:javascript %}
function helloWorld()
{
    alert("Hello World!");
}
{% endcodeblock %}



[0]:http://octopress.org/docs/plugins/codeblock/
[1]:http://octopress.org/docs/blogging/code/
[2]:http://pygments.org/docs/installation/
[3]:http://www.python.org/download/