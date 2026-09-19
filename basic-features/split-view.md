---
description: Compare two traffic views with separate filters and selections in Proxyman for macOS.
---

# Split View

## 1. What's it?

Split View shows two traffic panes side by side in the same tab. Each pane has its own request list, filters, selected request, and inspector.

Both panes share the same capture. You can inspect two endpoints or compare requests from different apps without switching back and forth.

{% hint style="info" %}
Split View is available in Proxyman v26.0.0 or later for macOS and requires Proxyman PRO.
{% endhint %}

<!-- IMAGE PLACEHOLDER: Split View with two request lists, different filters, and inspectors below each list. -->

## 2. Benefits

* Keep two apps, domains, or endpoints visible at the same time.
* Use different filters in each pane.
* Select a request in each pane and compare their headers, bodies, or status codes.
* Watch new requests arrive while keeping another request open for reference.
* Combine Split View with [Tab View](multiple-tabs.md) to organize your work.

## 3. How to open it?

Use the toolbar:

1. Open the tab you want to split.
2. Click **Show Split View** in the main toolbar.
3. Click inside either pane to make it active.

Or open an app or domain directly:

1. Right-click the app or domain in the sidebar.
2. Select **Open as Split View**.
3. Proxyman opens it in the second pane. If the second pane is already open, Proxyman uses that pane.

<!-- IMAGE PLACEHOLDER: Sidebar context menu with Open as Split View below Open as New Tab. -->

Proxyman supports two panes per tab. Opening another source as Split View changes the second pane instead of adding a third one.

## 4. Work with each pane

* Click a pane before selecting a source in the shared sidebar or using a toolbar action.
* Apply filters to the active pane. The other pane keeps its own filters.
* Select different requests in the two lists. Each inspector shows its pane's selected request.
* Drag the divider to adjust the width of the panes.

Newly opened split panes put their inspectors below the request lists. You can change the inspector position with the existing [layout controls](horizontal-vertical-layout.md).

To compare two endpoints:

1. Filter the first pane to the profile endpoint.
2. Filter the second pane to the activity endpoint.
3. Reproduce the action in your app.
4. Select a request in each pane and compare the results.

For highlighted differences between two requests or responses, use the [Diff tool](../advanced-features/diff.md).

## 5. How to close it?

Click **Hide Split View** in the toolbar to return to the first pane. Closing the second pane does not delete the captured traffic.

Each tab has its own layout. You can keep Split View open in one tab and use a single pane in another.

## 6. Related guides

* [Tab View](multiple-tabs.md)
* [Content Filter](content-filter.md)
* [Multiple Filters](../advanced-features/multiple-filters.md)
* [Horizontal/Vertical/Window Layout](horizontal-vertical-layout.md)
