<template class="container">
  <h2>プロフィール入力フォーム</h2>
  <div class="form">
    <template v-for="e of entries" :key="e">
      <p>{{ e.title ? e.title : e.items[0].label }}</p>
      <label v-for="i of e.items" :key="i">
        <span v-show="e.title !== ''">{{ i.label }}</span>
        <input
          :type="e.type"
          :placeholder="i.placeholder"
          :min="e.minVal && e.minVal"
        />
      </label>
    </template>
    <button @click="onSubmit">登録</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      entries: [
        {
          title: "名前（漢字)",
          type: "text",
          items: [
            {
              label: "姓",
              placeholder: "山田",
            },
            {
              label: "名",
              placeholder: "太郎",
            },
          ],
        },
        {
          title: "名前（カナ)",
          type: "text",
          items: [
            {
              label: "セイ",
              placeholder: "ヤマダ",
            },
            {
              label: "メイ",
              placeholder: "タロウ",
            },
          ],
        },
        {
          title: "",
          type: "number",
          minVal: 0,
          items: [{ label: "年齢", placeholder: 20 }],
        },
      ],
    };
  },
  computed: {},
  methods: {
    onSubmit() {
      console.log("onSubmit");
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 28rem;
  margin-left: auto;
  margin-right: auto;
  padding-top: 3rem;
  padding-bottom: 3rem;
}
.form {
  max-width: 20rem;
  display: grid;
  grid-template-columns: repeat(1, minmax(0, 1fr));
  gap: 0.6rem;
}
* {
  color: darkslategray;
}
p {
  margin: 0.8rem 0 0 0;
  padding-top: 0.8rem;
  border-top: solid 1px darkgray;
}
label {
  display: block;
}
input {
  margin-top: 0.25rem;
  display: block;
  width: 100%;
  border-radius: 0.375rem;
}
button {
  margin-top: 1rem;
  max-width: 10rem;
}
</style>
