---
hidden: true
coverY: 0
---

# Ui References

## GitBook UI Components – Quick Reference

Welcome to the **GitBook Components Showcase** \
This page helps new editors understand and try out all **UI blocks** available in GitBook’s Notion-style editor.

***

### &#x20;Stepper (Process / Flow Guide)

/stepper

**1️⃣ Add a Stepper Block**\
Type `/stepper` and hit Enter. You’ll get a vertical numbered layout like this.

**2️⃣ Add Your Steps**\
Each step can include text, images, lists, and even code blocks.

**3️⃣ Add More Steps**\
Press the **+** button below the step or hit **Enter twice** to add another step.

💡 _Use Stepper for process flows, setup instructions, or multi-step guides._

/stepper

***

### &#x20;Tabs (Switchable Views)

/tabs

**User View**\
You can use `/tabs` to create multiple views for different audiences — like **User** vs **Developer** content.

**Developer View**\
Tabs help organize long guides. Perfect for “API” vs “UI” instructions.

/tabs

💡 _Use Tabs for “Quick Verify / Bulk Verify” or “Frontend / Backend” type comparisons._

***

### Columns (Side-by-Side Layout)

/columns

#### &#x20;Left Column

Add text, bullet points, or lists here. Great for instructions.

#### Right Column

Add an image or table here using `/image` or `/table`.

💡 _Use Columns to show screenshots next to explanations!_

/columns

***

### &#x20;Hints (formerly Callouts)

/hint{"type":"info","title":"Info Hint"}\
Used for helpful notes, tips, or neutral context.

💡 Example: “You can get your API key under Settings → API.”\
/hint

/hint{"type":"success","title":"Success Hint"}\
Used to highlight success or completion messages.\
/hint

/hint{"type":"warning","title":"Warning Hint"}\
Used to show potential issues or cautionary notes.\
/hint

/hint{"type":"danger","title":"Danger Hint"}\
Used to highlight critical issues or errors.\
/hint

***

### &#x20;Table

/table

| Column 1 | Column 2        | Column 3         |
| -------- | --------------- | ---------------- |
| ✅ Valid  | ⚠️ Catch-All    | ❌ Invalid        |
| 200 OK   | 400 Bad Request | 500 Server Error |
| /table   |                 |                  |

💡 _Use `/table` for small data summaries or API status codes._

***

### &#x20;Code Blocks

/code

```javascript
fetch("https://api.clearout.io/v2/email_verify/instant", {
  method: "POST",
  headers: { "Authorization": "Bearer YOUR_API_KEY" },
  body: JSON.stringify({ email: "test@domain.com" }),
});
```

/code

💡 _Use `/code` for API examples or command snippets._

***

### &#x20;Image

/image\
Use `/image` to upload screenshots or product visuals.\
💡 _Recommended for showing dashboards, extensions, or plugin interfaces._

***

### &#x20;Quotes

/quote

> “Clear, visual documentation builds trust and improves onboarding.”\
> /quote

💡 _Use for short reminders or best practices._

***

### &#x20;Combining Components

You can even **mix components** for richer layouts:

* Use `/columns` inside a `/stepper` step to show image + description
* Put `/hint` inside `/tabs` for contextual info
* Add `/table` inside `/columns` to show side-by-side comparison

***

### 🧠 Example Layout Idea

/columns

#### &#x20;Stepper on Left

Use `/stepper` for:

* Install
* Connect
* Test
* Deploy

#### &#x20;Hints on Right

/hint{"type":"success","title":"Pro Tip"}\
Add hints on the right column to keep your layout interactive.\
/hint

/columns

***

### &#x20;Best Practices

* Keep one concept per section
* Don’t overuse tabs (3–4 max per block)
* Prefer `/hint` for short info — not long paragraphs
* Add screenshots often
* Use consistent emoji/icons per block type

***

### &#x20;Summary Table

/table

| Block   | Command    | Use Case                |
| ------- | ---------- | ----------------------- |
| Stepper | `/stepper` | Multi-step tutorials    |
| Tabs    | `/tabs`    | Switchable content      |
| Hint    | `/hint`    | Notes, tips, warnings   |
| Columns | `/columns` | Side-by-side layouts    |
| Table   | `/table`   | Data or comparisons     |
| Code    | `/code`    | Snippets                |
| Quote   | `/quote`   | Inspiration or guidance |
| Image   | `/image`   | Visuals or screenshots  |
| /table  |            |                         |
