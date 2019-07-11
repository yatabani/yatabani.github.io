---
layout: post
title: Integrating Select2 with czMore
---

Many people asked how to integrate [czMore](http://cozeit.github.io/czMore) with Select2.

## The Problem

The issue is with any other DOM related jQuery plugin is that the DOM object needs to exist before the plugin can be activated for, this applies to Auto-Complete plugins too.

## The Solution
The solution is to activate the plugin after the addition of the DOM objects by czMore, this is done by making use of the onAdd event, which is fired after adding new HTML (DOM objects).

## Example

```javascript
$("#czContainer").czMore({
        onAdd: function() {
            $("input[id$='_suffix']").select2();
        }
});
```

## Contribution
I ask anybody interested in czMore to step in and contribute to the project, remember it takes a group to make a great library