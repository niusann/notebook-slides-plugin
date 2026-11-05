# Notebook Slides Plugin — Gemini Notebook-style presentations in ChatGPT

**The impressive slide style of Gemini Notebook (formerly NotebookLM), right in ChatGPT.**

Turn your notes, reports, or ideas into richly illustrated presentations—with expressive artwork, thoughtful layouts, and a consistent style designed around your topic.

A ChatGPT and Codex plugin with two presentation skills: `notebook-slides` for illustrated PDF decks, and `notebook-slides-pptx` for editable PowerPoint. One installation includes both skills.

![Notebook Slides creating an illustrated AI presentation in ChatGPT](showcase-redacted.png)

## Install in ChatGPT

Use **Plugin Creator** to add the bundle to your account or workspace, where plugin creation is available:

1. [**Download notebook-slides-plugin.zip**](https://github.com/niusann/notebook-slides-plugin/releases/latest/download/notebook-slides-plugin.zip). Keep the file zipped. Choose the **plugin** ZIP to get both output options.
2. Open a new ChatGPT conversation. Type **@**, search for **Plugin Creator**, and select it.
3. Attach the downloaded ZIP and send this message:

   ```text
   Create a private plugin called Notebook Slides from the attached package.
   Keep both included skills and all their reference files as supplied.
   Give me the plugin link so I can install it.
   ```

4. Follow Plugin Creator's prompts, then open the plugin link it returns. Review the details and click **Install plugin** or the **+** install button. You may also find it under **Plugins → Personal → Created by me**, when available.
5. Start a **new conversation**, type **@**, and select **Notebook Slides**. Attach your notes or report and ask for a presentation.

Just specify **PowerPoint** or **PDF** in your prompt. One download includes both options.

Plugin Creator and plugin creation depend on your account and workspace permissions. If unavailable, ask your workspace admin or try the desktop installation below. No MCP server or separate API key is required by this plugin. See OpenAI's guides to [creating plugins](https://learn.chatgpt.com/docs/build-plugins) and [installing and using plugins](https://learn.chatgpt.com/docs/plugins).

### Alternative: install a local plugin in ChatGPT desktop

For **Work mode / Codex in the ChatGPT desktop app**, this repository includes a local marketplace:

1. [Download and extract the repository ZIP](https://github.com/niusann/notebook-slides-plugin/archive/refs/heads/main.zip), or run `git clone https://github.com/niusann/notebook-slides-plugin.git`.
2. Open that repository folder as a project in Work mode / Codex. Choose the root folder containing `.agents/plugins/marketplace.json`.
3. Restart the ChatGPT desktop app.
4. Open **Plugins**, choose the **Notebook Slides (local)** marketplace, and install **Notebook Slides**.
5. Start a new conversation in that project, select the plugin with **@**, and share your source material.

Keep the folder in place while using the local plugin. For use across projects, ask Plugin Creator to register the included `plugins/notebook-slides` folder in your personal marketplace. See OpenAI's [local marketplace instructions](https://developers.openai.com/plugins/build/plugins).

### Codex CLI

```sh
codex plugin marketplace add niusann/notebook-slides-plugin
codex
```

Enter `/plugins`, choose **Notebook Slides (local)**, and install **Notebook Slides**. Start a new session before using the skills. Image generation and file creation must be available in your environment to produce a complete deck.

## Try it

> Make a 10-slide presentation about artificial intelligence in the visual style of Google Gemini Notebook (formerly NotebookLM). Use warm colors and playful illustrations. Deliver it as an editable PowerPoint.

> Turn this report into a presentation for our leadership team. Focus on the key findings and next steps. Give me a PDF.

Notebook Slides guides you through the outline, visual theme, and slide designs before creating your deck. You can ask for changes along the way—or say **“just generate it”** to go straight to the result.

For the best result, mention your audience and preferred slide count. Your assistant needs image generation and file creation enabled. Allow a few minutes for the deck to be created, and review it before presenting.

## Keep editing your finished slides

A useful workflow: get the visual design right first, then make your final edits. If you love your PDF deck but want to change the wording, try [ReDeck](https://redeck.capsep.com/). Upload the PDF, choose your slides, and download a PowerPoint with editable text and supported movable graphics.

Already have an editable PowerPoint? Just keep editing it directly.

## Need help?

| Problem | What to try |
|---|---|
| The plugin or skills do not appear | Check that the plugin is installed, then start a new conversation. |
| The local marketplace is missing | Open the repository root in Work mode / Codex and restart the desktop app. |
| The output is not the format you wanted | Ask for an **editable PowerPoint (.pptx)** or an **illustrated PDF** explicitly. |
| Images or the downloadable deck are missing | Use a session with image generation and file creation enabled. If image generation is unavailable, the skill supplies prompts; the PPTX skill can use placeholders with prompts in the notes. |

## Downloads

- [Full plugin: PDF + PowerPoint skills](https://github.com/niusann/notebook-slides-plugin/releases/latest/download/notebook-slides-plugin.zip) — recommended for ChatGPT.
- [PDF skill only](https://github.com/niusann/notebook-slides-plugin/releases/latest/download/notebook-slides.zip).
- [PowerPoint skill only](https://github.com/niusann/notebook-slides-plugin/releases/latest/download/notebook-slides-pptx.zip).

The individual skill ZIPs are for hosts that support standalone skill imports. Downloading the source repository is only needed for the local desktop route.

This independent plugin is inspired by the visual style of Gemini Notebook / NotebookLM. It is not affiliated with Google or OpenAI. The v1.0.0 workflows have not yet been tested end to end in ChatGPT.
