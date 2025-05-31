<%*
const subject = await tp.system.prompt("Subject");
const paper = await tp.system.prompt("Exam Paper");
const type = await tp.system.suggester(["Silly Mistake", "Knowledge Gap"], ["Silly Mistake", "Knowledge Gap"]);
%>

# 📝 Mistake Log - <% tp.date.now("YYYY-MM-DD") %>

**Subject**:: [[<% subject %>]]  
**Exam Paper**:: [[<% paper %>]]  
**Type of Mistake**:: [[<% type %>]]

---

## ❌ Mistake

_Describe what you did wrong, the question if useful, and what you wrote/thought._


## 🧠 Why did this happen?

_E.g., misread the question, forgot to check units, never revised this, misunderstood a definition._


