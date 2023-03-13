# vue-todo-hackthon

Vue 3 introduce `script setup`, but it doesn't support by default with `vue create`,
you need manually add the support by add `vueComplierConfig` to `jsconfig/tsconfig`:

```json
  "vueCompilerOptions": {
    "extensions": [
      ".vue"
    ]
  }
```
