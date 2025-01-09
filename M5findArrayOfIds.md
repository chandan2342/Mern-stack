### MongoDB Query: Find Documents by Array of ObjectIds

```js
let likeSongArr = [
  ObjectId("60c72b2f9af1b3d073f43124"),
  ObjectId("60c72b2f9af1b3d073f43125"),
  ObjectId("60c72b2f9af1b3d073f43126"),
  ObjectId("60c72b2f9af1b3d073f43127"),
  ObjectId("60c72b2f9af1b3d073f43128"),
];

db.users.find({
  _id: { $in: likeSongArr },
});
``;

output: [
  { _id: "60c72b2f9af1b3d073f43124", name: "Song 1" },
  { _id: "60c72b2f9af1b3d073f43125", name: "Song 2" },
  { _id: "60c72b2f9af1b3d073f43126", name: "Song 3" },
  { _id: "60c72b2f9af1b3d073f43127", name: "Song 4" },
  { _id: "60c72b2f9af1b3d073f43128", name: "Song 5" },
];
```
