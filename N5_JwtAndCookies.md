## Add Task

```js
router.post("/", async (req, res) => {
try {
const savedTask = await Task.create(req.body); // Combine creation and saving
res.status(201).json(savedTask);
} catch (error) {
res.status(400).json({ error: error.message });
}
});


```
