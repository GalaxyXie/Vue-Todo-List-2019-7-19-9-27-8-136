<template>
  <div>
    <ol >
      <li v-for="item in items" v-bind:key="item.key" v-bind:class="{ checked: item.isChecked }">
        <input name="done-todo" type="checkbox" class="done-todo" v-model="item.isChecked" />
        <span>{{item.stringcontent}}</span>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: "Content",
  props: ['items'],
}
</script>
