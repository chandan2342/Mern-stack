## Remove Song from `favoriteSongs` Array by User ID

### MongoDB Query

To remove a song with ID `60c72b2f9af1b3d073f43126` from the `favoriteSongs` array for the user with `_id` of `60c72b2f9af1b3d073f43122`, the following query is used:

```js
db.users.findOneAndUpdate(
  { _id: ObjectId("60c72b2f9af1b3d073f43122") }, // Find the user by _id
  { $pull: { favoriteSongs: ObjectId("60c72b2f9af1b3d073f43126") } }, // Remove the song from the array
  { returnDocument: "after" } // Optionally return the updated document
);
```

### Document Before Update

````js{
  "_id": "60c72b2f9af1b3d073f43122",
  "name": "John Doe",
  "favoriteSongs": [
    "60c72b2f9af1b3d073f43124",
    "60c72b2f9af1b3d073f43125",
    "60c72b2f9af1b3d073f43126",
    "60c72b2f9af1b3d073f43127",
    "60c72b2f9af1b3d073f43128"
  ]
}``

### Document After Update
```js{
  "value": {
    "_id": "60c72b2f9af1b3d073f43122",
    "name": "John Doe",
    "favoriteSongs": [
      "60c72b2f9af1b3d073f43124",
      "60c72b2f9af1b3d073f43125",
      "60c72b2f9af1b3d073f43127",
      "60c72b2f9af1b3d073f43128"
    ]
  }
}``

````
