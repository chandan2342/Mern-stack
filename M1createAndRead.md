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

## Get All Tasks

``js
router.get("/", async (req, res) => {
try {
const tasks = await Task.find();
res.status(200).json(tasks);
} catch (error) {
res.status(500).json({ error: error.message });
}
});``

```
