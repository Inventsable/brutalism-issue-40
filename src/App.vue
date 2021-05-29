<template>
  <div id="app">
    <Menus refresh debug />
    <Panel>
      <Select label="Foo" :items="fooItems" v-model="fooModel" />
      <Select label="Bar" :items="barItems" v-model="barModel" />
      <Select label="Doe" :items="doeItems" v-model="doeModel" />
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