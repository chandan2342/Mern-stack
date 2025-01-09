### Cookies Summary

- **Set Cookie**:
  res.cookie(name, value, options)
  Example: res.cookie("token", token, { httpOnly: true, maxAge: 3600000 });

- **Get Cookie**:
  req.cookies[name] (requires cookie-parser middleware)
  Example: const token = req.cookies.token;

- **Clear Cookie**:
  res.clearCookie(name, options)
  Example: res.clearCookie("token", { httpOnly: true });
