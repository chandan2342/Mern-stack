## All JWT and cookie concept

```js
const secretJwtToken = "hjgknjdomdhjdslmmndsjhdnb"; 

const allConcept = async (req, res) => {
  // JWT Options
  const jwtOptions = { expiresIn: "1h" };

  // Cookie Options
  const cookieOptions = {
    httpOnly: true,
    maxAge: 12 * 60 * 60 * 1000, 
  };

  const payload = {
    id: req.body.id, 
    name: "Chandan",
  };

  // Generate JWT Token
  const token = jwt.sign(payload, secretJwtToken, jwtOptions);

  // Set Token in Cookies
  res.cookie("authToken", token, cookieOptions);

  // Retrieve Token from Cookies
  const receivedToken = req.cookies.authToken; 
  if (!receivedToken) {
    return res.status(401).json({ error: "No token found in cookies" });
  }

  try {
    // Verify JWT Token
    const decodedToken = jwt.verify(receivedToken, secretJwtToken);
    console.log("Decoded Token:", decodedToken);
  } catch (error) {
    return res.status(401).json({ error: "Invalid or expired token" });
  }

  // Clear Token from Cookies
  res.clearCookie("authToken", { httpOnly: true });

  res.status(200).json({ message: "JWT Token processed successfully" });
};




```
