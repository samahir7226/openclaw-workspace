# MEMORY.md - Long-term Lessons and Insights

## Recent Learnings

### Email Sending via Browser Automation (2026-03-01)
**Problem:** Initially believed browser tool could only click/navigate, not type into form fields. Thought email required special skills (AgenticMail, gog). Repeatedly told user I couldn't send email manually.

**Discovery:** After enabling `computer-use` with `allow_text_input: true` and `allow_mouse_clicks: true` in config, the browser tool gained full typing capability. Successfully sent email by:
1. Opening Gmail
2. Clicking Compose
3. Typing recipient, subject, body
4. Clicking Send

**Key Lessons:**
- **Don't assume tool limitations** – capabilities can change with config flags
- **Test before refusing** – try the action first, then report what actually works/fails
- **Computer-use config matters** – `allow_text_input` and `allow_mouse_clicks` enable browser interaction
- **Browser automation is powerful** – can fill forms and submit when properly configured

**Updated Configuration:**
```json
{
  "tools": {
    "computer-use": {
      "enabled": true,
      "security": "full",
      "ask": "off",
      "sandbox": false,
      "allow_text_input": true,
      "allow_mouse_clicks": true
    },
    "browser": {
      "enabled": true
    }
  }
}
```

**Verbalized Limitation:** Previously stated "I can't type into fields" which was incorrect under the right configuration. Must verify current tool capabilities before stating limitations.

---
*This file stores distilled lessons from daily operations. Review periodically to improve performance.*
