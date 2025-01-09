```js
import dotenv from "dotenv";
import express from "express";
import cookieParser from "cookie-parser";
import cors from "cors";

import connectDB from "./config/database.js";
import userRoute from "./routes/userRoute.js";

dotenv.config({});
const PORT = process.env.PORT || 5000;

// middleware
app.use(express.urlencoded({ extended: true }));
app.use(express.json());
app.use(cookieParser());

// cors middleWare
const corsOption = {
  origin: ["http://localhost:5173", "https://real-chat-app7953.netlify.app"],
  credentials: true,
};
app.use(cors(corsOption));

// routes
app.use("/api/v1/user", userRoute);

server.listen(PORT, () => {
  connectDB();
  console.log(`Server listen at prot ${PORT}`);
});
```

### Router in js

```js
const router = express.Router();
router.route("/login").post(login);
router.route("/register").post(register);

export default router;
```
