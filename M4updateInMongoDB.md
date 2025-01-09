# Updating Documents in MongoDB with Mongoose: `findByIdAndUpdate()` vs `updateOne()`

- **URL:** `/api/users/:id`

## 1. API Using `findByIdAndUpdate()`

This API updates a user document by its ID and returns the updated document.

### Code

```javascript
app.put("/api/users/:id", async (req, res) => {
  const { id } = req.params; // Extract user ID from params
  const { age, address } = req.body; // Extract fields to update

  try {
    const updatedUser = await User.findByIdAndUpdate(
      id,
      { $set: { age, address } }, // Update only age and address
      { new: true } // Return updated document and validate schema
    );

    if (!updatedUser) {
      return res.status(404).json({ message: "User not found" });
    }

    res.status(200).json(updatedUser); // Send updated user data as response
  } catch (error) {
    res.status(400).json({ error: error.message }); // Handle errors
  }
});
```

## 2. API Using `updateOne()`

This API updates a user document by its ID and returns a summary of the update operation instead of the document itself.

### Code Example

```javascript
app.patch("/api/users/:id", async (req, res) => {
  const { id } = req.params; // Extract user ID from params
  const { age, address } = req.body; // Extract fields to update

  try {
    const result = await User.updateOne(
      { _id: id }, // Query filter
      { $set: { age, address } }, // Update only age and address
      { runValidators: true } // Validate schema
    );

    if (result.matchedCount === 0) {
      return res.status(404).json({ message: "User not found" });
    }

    res.status(200).json({
      message: "User updated successfully",
      modifiedCount: result.modifiedCount, // Indicates how many documents were modified
    });
  } catch (error) {
    res.status(400).json({ error: error.message }); // Handle errors
  }
});
```

### Features

- **No Document Retrieval:** Provides only the status of the update operation (e.g., matched and modified counts).
- **Performance:** Faster than `findByIdAndUpdate()` as it skips fetching the document.
- **Use Case:** Ideal for bulk updates or when the updated data isn’t needed immediately.

### Comparison of findByIdAndUpdate() and updateOne()

| Feature                      | `findByIdAndUpdate()`                  | `updateOne()`                            |
| ---------------------------- | -------------------------------------- | ---------------------------------------- |
| **Returns Updated Document** | ✅ Yes                                 | ❌ No                                    |
| **Performance**              | Slightly slower (fetches the document) | Faster (doesn't fetch the document)      |
| **Validation Support**       | ✅ Yes                                 | ✅ Yes                                   |
| **Use Case**                 | When you need the updated document     | When you only need to confirm the update |
