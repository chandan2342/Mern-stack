const data = {
id: 1,
name: "John Doe",
age: 25,
};

### Concise Summary of Methods

- **Body**:
  Use `req.body`
  with `axios.post(url, data)`
  → Destructure using `const { id, name, age } = req.body;`

- **Query**:
  Use `req.query`
  with `axios.get(url, { params: data })`
  → Destructure using `const { id, name, age } = req.query;`

- **URL Params**:
  Use `req.params`
  with `axios.get(url/:id/:name/:age)`
  → Destructure using `const { id, name, age } = req.params;`
