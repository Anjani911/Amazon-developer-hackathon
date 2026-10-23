# Scam Shield: a simulated Alexa+ skill

Built for the Build, Ship, Shape: Amazon Developer Hackathon (Alexa+ track, simulated-experience path).

Scam Shield is a voice-and-chat assistant that checks suspicious calls, SMS and WhatsApp messages for scam patterns (digital arrest, fake KYC, job and investment scams), explains the red flags, saves a scam diary, and gives next steps for India (1930 helpline, cybercrime.gov.in). It can also draft a warning for family.

## Run it
No install needed. Open `index.html` in Chrome or Edge. For voice input, serve it locally if the browser blocks the mic on file URLs:

    python3 -m http.server 8000

then open http://localhost:8000.

## How it works
- Agent loop in `handle()` picks tools from the request and chains them: `analyze_message` -> `save_to_diary` -> `get_action_plan` / `alert_family`.
- Tools are shown live in the chat as `tool: name -> result` lines.
- State persists across sessions in `localStorage` (the scam diary and last analysis).
- Voice in uses the browser SpeechRecognition API; voice out uses speechSynthesis.
- Scoring is rule-based (10 scam signal groups with weights), so it runs offline.

## Try it
Use the sample chips, then say "what should I do", "alert my family" and "show my diary".

## Alexa+ track note
This is the simulated Alexa+ experience allowed by the rules. The tool layer is written as separate functions so it can be exposed as an MCP server over Streamable HTTP later.

## License
MIT
