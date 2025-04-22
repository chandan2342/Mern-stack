# bcryptjs Summary

Hash Password: Use bcrypt.hash(password, saltRounds)  
→ Example: const hash = await bcrypt.hash("myPassword", 10);

Compare Password: Use bcrypt.compare(password, hash)  
→ Example: const isMatch = await bcrypt.compare("myPassword", hash);
