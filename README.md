# ai.sh

Just a simple bash script I put together to bring Gemini into my terminal. I wanted something lightweight that didn't require a heavy environment—just `curl`, `jq`, and a bit of shell magic.

### Why?
I often find myself needing a quick answer, a log summary, or a snippet of code without wanting to leave my terminal or open a browser. I built this to be that bridge—unobtrusive, fast, and pipe-friendly.

### What?
It's a single-file script that interacts with the Gemini API. It handles standard prompts, piped input from other commands, and even maintains a simple conversation history when you need it.

### Features
- **Default Mode:** Quick one-off questions and answers.
- **Memory Mode (`memory`):** An interactive chat session that remembers the context of your conversation (stored in `convo.json`).
- **Code Mode (`code`):** Strips away the explanations and markdown fences, returning only the raw code—perfect for piping directly into files or editors.
- **Pipe Support:** Seamlessly handles input from `stdin`, so you can do things like `cat error.log | aidotsh "what is happening here?"`.

### How to use it
1. **API Key:** Grab a key from [Google AI Studio](https://aistudio.google.com/).
2. **Setup:** Export your key in your shell config (e.g., `.zshrc` or `.bashrc`):
   ```bash
   export GEMINI_API_KEY="your_actual_key_here"
   ```
3. **Run:**
   ```bash
   # A simple question
   ./aidotsh "How do I list files by size in bash?"

   # Debugging a log file
   cat sys.log | ./aidotsh "Find any critical errors"

   # Generating a script directly
   ./aidotsh code "write a python script to scrape titles from a url" > scraper.py

   # Starting a conversation
   ./aidotsh memory
   ```

---
*Just a small tool I find useful in my daily workflow. I hope it finds a place in yours too.*
