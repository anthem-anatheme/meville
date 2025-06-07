<%*
  // 1. Prompt for mistake title and rename file
  let title = await tp.system.prompt("Enter the mistake title");
  if (title) {
    await tp.file.rename(title);
  } else {
    title = tp.file.title;
  }

  // 2. Prompt for subject
  const subjects = ["biology", "chemistry", "maths"];
  let selectedSubject = await tp.system.suggester(subjects, subjects, false);
  if (!selectedSubject) {
    selectedSubject = "subject-not-specified";
  }

  // 3. Prompt for topic from Topics folder
  const topicFolder = "Topics";
  const files = tp.app.vault.getFiles().filter(f => f.path.startsWith(topicFolder + "/"));
  const topicNames = files.map(f => f.basename);
  let selectedTopic = await tp.system.suggester(topicNames, topicNames, false);
  if (!selectedTopic) {
    selectedTopic = "No topic selected";
  }

  // 4. Prompt for mistake content/description
  let mistakeContent = await tp.system.prompt("Describe the mistake:");
  if (!mistakeContent) {
    mistakeContent = "No description provided.";
  }

  // 5. Prompt for mistake type
  const mistakeTypes = ["Silly mistake", "Knowledge gap"];
  let mistakeType = await tp.system.suggester(mistakeTypes, mistakeTypes, false);
  if (!mistakeType) {
    mistakeType = "Not specified";
  }

  // 6. Determine tags
  let tags = [`#${selectedSubject.replace(/\s+/g, "-").toLowerCase()}`];
  if (mistakeType === "Silly mistake") {
    tags.push("#silly-mistake");
  } else if (mistakeType === "Knowledge gap") {
    tags.push("#knowledge-gap");
  } else {
    tags.push("#mistake");
  }
%>

tags: <% tags.join(" ") %>

# Mistake: <% title %>

- **Date:** <% tp.date.now("YYYY-MM-DD") %>
- **Subject:** <% selectedSubject.charAt(0).toUpperCase() + selectedSubject.slice(1) %>
- **Topic:** [[<% selectedTopic %>]]
- **Mistake Type:** <% mistakeType %>
- **Source (Paper/Question):** 
- **What was the mistake?**  
  <% mistakeContent %>
- **Correct Answer/Concept:**  
- **Why did I make this mistake?**  
- **How will I avoid it next time?**  

## Related Topics
- [[<% selectedTopic %>]]
