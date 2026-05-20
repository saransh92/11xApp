# Web — landing page

Static landing page for the ElevenAgents PMM work sample. Pure HTML + CSS, no build step.

## Files

- `index.html` — the landing page
- `writing.html` — HTML render of the positioning essay (linked from the footer)
- `styles.css` — single stylesheet, shared by both pages
- `assets/` — reserved for any images or downloads added later

## Local preview

Open `index.html` directly in a browser, or serve the folder over HTTP:

```bash
# from the repo root
cd web && python3 -m http.server 8000
# then visit http://localhost:8000
```

**Note on the widget:** the ElevenLabs conversational widget needs HTTPS to request microphone permission. Loading `index.html` over `file://` or `http://localhost` will render the widget UI but will block the mic. Test the live widget on the deployed GitHub Pages URL.

## The live agent

The widget is already wired in. It mounts as ElevenLabs' default floating bubble in the viewport's bottom-right corner (rendered as a fixed-position custom element at the end of `<body>`). The demo section in the page contains a directional callout pointing visitors to the bubble, plus suggested prompts.

Current agent ID: `agent_1201ks13n7khf5ws6gnrjkc5667n`. To swap it, edit the `agent-id` attribute on the `<elevenlabs-convai>` element in `index.html` (just above the footer):

```html
<elevenlabs-convai agent-id="YOUR_NEW_AGENT_ID"></elevenlabs-convai>
<script
  src="https://unpkg.com/@elevenlabs/convai-widget-embed"
  async
  type="text/javascript"
></script>
```

### Mic permission

The convai widget needs HTTPS to request microphone access. The floating UI appears over `http://localhost` or `file://`, but starting a call will fail. Test the live conversation on the deployed Pages URL (`https://saransh92.github.io/11xApp/`).

### Configuring the agent

Persona, system prompt, voice, language, and knowledge base are all configured in the ElevenLabs dashboard — no code change required. A ServiceNow-flavored internal helpdesk persona fits the page narrative (password resets, access requests, P1 incident logging, knowledge base lookups). Add multilingual support to mirror the Revolut proof point on the page.

### Inline vs. floating layout

The widget defaults to a floating bubble. To embed it inline inside the demo section instead of floating, the relevant configuration lives in the **Widget** tab of the agent dashboard (look for *Variant: Embedded*). If you flip that, move the `<elevenlabs-convai>` element back into the `#talk` section in place of the `.demo-callout` block, and remove the callout's "live in the bottom-right" copy.

## Design notes

- Refined minimalism. Black on white, single ElevenLabs blue accent on the CTA hover.
- System sans font stack — no web font loaded.
- One non-trivial breakpoint at `720px` (single column below, three-column grid above).
- No JavaScript except whatever the embedded widget loads.
- All section padding scales via CSS variables (`--section`, `--gutter`); change them in `:root` to retune the entire vertical rhythm.

## Verifying the published claims

Customer outcome numbers (Klarna, Revolut, Better.com) and the compliance list come from ElevenLabs' public customer pages and trust documentation. URLs are noted in HTML comments above the proof section in `index.html`. If ElevenLabs publishes updated figures, swap them in there.
