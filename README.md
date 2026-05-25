# 🌊 steamrollArray — Deep Flattening Tool

A lightweight, recursive JavaScript utility that deeply flattens nested arrays of any depth into a single flat array.

---

## 📦 Usage

```js
function steamrollArray(arr) {
  let result = [];
  for (let item of arr) {
    if (Array.isArray(item)) {
      result = result.concat(steamrollArray(item));
    } else {
      result.push(item);
    }
  }
  return result;
}
```

Simply copy the function into your project — no installation or dependencies required.

---

## ✨ Examples

```js
steamrollArray([1, [2], [3, [[4]]]]);
// → [1, 2, 3, 4]

steamrollArray([[['a']], [['b']]]);
// → ['a', 'b']

steamrollArray([1, [2, [3, [4, [5]]]]]);
// → [1, 2, 3, 4, 5]

steamrollArray([true, [[false]], [null, [undefined]]]);
// → [true, false, null, undefined]
```

---

## ⚙️ How It Works

The function uses **recursion** to handle arbitrarily deep nesting:

1. Iterates over each item in the input array.
2. If an item is itself an array, it recursively calls `steamrollArray` on it and concatenates the result.
3. If an item is a primitive value, it's pushed directly into the result array.
4. Returns the fully flattened array once all items are processed.

This approach handles **any level of nesting** without needing to know the depth in advance.

---

## 🧪 Edge Cases

| Input | Output |
|---|---|
| `[]` | `[]` |
| `[[[]]]` | `[]` |
| `[0, [false, [null]]]` | `[0, false, null]` |
| `['a', ['b', ['c']]]` | `['a', 'b', 'c']` |

---

## 🌐 Browser & Environment Compatibility

Works in any environment that supports standard JavaScript (ES5+):

- ✅ All modern browsers
- ✅ Node.js (any version)
- ✅ Deno / Bun

---

## 🤝 Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request for:

- Performance improvements
- Additional test cases
- TypeScript type definitions
