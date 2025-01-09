# Deleting Documents in MongoDB with Mongoose: `findByIdAndDelete()` vs `deleteOne()`

- **URL:** `/api/users/:id`

## 1. API Using `findByIdAndDelete()`

This API deletes a user document by its ID and returns the deleted document.

### Code Example

```javascript
app.delete("/api/users/:id", async (req, res) => {
  const { id } = req.params; // Extract user ID from params

  try {
    const deletedUser = await User.findByIdAndDelete(id); // Delete user by ID

    if (!deletedUser) {
      return res.status(404).json({ message: "User not found" });
    }

    res.status(200).json(deletedUser); // Return deleted user data
  } catch (error) {
    res.status(400).json({ error: error.message }); // Handle errors
  }
});
```

## 2. API Using `deleteOne()`

This API deletes a user document by its ID and returns a summary of the delete operation instead of the document itself.

### Code Example

```javascript
app.delete("/api/users/:id", async (req, res) => {
  const { id } = req.params; // Extract user ID from params

  try {
    const result = await User.deleteOne({ _id: id }); // Delete user by ID

    if (result.deletedCount === 0) {
      return res.status(404).json({ message: "User not found" });
    }

    res.status(200).json({
      message: "User deleted successfully",
      deletedCount: result.deletedCount, // Indicates how many documents were deleted
    });
  } catch (error) {
    res.status(400).json({ error: error.message }); // Handle errors
  }
});
```

### Comparison of `findByIdAndDelete()` and `deleteOne()`

| Feature                      | `findByIdAndDelete()`                  | `deleteOne()`                            |
| ---------------------------- | -------------------------------------- | ---------------------------------------- |
| **Returns Deleted Document** | ✅ Yes                                 | ❌ No                                    |
| **Performance**              | Slightly slower (fetches the document) | Faster (doesn't fetch the document)      |
| **Validation Support**       | ✅ Yes                                 | ✅ Yes                                   |
| **Use Case**                 | When you need the deleted document     | When you only need to confirm the delete |
