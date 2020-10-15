---
layout: post
title:  "Floating-point errors in Ruby"
tags: [ruby]
description: "Learn how to avoid errors in Ruby working with floating-point numbers"
---

Ruby, like many other languages, has trouble performing arithmetic on floating-point numbers. It's not something new, but many people forget it when working with decimal numbers.

I'm not going to explain to you the problem facing floating-point arithmetic. You can get an explanation from a better source [here](https://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html).

The official Ruby documentation for the [Float class](https://ruby-doc.org/core-2.5.0/Float.html) defines itself as inexact. Let's see what happens when we do an operation between two floating numbers in Ruby:

{% highlight ruby %}
result = 0.1 + 0.2

result == 0.3 # false

result # 0.30000000000000004
{% endhighlight %}

As you can see, the result is not what you expected. This is a big problem when we are working with sensitive data, so we need to avoid this error and secure our arithmetic operations.

To achieve this, Ruby offers the [BigDecimal class](https://ruby-doc.org/stdlib-2.5.1/libdoc/bigdecimal/rdoc/BigDecimal.html), wich, to quote the official documentation: "provides support for arbitrary precision integer arithmetic".

Let's look at the same operation again, this time using the BigDecimal class:

{% highlight ruby %}
require 'bigdecimal'

result = BigDecimal('0.1') + BigDecimal('0.2')

result == 0.3 # true

result # 0.3e0
{% endhighlight %}

Problem solved. Get started with BigDecimal and forget about floating number problems, no more lost decimals performing operations in your app.
