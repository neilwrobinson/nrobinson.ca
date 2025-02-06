---
title: "ERB def_method"
date: 2025-02-05T20:05:41-05:00
draft: false
featuredImage: "/images/2025-02-05/Template_alt_full_black_22.svg"
featuredImageAlt: "Picture of two curly braces to indicate template insertion"
tags: ["ERB", "ERB template", "metaprogramming", "Ruby"]
---
# ERB and metaprogramming

I was using ERB to generate a template over the past weekend. I discovered that you can use ERB to pry open a class and add a new method into your class that will render a template. 

For example, you create a new ERB class and pass the template or template file into the constructor to initialize a new ERB object. Now you can call the #def_method on this newly created ERB object, and pass in the following arguments:
1. class you want to generate a template on, 
2. a name of the function to call when you want to render the template (you can even name the exact instance variables for the template), and
3. the last argument is the template or template file.

With a new instantiation of the class, you can call the function you set in the second argument to render the template.

Okay, that was probably difficult to read, here’s an example using irb:

```
class TemplateExample
  def initialize 
    @hello = "Fellow Blog Reader"
  end
end
filename = 'hello <%= @hello %>'
erb = ERB.new(filename)
erb.def_method(TemplateExample, 'render()')
template_example = TemplateExample.new
template_example.render
```
output:

```
"hello Fellow Blog Reader"
```

## Conclusion:
This is a strange way to add behaviour to a class. Metaprogramming is unlike anything that I have encountered in the past. I have been used to adding behaviour by adding interfaces, implementation, and subclasses. This idea of taking a feature of an existing class and dynamically adding it to another unrelated class is a foreign concept to me. 

But it is also easy to understand and perform, but only once you understand how things work behind the scenes. Otherwise, it just seems like magic. And I guess maybe this is the appeal of Ruby. 
Thanks for coming on this short journey of metaprogramming with me.

## Source:
https://docs.ruby-lang.org/en/master/ERB.html#method-i-def_method

### Credits:
Picture credit 
"Template alt full black 22" by Srđan is licensed under CC BY-SA 4.0
https://commons.wikimedia.org/w/index.php?curid=47134358