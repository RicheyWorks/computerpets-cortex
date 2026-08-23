# Cortex contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Cortex**
- Repo: `computerpets-cortex`
- Category: AI & GPU
- Idea: LLM Pet Brain
- Port / surface: `8091`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Persona(speciesId, voice, temperament, taboo[]) · Utterance(petId, text, emotion, seed) · MemoryWindow(petId, turns[8])

## Surface

- POST /v1/speak — given petId + event (fed, poked, ignored), return a line + emotion tag
- POST /v1/chat — multi-turn player chat with a species system prompt and short-term memory
- GET /v1/persona/{speciesId} — locked voice, vocabulary, taboo list for that animal
- POST /v1/moderate — drop or rewrite lines that break canon or safety policy

## Neighbors

- computerpets (desktop + Spring backend)
- computerpets-vox (spoken replies)
- computerpets-quests (daily prompts)
- computerpets-lore (canon facts)

## Failure doctrine

Model timeout → canned species bark. Safety trip → silent emote only. Unknown species → generic 'critter' prompt, never another animal's voice.

## Stack

Python 3.12 · FastAPI · xAI Grok / local vLLM · Redis session memory · gRPC to the desktop client
