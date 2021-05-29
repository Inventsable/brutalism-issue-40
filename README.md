# [Issue #40](https://github.com/battleaxedotco/brutalism/issues/40)

Hi Erik, I don't see this behavior in the docs. May be possible that behavior changes depending on OS? I'm on Windows 10 myself. [I've made a sample panel to isolate this with the code below for you to check out](https://github.com/Inventsable/brutalism-issue-40), try the following and let me know if this behavior still exists:

![](https://thumbs.gfycat.com/FirmSimplisticBlacknorwegianelkhound-size_restricted.gif)

```bash
# First ensure brutalism is up to date
npm i brutalism@latest
```

In App.vue itself:

```html
<template>
  <div id="app">
    <Menus refresh debug />
    <Panel>
      <select label="Foo" :items="fooItems" v-model="fooModel" />
      <select label="Bar" :items="barItems" v-model="barModel" />
      <select label="Doe" :items="doeItems" v-model="doeModel" />
      <Divider alt />
      <Anno>{{ `Foo: ${fooModel}` }}</Anno>
      <Anno>{{ `Bar: ${barModel}` }}</Anno>
      <Anno>{{ `Doe: ${doeModel}` }}</Anno>
    </Panel>
  </div>
</template>

<script>
  export default {
    data: () => ({
      fooItems: ["Item 1", "Item 2", "Item 3", "Item 4", "Item 5"],
      fooModel: "0",
      barItems: ["Item 1", "Item 2", "Item 3", "Item 4", "Item 5"],
      barModel: "0",
      doeItems: ["Item 1", "Item 2", "Item 3", "Item 4", "Item 5"],
      doeModel: "0",
    }),
  };
</script>
```

Of note, `<Select />` sometimes works best with a string v-model as I do above. I believe string indices are also supported -- ideally it would (and should, to be honest) be numeric indices as you're trying, but the root of this issue is likely some faulty logic with numeric indices if not a difference in OS. You could can probably mix `@update` return values in order to match numeric indices with string values within some given array if this is the case.

Let me know if this repository has the same behavior for you and we can go from there.
