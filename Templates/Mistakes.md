<%*
const subject = await tp.system.prompt("Subject");
const paper = await tp.system.prompt("Exam Paper");
const type = await tp.system.suggester(["Silly Mistake", "Knowledge Gap"], ["Silly Mistake", "Knowledge Gap"]);
const today = tp.date.now("YYYY-MM-DD");

// Rename the current file
const filename = `Mistake - ${subject} - ${type} - ${today}`;
await tp.file.rename(filename);
%>

# 📝 Mistake Log - <%= today %>

**Subject**:: [[<% subject %>]]  
**Exam Paper**:: [[<% paper %>]]  
**Type of Mistake**:: [[<% type %>]]

---

## ❌ Mistake

## ✅ Correct Explanation

## 🧠 Why did this happen?

## 🔁 What will I do about it?
