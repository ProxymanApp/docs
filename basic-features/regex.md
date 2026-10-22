---
description: >-
  Use Wildcard and Regex matching rules in Proxyman tools such as Map Local and
  Breakpoint, and test your rule against sample URLs before you save it.
---

# Regex (Regular Expression)

## 1. What's it?

From version 2.3.0, Proxyman supports **Wildcard** and **Regex** (match whole words) when you define matching rules for all debugging tools:

* [Map Local](../advanced-features/map-local.md)
* [Map Remote](../advanced-features/map-remote.md)
* [Block List](../advanced-features/blacklist.md) and [Allow List](../advanced-features/whitelist.md)
* [Breakpoint](../advanced-features/breakpoint.md)
* [Protocol Buffers (Protobuf)](../advanced-features/protobuf.md)
* [Reverse Proxy](../advanced-features/reverse-proxy.md)
* [Network Conditions](../advanced-features/network-throttling.md)
* ...

It helps you define exactly which requests trigger the tool.

![Proxyman Map Remote rule list with Regex and Wildcard matching rules](<../.gitbook/assets/Screen Shot 2020-07-19 at 10.17.34.png>)

## 2. Test your URL (New feature 🎉)

From Proxyman v4.8.0, you can quickly test your rule (Wildcard or Regex).

* Quickly test and try out your Wildcard or Regex rule.
* **Save time**: You don't need to go back and forth to check your URL.
* Make fewer mistakes.

<figure><img src="../.gitbook/assets/CleanShot 2023-05-09 at 09.54.22@2x.jpg" alt="Proxyman Test Rules window checking a wildcard rule against four URLs with Matched and Not Matched results"><figcaption></figcaption></figure>

#### How to use it?

1. Open any debugging tool (Breakpoint, Map Local, ...) and create a new rule.
2. Click the **Test your Rule** button. The Test Rules window opens.
3. Add your rule and the URLs you want to check.

* :white\_check\_mark: Matched: Your URL matches your rule.
* :warning: Not Matched: Your URL doesn't match your rule. You might need to rewrite your Wildcard or Regex rule.

## 3. Wildcard

Proxyman supports two simple Wildcard characters: `*` and `?`

| Wildcard | Purpose                                                              |
| -------- | -------------------------------------------------------------------- |
| `*`      | The asterisk in a wildcard matches any character zero or more times. |
| `?`      | A question mark matches a single character once.                     |

For instance:

* http://proxyman.io/v1/\*
* https://myserver.com/v?/\*

## 4. Regex

Proxyman also supports Regex.&#x20;

* Make sure your regex **matches the whole URL**.
* A **partial match** counts as not matching.
* Make sure you **escape characters** properly: slash (/), dot (.), etc.

For instance:

| Regex                                                                        | Matched URL Examples                                                                             |
| ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| https:\\/\\/proxyman\\.io.\*                                                 | <p>https://proxyman.io<br>https://proxyman.io/v1/data?id=123<br>https://proxyman.io/pricing</p>  |
| ^(http\|https):\\/\\/www\\.google\\.com.\*                                   | <p>http://www.google.com<br>http://www.google.com/user?id=proxyman<br>https://www.google.com</p> |
| ^(http\|https)?:\\/\\/www\\.google\\.com\\/v\[0-9]?\\/build\\?query=proxyman | <p>http://www.google.com/v1/build?query=proxyman<br>www.google.com/v2/build?query=proxyman</p>   |

You can use [regex101](https://regex101.com/) to check that your regex matches the whole URL.

![regex101 test with a regex that fully matches three google.com URLs](../.gitbook/assets/1.png)

{% hint style="info" %}
Proxyman uses Apple's NSRegularExpression. Check the [**Regex** **metacharacters, operators and flags**](https://developer.apple.com/documentation/foundation/nsregularexpression#1965590) in the Apple Developer documentation to see which ones are supported.
{% endhint %}

{% hint style="info" %}
Check your regex on [regex101.com](https://regex101.com) and make sure it fully matches the given URL.
{% endhint %}

* Select **Use Regex** when you create a rule.

![Map Remote rule editor with Use Regex selected for the matching rule](<../.gitbook/assets/Screen Shot 2020-07-19 at 10.17.44.png>)

{% hint style="info" %}
With regular expressions, `?` and `*` mean something different than in wildcards. The wildcard `?` is the regex `.` and the wildcard `*` is the regex `.*`
{% endhint %}
