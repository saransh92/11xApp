# ElevenAgents for enterprise

A two-part work sample for a PMM application to ElevenLabs (ElevenAgents):

1. **A positioning essay** arguing that the next leg of voice-agent adoption is inside the enterprise platforms ElevenAgents already integrates with (Salesforce, ServiceNow, Zendesk, HubSpot).
2. **A live landing page** that adapts the essay into web copy and embeds a working ElevenAgents voice widget so the visitor can talk to it.


**Live page:** [saransh92.github.io/11xApp](https://saransh92.github.io/11xApp/) (deploys from `main` via GitHub Pages)

## File structure

```
.
├── README.md                                    ← you are here
├── writing/
│   └── elevenagents-for-servicenow.md           ← the source essay (~830 words)
├── web/
│   ├── index.html                               ← landing page
│   ├── writing.html                             ← essay as an HTML page
│   ├── styles.css                               ← shared stylesheet
│   ├── README.md                                ← page-level docs + widget instructions
│   └── assets/                                  ← reserved for images
└── .github/
    └── workflows/
        └── pages.yml                            ← auto-deploy to GitHub Pages
```

## Local development

No build step. Open `web/index.html` in a browser, or serve over HTTP:

```bash
cd web && python3 -m http.server 8000
# http://localhost:8000
```

The ElevenAgents widget needs HTTPS for microphone permission, so the live agent only works on the deployed Pages URL — local previews will show the placeholder block.

## Deploying to GitHub Pages

1. Push this repo to `https://github.com/saransh92/11xApp` (or whichever repo you want; the workflow is repo-agnostic).
2. In **Settings → Pages**, set **Source** to **GitHub Actions**.
3. Push to `main`. The workflow in `.github/workflows/pages.yml` will build and deploy the `web/` directory.
4. The site will be live at `https://<username>.github.io/<repo>/` within a minute of the workflow finishing.

Custom domain is optional — add it in **Settings → Pages → Custom domain** and create a `CNAME` file in `web/`.

## The live agent

The widget is already plugged in and mounts as a floating bubble in the bottom-right of the page. Mic permission requires HTTPS, so the live conversation only works on the deployed Pages URL. See [`web/README.md`](web/README.md) for how to swap the agent ID or switch to an embedded (non-floating) variant.

## What's left for me to do

- [ ] Push to `https://github.com/saransh92/11xApp` and enable Pages → GitHub Actions in repo settings
- [ ] Drop the actual CV PDF (or hosted link) into the footer's "CV · coming soon" link
- [ ] Verify Klarna / Revolut / Better.com source URLs (currently noted as HTML comments) point at the right ElevenLabs customer pages


## Authoring notes

- All customer outcome statistics are sourced from ElevenLabs' public customer pages. URLs in HTML comments in `web/index.html`.
- The compliance list (SOC 2 Type II, ISO 27001, HIPAA, PCI DSS L1, GDPR, TXRAMP L2, AIUC-1, Zero Retention, VPC, regional data residency) is from ElevenLabs' public trust documentation.
- Anything unverified would carry a `[TBD: verify]` marker in the essay; there are none in the current draft.
