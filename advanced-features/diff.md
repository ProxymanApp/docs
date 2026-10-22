---
description: >-
  Compare two HTTP requests or responses with the Proxyman Diff tool, side by
  side or unified, including the URL, headers, status code, and body.
---

# Diff

## 1. What's it?

When you use Proxyman, you may need to find the differences between requests or responses. The Diff tool helps you:

* Diff two requests or responses, including the URL, method, status code, headers, and text-based body.
* Show the diff side by side or unified.
* Use a light or dark theme.
* Export as a unified diff file.
* Open the diff in 3rd-party apps, such as FileMerge.
* Highlight and add comments.

{% hint style="info" %}
This feature is only available for macOS 11.2 and later.
{% endhint %}

## 2. How to use it?

1. Select your requests on the main table view.
2. Right-click -> **Tools** -> **Add to Diff Pool…** (or press ⌘Y)
3. In the Diff window, select the Left and Right requests.
4. Proxyman performs the diff and displays it.

You can open the Diff window at any time from the **Diff** menu -> **Open Diff View…** (⌥⌘Y).

### Side-by-Side mode

![Proxyman Diff window comparing two responses in side-by-side mode](<../.gitbook/assets/Screen Shot 2022-03-27 at 09.30.03.png>)

### Unified Mode

![Proxyman Diff window comparing two requests in unified mode](<../.gitbook/assets/Screen Shot 2022-03-27 at 09.31.53.png>)

## 3. Open with 3rd-party diff tools

* FileMerge: requires Xcode
* Kaleidoscope: install the `ksdiff` command-line tool from Kaleidoscope's settings.

## Learn more

* [Compare two HTTP requests and responses with the Proxyman Diff tool](https://proxyman.com/posts/2022-05-28-Introduce-Diff-View)
